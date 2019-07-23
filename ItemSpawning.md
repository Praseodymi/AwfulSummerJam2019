#Item Spawning

##Adding New Items
====
Add new Items to the ItemLibrary array in the Game Instance.

##Add Item to a Level
==== 
Add the index of the Item in the ItemLibrary to the <LevelName>Items array. So 
to add an item that will appear in the Basement and Lava levels add the index
to both the BasementItems and LavaItems arrays.

##Operation
====
When the HubLevel is loaded a map is populated using the GenItems function in 
ASJ19_GameInstance. that uses the level name as a
key and the item id as a value. When the streaming levels are loaded the
shelf in the level uses that array to find which item it should contain.

The item map contains only the items that actually exist, but the shelves
will have an ItemIndex of -1 if they don't contain an item.

If the shelf is not in a streamed level it will not receive its item index
as it will attempt to get one before the map has been populated. I'll fix this
if it is ever an issue.

The shelves have a LevelName string that must be filled manually, there seems
to be know way to get the name of the streamed level containing the object.

###GenItems
====
This function takes the number of items to be generated as a parameter. This is
called from the Hub level loading blueprint, and is determined by a switch with
the current level number as an input.

##Todo
====
Place the new shelf blueprint in the levels instead of just the mesh.
Actually display the items on the UI.
The Item struct will need to be extended with an icon to display.