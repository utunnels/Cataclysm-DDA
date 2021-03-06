# JSON file contents

##raw
* bionics.json       - bionics, does NOT include bionic effects
* dreams.json        - dream text and linked mutation categories
* item_groups.json   - item spawn groups
* materials.json     - material types
* monstergroups.json - monster spawn groups
* names.json         - names used for NPC/player name generation
* professions.json   - profession definitions
* recipes.json       - crafting/disassembly recipes
* skills.json        - skill descriptions and ID's
* snippets.json      - flier/poster descriptions
* traits.json        - traits/mutation visibility, does NOT include mutation effects

##raw/items
* archery.json       - bows and arrows
* ranged.json        - guns
* tools.json         - tools and items that can be (a)ctivated
* ammo.json          - ammo
* books.json         - books
* comestibles.json   - food/drinks
* containers.json    - containers
* instruments.json   - instruments
* melee.json         - anything that doesn't go in the other item jsons, melee weapons
* mods.json          - gunmods

#raw jsons

###BIONICS
```C++
"id"         :    "bio_batteries",   // Unique ID. Must be one continuous word, use underscores if necessary
"name"       :    "Battery System",  // In-game name displayed
"cost"       :    0,                 // How many PUs it costs to use the bionic.
"time"       :    0,                 // How long, when activated, between drawing cost. If 0, it draws power once.
"flags"      :    ["POWER"],         // Used to flag the bionic as a specific type.
"description":    "You have a battery draining attachment, and thus can make use of the energy\ncontained in normal, everyday batteries.  Use 'E' to consume batteries." // In-game description
```
###DREAMS
```C++
"message"		:	[                // List of potential dreams
	"You have a strange dream about birds.",
	"Your dreams give you a strange feathered feeling."
	],
"category"		:	"MUTCAT_BIRD",   // Mutation category needed to dream
"strength"		:	1                // Mutation category strength required
                                          1 = 20 - 34
                                          2 = 35 - 49
                                          3 = 50+
```
###ITEM GROUPS
```C++
"id":"forest",            // Unique ID. Must be one continuous word, use underscores if necessary
"items":[                 // List of potential item ID's. Chance of an item spawning is x/T, where
  ["rock", 40],           //    X is the value linked to the specific item and T is the total of all
  ["stick", 95],          //    item values in a group
  ["mushroom", 4],
  ["mushroom_poison", 3],
  ["mushroom_magic", 1],
  ["blueberries", 3]
]
```
###MATERIALS
```C++
"ident"         : "hflesh",       // Unique ID. Must be one continuous word, use underscores if necessary
"name"          : "Human Flesh",  // In-game name displayed
"bash_resist"   :   1,            // How well a material resists bashing damage
"cut_resist"    :   1,            // How well a material resists cutting damage
"bash_dmg_verb" : "bruised",      // Verb used when material takes bashing damage
"cut_dmg_verb"  : "sliced",       // Verb used when material takes cutting damage
"dmg_adj"       : ["bruised", "mutilated", "badly mutilated", "thoroughly mutilated"], // Description added to damaged item in ascending severity
"acid_resist"   :   1,            // Ability of a material to resist acid
"elec_resist"   :   1,            // Ability of a material to resist electricity
"fire_resist"   :   0,            // Ability of a material to resist fire
"density"       :   5             // Density of a material
```
###MONSTER GROUPS
```C++
"name" : "GROUP_ANT",             // Unique ID. Must be one continuous word, use underscores if necessary
"default" : "mon_ant",            // Default monster, automatically fills in any remaining spawn chances
"monsters" : [
  { "monster" : "mon_ant_larva", "freq" : 40, "multiplier" : 0 },   // To choose monster spawned game creates 1000 entries and picks one.
  { "monster" : "mon_ant_soldier", "freq" : 90, "multiplier" : 5 }, // Each monster will have a number of entries equal to it's "freq" and 
  { "monster" : "mon_ant_queen", "freq" : 0, "multiplier" : 0 }     // the default monster will fill in the remaining. "multiplier" increases
]                                                                   // how much each monster counts for in a spawn group (i.e. will spawn 5 larva or 1 soldier)
```
###NAMES
```C++
{ "name" : "Aaliyah", "gender" : "female", "usage" : "given" }, // Name, gender, "given"/"family"/"city" (first/last/city name).
// NOTE: Please refrain from adding name PR's in order to maintain kickstarter exclusivity
```
###PROFESSIONS
```C++
"description":"Ever since you were a child you loved hunting, and you loved the challenge of hunting with a bow even more. You start with a level in archery and survival.", // In-game description
"ident":"hunter",      // Unique ID. Must be one continuous word, use underscores if necessary
"items":[              // ID's of items player starts with when selecting this profession
 "army_top",
 "boots_steel",
 "jeans"
],
"name":"Bow Hunter",   // In-game name displayed
"points":2,            // Point cost of profession. Positive values cost points and negative values grant points
"addictions" : [       // Optional list of starting addictions.
 {
	"type": "nicotine", // ID of addiction
	"intensity" : 10,  // Intensity of starting addiction
 }
"skills":[             // Skills that the player starts with when selecting this profession, stacks with purchased skills
 {
	"level":1,         // Skill level granted
	"name":"archery"   // ID of granted skill
 },
 {
	"level":1,
	"name":"survival"
 }
]
```
###RECIPES
```C++
"result": "javelin",         // ID of resulting item
"category": "CC_WEAPON",     // Category of crafting recipe. CC_NONCRAFT used for disassembly recipes
"skill_used": "fabrication", // Skill trained and used for success checks
"requires_skills": [ "survival", 1, "throw", 2 ], // Skills required to unlock recipe
"difficulty": 3,             // Difficulty of success check
"time": 5000,                // Time to perform recipe
"reversible": false,         // Can be disassembled.
"autolearn": true,           // Automatically learned upon gaining required skills
"tools": [                   // Tools needed to craft
[                            // Equivalent tools are surrounded by a single set of brackets []
  [ "hatchet", -1 ],         // Charges consumed when tool is used, -1 means no charges are consumed
  [ "knife_steak", -1 ],
  [ "knife_combat", -1 ],
  [ "knife_butcher", -1 ],
  [ "pockknife", -1 ],
  [ "scalpel", -1 ],
  [ "machete", -1 ],
  [ "broadsword", -1 ],
  [ "toolset", -1 ]
],
[
  [ "fire", -1 ]
	]
],
"components": [              // Equivalent components are surrounded by a single set of brackets
[
  [ "spear_wood", 1 ],       // Number of charges/items required
  [ "pointy_stick", 1 ]
],
[
  [ "rag", 1 ],
  [ "leather", 1 ],
  [ "fur", 1 ]
],
[
  [ "plant_fibre", 20 ],
  [ "sinew", 20 ],
  [ "thread", 20 ],
  [ "duct_tape", 20 ]
]
]
```
###SKILLS
```C++
"smg",              // Unique ID. Must be one continuous word, use underscores if necessary
"submachine guns",  // In-game name displayed
"Your skill with submachine guns and machine pistols. Halfway between a pistol and an assault rifle, these weapons fire and reload quickly, and may fire in bursts, but they are not very accurate.", // In-game description
["gun_type"]        // Special flags, most skills will have an empty list "[]"
```
###SNIPPETS
```C++
"category": "flier", // Category used
	"text": "This is an advertisement for the Diet Devil brand Metabolic Exchange CBM.  It shows a picture of a tiny obese devil sitting on a woman's shoulder. The woman stares intently at a gigantic wedding cake covered with bacon and candybars. The caption reads: \"Burn calories! Burn!\"" // In-game description
```
###TRAITS
```C++
"name": "Optimist",  // In-game name displayed
"points": 2,         // Point cost of the trait. Positive values cost points and negative values give points
"visibility": 0,     // Visibility of the trait for purposes of NPC interaction
"ugliness": 0,       // Ugliness of the trait for purposes of NPC interaction
"description": "Nothing gets you down!  You savor the joys of life, ignore its hardships, and are generally happier than most people." // In-game description
```
#raw/items jsons

###AMMO
```C++
"type" : "AMMO",      // Defines this as ammo
"id" : "shot_bird",   // Unique ID. Must be one continuous word, use underscores if necessary
"price" : 500,        // Used when bartering with NPC's
"name" : "birdshot",  // In-game name displayed
"symbol" : "=",       // ASCII character used in-game
"color" : "red",      // ASCII character colour
"description" : "Weak shotgun ammunition. Designed for hunting birds and other small game, its applications in combat are very limited.", // In-game description
"material" : "plastic", // Material types.  See materials.json for possible options
"volume" : 2,         // Volume, measured in 1/4 liters
"weight" : 34,        // Weight, measuted in grams
"bashing" : 1,        // Bashing damage caused by using it as a melee weapon
"cutting" : 0,        // Cutting damage caused by using it as a melee weapon
"to_hit" : 0,         // To-hit bonus if using it as a melee weapon
"ammo_type" : "shot", // Determines what it can be loaded in
"damage" : 18,        // Ranged damage when fired
"pierce" : 0,         // Armor piercing ability when fired
"range" : 5,          // Range when fired
"dispersion" : 0,     // Inaccuracy of ammo, measured in quarter-degrees
"recoil" : 18,        // Recoil caused when firing
"count" : 25,         // Number of rounds that spawn together
"effects" : ["COOKOFF", "SHOT"] // Special effects
```
###ARMOR
```C++
"type" : "ARMOR",     // Defines this as armor
"id" : "socks",       // Unique ID. Must be one continuous word, use underscores if necessary
"name" : "socks",     // The name appearing in the examine box.  Can be more than one word separated by spaces
"weight" : 350,       // Weight of armour in grams
"color" : "blue",     // ASCII character colour
"covers" : ["FEET"],  // Where it covers.  Possible options are TORSO, HEAD, EYES, MOUTH, ARMS, HANDS, LEGS, FEET
"to_hit" : 0,         // To-hit bonus if using it as a melee weapon (whatever for?)
"storage" : 0,        // How many volume storage slots it adds
"symbol" : "[",       // ASCII character used in-game
"description" : "Socks. Put 'em on your feet.", // Description of armour
"price" : 100,        // Used when bartering with NPCs
"material" : ["COTTON", "NULL"],    // Material types.  See materials.json for possible options
"volume" : 1,         // Volume, measured in 1/4 liters
"cutting" : 0,        // Cutting damage caused by using it as a melee weapon
"warmth" : 10,        // How much warmth clothing provides
"phase" : "solid",    // What phase it is
"enviromental_protection" : 0,  // How much environmental protection it affords
"encumberance" : 0,   // Base encumbrance (unfitted value)
"bashing" : -5,       // Bashing damage caused by using it as a melee weapon
"flags" : ["VARSIZE"] // Indicates special effects
"coverage" : 80,      // What percentage of body part
"material_thickness" : 1  // Thickness of material, in millimetre units (approximately).  Generally ranges between 1 - 5, more unusual armour types go up to 10 or more
```
###BOOKS
```C++
"type" : "BOOK",      // Defines this as a BOOK
"id" : "textbook_computers", // Unique ID. Must be one continuous word, use underscores if necessary
"name" : "Computer Science 301", // In-game name displayed
"max_level" : 5,      // Maximum skill level this book will train to
"description" : "A college textbook on computer science.", // In-game description
"weight" : 1587,      // Weight, measured in grams
"to_hit" : 1,         // To-hit bonus if using it as a melee weapon
"color" : "blue",     // ASCII character colour
"intelligence" : 11,  // Intelligence required to read this book without penalty
"symbol" : "?",       // ASCII character used in-game
"material" : ["paper", "null"], // Material types.  See materials.json for possible options
"volume" : 7,         // Volume, measured in 1/4 liters
"bashing" : 5,        // Bashing damage caused by using it as a melee weapon
"cutting" : 0,        // Cutting damage caused by using it as a melee weapon
"time" : 35,          // Time (in minutes) a single read session takes
"fun" : -2,           // Morale bonus/penalty for reading
"skill" : "computer", // Skill raised
"price" : 500,        // Used when bartering with NPCs
"required_level" : 2  // Minimum skill level required to learn
```
###COMESTIBLES
```C++
"type" : "COMESTIBLE", // Defines this as a COMESTIBLE
"id" : "crack",       // Unique ID. Must be one continuous word, use underscores if necessary
"name" : "crack",     // In-game name displayed
"weight" : 1,         // Weight, measured in grams
"color" : "white",    // ASCII character colour
"addiction_type" : "crack", // Addiction type
"spoils_in" : 0,      // How long a comestible is good for. 0 = no spoilage
"use_action" : "CRACK", // What effects a comestible has when used
"stim" : 40,          // Stimulant effect
"container" : "null", // What container stores this
"to_hit" : 0,         // To-hit bonus if using it as a melee weapon
"comestible_type" : "MED", // Comestible type, used for inventory sorting
"symbol" : "!",       // ASCII character used in-game
"quench" : 0,         // Thirst quenched
"heal" : -2,          // Health effects (used for sickness chances)
"addiction_potential" : 80, // Ability to cause addictions
"nutrition" : 0,      // Hunger satisfied
"description" : "Refined cocaine, incredibly addictive.", // In-game description
"price" : 420,        // Used when bartering with NPCs
"material" : "powder", // Material types.  See materials.json for possible options
"tool" : "apparatus", // Tool required to be eaten/drank
"volume" : 1,         // Volume, measured in 1/4 liters
"cutting" : 0,        // Cutting damage caused by using it as a melee weapon
"phase" : "solid",    // What phase it is
"charges" : 4,        // Number of uses when spawned
"bashing" : 0,        // Bashing damage caused by using it as a melee weapon
"fun" : 50            // Morale effects when used
```
###CONTAINERS
```C++
"id": "keg",          // Unique ID. Must be one continuous word, use underscores if necessary
"type": "CONTAINER",  // Defines this as a CONTAINER
"symbol": ")",        // ASCII character used in-game
"color": "light_cyan", // ASCII character colour
"name": "aluminum keg", // In-game name displayed
"description": "A reusable aluminum keg, used for shipping beer.\nIt has a capacity of 50 liters.", // In-game description
"price": 6000,        // Used when bartering with NPCs
"weight": 13500,      // Weight, measured in grams
"volume": 200,        // Volume, measured in 1/4 liters
"bashing": -4,        // Bashing damage caused by using it as a melee weapon
"cutting": 0,         // Cutting damage caused by using it as a melee weapon
"to_hit": -4,         // To-hit bonus if using it as a melee weapon
"material": "steel",  // Material types.  See materials.json for possible options
"contains": 200,      // How much volume this container can hold
"flags": ["RIGID", "SEALS", "WATERTIGHT"] // Indicates special effects
```
###MELEE
```C++
"id": "hatchet",      // Unique ID. Must be one continuous word, use underscores if necessary
"symbol": ";",        // ASCII character used in-game
"color": "light_gray", // ASCII character colour
"name": "hatchet",    // In-game name displayed
"description": "A one-handed hatchet. Makes a great melee weapon, and is useful both for cutting wood, and for use as a hammer.", // In-game description
"price": 95,          // Used when bartering with NPCs
"material": ["iron", "wood"], // Material types.  See materials.json for possible options
"weight": 907,        // Weight, measured in grams
"volume": 6,          // Volume, measured in 1/4 liters
"bashing": 12,        // Bashing damage caused by using it as a melee weapon
"cutting": 12,        // Cutting damage caused by using it as a melee weapon
"flags" : ["CHOP"],   // Indicates special effects
"to_hit": 1           // To-hit bonus if using it as a melee weapon
```
###GUN
```C++
"id": "nailgun",      // Unique ID. Must be one continuous word, use underscores if necessary
"type": "GUN",        // Defines this as a GUN
"symbol": "(",        // ASCII character used in-game
"color": "light_blue", // ASCII character colour
"name": "nail gun",   // In-game name displayed
"description": "A tool used to drive nails into wood or other material. It could also be used as a ad-hoc weapon, or to practice your handgun skill up to level 1.", // In-game description
"price": 100,         // Used when bartering with NPCs
"material": "iron",   // Material types.  See materials.json for possible options
"flags": "MODE_BURST", // Indicates special effects
"skill": "pistol",    // Skill used for firing
"ammo": "nail",       // Ammo type accepted for reloading
"weight": 2404,       // Weight, measured in grams
"volume": 4,          // Volume, measured in 1/4 liters
"bashing": 12,        // Bashing damage caused by using it as a melee weapon
"cutting": 0,         // Cutting damage caused by using it as a melee weapon
"to_hit": 1,          // To-hit bonus if using it as a melee weapon
"ranged_damage": 0,   // Ranged damage when fired
"range": 0,           // Range when fired
"dispersion": 32,     // Inaccuracy of gun, measured in quarter-degrees
"recoil": 0,          // Recoil caused when firing
"durability": 8,      // Resistance to damage/rusting, also determines misfire chance
"burst": 5,           // Number of shots fired in burst mode
"clip_size": 100,     // Maximum amount of ammo that can be loaded
"reload": 450         // Amount of time to reload, 100 = 6 seconds = 1 "turn"
```
###TOOLS
```C++
"id": "torch_lit",    // Unique ID. Must be one continuous word, use underscores if necessary
"type": "TOOL",       // Defines this as a TOOL
"symbol": "/",        // ASCII character used in-game
"color": "brown",     // ASCII character colour
"name": "torch (lit)", // In-game name displayed
"description": "A large stick, wrapped in gasoline soaked rags. This is burning, producing plenty of light", // In-game description
"price": 0,           // Used when bartering with NPCs
"material": "wood",   // Material types.  See materials.json for possible options
"techniques": "FLAMING", // Combat techniques used by this tool
"flags": "FIRE",      // Indicates special effects
"weight": 831,        // Weight, measured in grams
"volume": 6,          // Volume, measured in 1/4 liters
"bashing": 12,        // Bashing damage caused by using it as a melee weapon
"cutting": 0,         // Cutting damage caused by using it as a melee weapon
"to_hit": 3,          // To-hit bonus if using it as a melee weapon
"max_charges": 75,    // Maximum charges tool can hold
"initial_charges": 75, // Charges when spawned
"charges_per_use": 1, // Charges consumed per tool use
"turns_per_charge": 20, // Charges consumed over time
"ammo": "NULL",       // Ammo type used for reloading
"revert_to": "torch_done", // Transforms into item when charges are expended
"use_action": "TORCH_LIT" // Action performed when tool is used
```