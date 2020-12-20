---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-JEI'
---

# \[细节\] JEI

## 向 JEI 中添加配方

`Assembly::addJEIRecipe(AssemblyRecipe recipe)`

* recipe - 要添加的配方.

所有添加到 JEI 的配方都会执行他们的配方函数. 此容器不能输入任何已标记的输入! 此容器将会被标记为由 JEI 处理, 意味着你可以检查和调整一个配方在JEI中的显示. 也就是说, 如果你认为一个自动添加的配方有问题, 你可以手动添加正确的配方.

## 配方方式

`Assembly::addJEIRecipe(IItemStack catalyst)`

* catalyst - 将一个 IIteamStack 注册为配方方式.

配方方式是数个以 JEI 分类图标形式现实的 IItemStack, 位于当前显示配方的左侧. 它们代表了所有可以执行此配方的机器.

## 物品槽

`Assembly::setJEIItemSlot(int x, int y, String group, {optional} SlotVisual visual)`

* x,y - 槽位在 JEI 中的位置.
* group - 此槽位所属的需求/结果组.
* visual - 此槽位的额外视觉效果.

见 [\[细节\] 物品槽.](slots/item-slot.md)

## 流体槽

`Assembly::setJEIFluidSlot(int x, int y, String group)`

* x,y - 槽位在 JEI 中的位置.
* group - 此槽位所属的需求/结果组.

见 [\[细节\] 流体槽](slots/fluid-slot.md).

## 能量槽

`Assembly::setJEIEnergySlot(int x, int y, String group, {optional} String unit)`

* x,y - 槽位在 JEI 中的位置.
* group - 此槽位所属的需求/结果组.
* unit - 此单元将显示为此槽位的 Tooltip, 默认为 "none".

见 [\[细节\] 能量槽](slots/energy-slot.md).

## 激光槽

`Assembly::setJEILaserSlot(int x, int y, String group)`

* x,y - 槽位在 JEI 中的位置.
* group - 此槽位所属的需求/结果组.

见 [\[细节\] 激光槽](slots/laser-slot.md).

## 选择槽

`Assembly::setJEISelectionSlot(int x, int y, String group, {optional} SlotVisual visual)`

* x,y - 槽位在 JEI 中的位置.
* group - 此槽位所属的需求/结果组.
* visual - An optional visual to render on this slot.

见 [\[细节\] 选择槽](slots/selection-slot.md).

## 持续时间槽

`Assembly::setJEIDurationSlot(int x, int y, String group, SlotVisual visual)`

* x,y - 槽位在 JEI 中的位置.
* group - 此槽位所属的需求/结果组.
* visual - 此槽位的额外视觉效果.

见 [\[细节\] 持续时间槽](slots/duration-slot.md).

## 装饰

`Assembly::setJEIDecoration(int x, int y, String group, SlotVisual visual)`

* x,y - 槽位在 JEI 中的位置.
* group - 此槽位所属的需求/结果组.
* visual - 此槽位的额外视觉效果.

