# DynamicDropRateCalculator
This standalone software is used to automate drop rate statistical analysis.

## Goal:
- Process and display statistical information about loot drops and with various modes.

## Specifics:

- Allow users to build or load loot tables, set/change modes, set mode parameters, and display a wealth of statistical information.
- Allow users to pick a mode, the number of items they want, ask for days or crates or rolls, ask for what % option they want and output general stats as well as what the base item % would need to be to meet the goal.

## Storage Format:
### CSV file with a header in the format of:
    - \<Tier Name\>:\<Tier Weight\>,\<Tier Name>\:\<Tier Weight\>,......
### Each following line in the format of: 
    - \<objectName\>, \<roll Weight\>, \<tier*\>

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



## Statistics:
Take in possible statistical parameters such as:
 - Repeatedly ask for lootbox item name and chance
 - Rolls per drop/lootbox (kem rolls 3 times)
 - Rolls per day (range or static number)
 - Uses CSV for creating and storing loot boxes.   

## Output a varity of information based on input drop/lootbox such as:
 - Info on odds per individual roll
 - Info on odds per drop/lootbox
 - Info on odds per item per day
 - Time and rolls expected for N of each item to be given at 10%, 30%, 50%, 70%, 90%, 95%
 - Test N Sample rolls with output results and stats 


## Glossary:
- weight* is the weight on the roll for success. Calculated by suming applicable weights and dividing the chosen weight by the sum to get a chance. (if all weights sum to 10, and your item is weighted 2.05, you have a 20.5% chance of rolling that item as a success)
- Tier* is not used in all modes, and each item defaults to "common" in the file unless otherwise defined. 
