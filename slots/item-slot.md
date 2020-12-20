---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Item-Slots'
---

# \[细节\] 物品槽

##  添加物品槽

`ItemSlot Assembly::setItemSlot(int x, int y, ComponentFace face, int capacity)`

* x,y - 槽的位置.
* face - 可接受输入输出的机器朝向.
* capacity - 槽位物品容量, 不能多于 64.

## 设置访问位置

`ItemSlot::setAccess(boolean input, boolean output)`

* input - 此槽位是否能被外部输入.
* output - 此槽位是否能向外输出.

此方法控制槽位是否接受外部物品输入输出. 玩家手动摆放和配方不会被影响.

## 允许互动

`ItemSlot::setHandAccess(boolean input, boolean output)`

* input - 玩家是否能将物品放入此槽位.
* output - 玩家是否能从此槽位取走物品.

此方法只在玩家打开机器 UI 时有效.

## 过度填充

`ItemSlot::allowOverfill()`

此方法会将一个槽位设置为可被过度填充的. 这决定了当一个槽位为空时，第一次对此槽位的输入将会无视槽位容量. 比如一个 8 物品容量的槽位第一次输入时可输入 32 物品. 对输出物品的配方来说很好用.

## 取消掉落

`ItemSlot::noDrop()`

此方法决定在机器被破坏时, 槽内的物品是否会掉落.

## 自动输出

`ItemSlot::pushItem(int size)` `ItemSlot::pushItem(int size, int slot)`

* size - 每 Tick 输出多少物品.
* slot - 向目标的哪一个槽位输出物品, 默认为 -1, 即任意槽.

此方法将槽位设置为会向邻近的物品栏自动输出物品.

