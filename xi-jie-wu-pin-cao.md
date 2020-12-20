---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Item-Slots'
---

# \[细节\] 物品槽

###  添加物品槽

`ItemSlot Assembly::setItemSlot(int x, int y, ComponentFace face, int capacity)`

* x,y - Position of the slot.
* face - Which side of the machine accesses this slot.
* capacity - How many items fit into the slot. Can be more than 64!

####  

#### Setting Access

`ItemSlot::setAccess(boolean input, boolean output)`

* input - Whether this slot can be inserted into.
* output - Whether this slot can be extracted from.

This method only affects how the slot reacts to piping items in or out. The players hand and recipe movements should be unaffected.

####  

#### Setting Hand Access

`ItemSlot::setHandAccess(boolean input, boolean output)`

* input - Whether a player can put items into this slot.
* output - Whether a player can take items from this slot.

This method only affects interactions by the player in a gui.

####  

#### Overfill

`ItemSlot::allowOverfill()`

This method sets a slot to be overfillable. This determines that if the slot is empty, the capacity of the slot will be completely ignored on the first insertion. For example, a slot with 8 capacity can have 32 items inserted _only on the first insertion_. This is useful for output slots from recipes.

####  

#### No Drop

`ItemSlot::noDrop()`

This method sets a slot to not drop its contents if the machine is broken.

####  

#### Auto-Output

`ItemSlot::pushItem(int size)` `ItemSlot::pushItem(int size, int slot)`

* size - How many items are pushed per tick
* slot - Which slot will be inserted into in the target inventory. Default is -1 for any slot.

This method sets a slot to automatically output to inventories connected on its face.

