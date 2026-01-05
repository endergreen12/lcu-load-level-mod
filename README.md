# LCU-Load-Level-Mod
## What does this mod do
As the name suggests, this mod will enable you to load any levels

https://github.com/user-attachments/assets/a1be8de6-f1bc-40f5-95ea-519a46ab4cd5
## How to install
### 1. Extract game files
#### Download files
You will need:
- QuickBMS
- ttgames.bms

You can download them from this website: https://aluigi.altervista.org/quickbms.htm
#### Place files
Place them in the root of the LCU folder like this:

<img width="627" height="279" alt="image" src="https://github.com/user-attachments/assets/189d51e2-55fb-4ffe-be27-71f120e03316" />

#### Configure and run
Set FORCE_CRC_BITS to 32 in ttgames.bms

<img width="533" height="102" alt="image" src="https://github.com/user-attachments/assets/0c1d9454-1cf2-4848-a057-634c489f390f" />

Open terminal at the folder, and run this command:
```
.\quickbms.exe -F "{}.DAT" .\ttgames.bms .
```

Wait until it's done
#### Move or delete original files
Move or delete All .DAT files and `__DISC__` file in order to make the game use extracted files

In any case, it’s fine as long as those files are not located in the LCU folder
### 2. Modify game files
#### Install "Load_Level" cutscene
Firstly, download CUT folder from this repository, and merge it into the LCU folder

Next, copy `CUT\LOADING_SCREEN\LOADINGSCREEN_01_CHERRY\LOADINGSCREEN_01_CHERRY_NXG.CU3` to `CUT\LOAD_LEVEL\`, and then rename it to `LOAD_LEVEL_NXG.CU3`

Then, open `CUT\CUTSCENES_MAIN.TXT`, and add those lines:
```
;; =====================================
;; Custom
;; =====================================

txt_file "cut\Load_Level\Load_Level.txt"
```
like this:

<img width="443" height="429" alt="image" src="https://github.com/user-attachments/assets/94183573-cf04-4cf8-aa40-e4139ddca547" />

#### Edit codes
Open `JOBS\SCRIPTS\CITY_SETUP\LEVEL_TRANSITIONS\HUB.SF`, go to line 202 and locate `Function FN_LCPD()`

Set `tCutscene` to `Load_Level`, comment out `goto ShowSummaryScreen();` and add `PlayCutscene(cutscene= tCutscene);`

like this:

<img width="502" height="254" alt="image" src="https://github.com/user-attachments/assets/07d99128-4503-4b50-8638-3e1a86cbf769" />

And you're done!

## How to use
You can specify which level to load with the level property in `CUT\LOAD_LEVEL\LOAD_LEVEL.TXT`

<img width="371" height="218" alt="image" src="https://github.com/user-attachments/assets/6c808a59-a096-401f-b1ae-f5e56abb67ea" />

Approaching the entrance of the police station loads the specified level

## Notes
The game refuses to load levels which has test_level property, so remove it if you want to load the level

<img width="355" height="96" alt="image" src="https://github.com/user-attachments/assets/8b9783cf-3bdc-4067-8f86-0c6399e0d851" />
