# DynamicDropRateCalculator
This standalone software is used to automate drop rate statistical analysis.

## Goal:
- Process and display statistical information about drop table and with various modes.
- Allow changes and additions to drop tables

## Specifics:

- Allow users to build or load loot tables, set/change modes, set mode parameters, and display a wealth of statistical information.
- Allow users to pick a mode, the number of items they want, ask for days or crates or rolls, ask for what % option they want and output general stats as well as what the base item % would need to be to meet the goal.

## Storage Format:
### CSV file with a header in the format of:
    <Tier Name>:<Tier Weight>,<Tier Name>:<Tier Weight>,......
### Each following line in the format of: 
    <objectName>,<roll Weight>,<Tier Name>

### Example File:
    Unspoken:.005,Godly:.895,Legendary:1.1,Epic:8,Rare:20,Common:30,Poor:40
    Godly Weapon,.3,Godly                  
    Stone, 50,Common            
    healStone ,10.2,Rare           

## Modes:
Once you have a file, you must pick a mode. Each mode uses the file drastically different, so be sure to understand what the weights do for each mode.
- Basic Chance mode:
    - Will calculate stats as if there is not an initial tier selection system, using weights, outputing one item.
- Tier Mode:
    - Will roll each tier first, selecting a tier based on the tier weight. It will then ask if you want to use the internal weights, or even odds. (Kem does even odds within tier)
- Max Items Mode:
    - Will roll each item from top to bottom once, with each either being success or failure, outputting multiple items.       

## User Options:
Take in possible statistical parameters such as:
 - Allow users to create boxes from scratch.
 - Rolls per drop/lootbox (kem rolls 3 times)
 - Rolls per day (range or static number)
 - Uses CSV for creating and storing loot boxes.   

## Output a varity of information based on input drop/lootbox such as:
 - Info on odds per individual roll
 - Info on odds per drop/lootbox
 - Info on odds per item per day
 - Time and rolls expected for N of each item to be given at 10%, 30%, 50%, 70%, 90%, 95%
 - Test N Sample rolls with output results and stats 

## Menus:
### Start Menu:
    1. Load a File - > File Load Flow(Table)
    2. Create a File -> New File Flow
### Mode Menu:
    1. Choose from modes
    2. Change Tier
    3. Add Tier
    4. Remove Tier
### Add New Object Menu:
    Options:
    1. Add via raw weight (DANGER)- > addRaw Flow
    2. Add via % -> add% Flow
    3. Add via day goal -> Daily Add Flow
### Loaded Menu:
    1. View All Info on loaded Box
    2. View Info on specific Object
    3. Mode Menu
    4. Add New Object Menu
    5. Set Loot Table rolls per Crate
    6. Set Crates per day.
    7. Start Menu
## Flows:
### New File Flow:
    1. Get Name from User
    2. createEmptyLootTable(name)
    3. File Load Flow(Empty Loot Table)
### File Load Flow(table):
    1. Mode Menu
    2. Set Crate Rolls
    3. Set Crates per day
    3. Add New Object Menu
    4. Rolls per Crate
    5. Crates Per Day
    6. Loaded Menu
### AddRaw Flow:
    1. Ask for item name
    2. Ask for item wieght
    3. Ask for item tier (only in tier mode)
    4. Return
### add% Flow:
    1. Ask for item name
    2. Ask for item drop %
    3. Loop Ask for what item we want to decrease to compensate for changes until we are balanced
    4. Return
### Daily Add Flow:
    1. Ask for item Name
    2. Ask for day goal
    3. Loop Ask for what item we want to decrease to compensate for changes until we are balanced
    4. Return


## Glossary:
- weight* is the weight on the roll for success. Calculated by suming applicable weights and dividing the chosen weight by the sum to get a chance. (if all weights sum to 10, and your item is weighted 2.05, you have a 20.5% chance of rolling that item as a success)
- Tier* is not used in all modes, and each item defaults to "common" in the file unless otherwise defined. 
