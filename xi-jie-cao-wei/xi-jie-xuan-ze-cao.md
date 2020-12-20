---
description: >-
  https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Selection-Slots
---

# \[细节\] 选择槽

## 前言

选择槽允许你创建一个可以从中选择图标的图标列表.  
 ![](https://camo.githubusercontent.com/5f1c2aa70fba3ef422e8bc83cb32d9e73d0bbacde34bc2a8163013260311c830/68747470733a2f2f692e696d6775722e636f6d2f69676e416e36332e706e67)  
这个列表可以通过使用配方要求来填充.

## 添加选择槽

`SelectionSlot Assembly::setSelectionSlot(int x, int y, String selectionGroup, int index)`

* x,y - 槽的位置.
* face - 可接受输入输出的机器朝向.
* selectionGroup - 此槽位所属的选择组.
* index - 这个槽所代表的选择组中的索引.

请注意, 选择组与普通槽组是完全两回事.

## 设置最大选择数

`SelectionSlot::setMaxSelection(int max)`

* max - 在此槽位所属的选择组中一次可选择多少个图标.

你不需要在一个选择组中的所有图标上调用此方案. 随便一个就可以.

