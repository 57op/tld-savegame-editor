# tld-savegame-editor
The Long Drive Savegame Editor

## Save game location
Savegames are usually stored in `%USERPROFILE%\Documents\TheLongDrive\Saves`.  
A savegame has a `tlds` extension and it's named with a pattern like this: `TLDsaveData_<name>.tlds`.  
Each `tlds` file has a companion `tldsp` file which you might want to modify as well.

## How to use
Just choose your savegame (by browsing or dragging and dropping) in the webapp window.  
There, you can explore savegame data and modify basic fields.

## Example
### Gas Can Refill
1. Start the game with your save game
2. Hold a gas can and, while holding, save and exit (main menu will suffice).
3. Open that save game in the editor
4. Click on `player` entry
5. Look for `heldItemID` field and copy its value (e.g. `-2147482549`)
6. Click on `Expand Near Stuff` on the top of the page
7. Search for the copied value, you should find a `key` field with that value
8. Some fields below you should see a `tank` field with a `amount` subfield
9. Change amount to the desired value (which can be more than 20L but be wary of its weight then...)
10. ???
11. Profit

## Technical limitations and details
I implemented a very **basic** parser of a **subset** of the game format, which happens to be [MS-NRBF](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-nrbf/75b9fe09-be15-475f-85b8-ae7b7558cfe5).  
Since I didn't want to implement a serializer as well, this software only allows you to modify primitive value types (i.e. bool, int, float, double).  
By doing so, I just patch the values in memory and then let you download the patched version.  
This means you cannot add or remove items to your inventory, and whatnot, but just modify the ones you have.  
At this time, I don't plan doing further development on this project as I just did it for fun.  
