---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Energy-Slots'
---

# \[细节\] 能量槽

##  添加能量槽

`EnergySlot Assembly::setEnergySlot(int x, int y, ComponentFace face, int capacity)`

* x,y - 槽的位置.
* face - 可接受输入输出的机器朝向.
* capacity - 槽位 FE 容量.

####  

## 设置访问位置

`EnergySlot::setAccess(boolean input, boolean output)`

* input - 此槽位是否能被外部输入.
* output - 此槽位是否能向外输出.

此方法控制槽位是否接受外部电器\(如线缆\)输入输出. 配方不会被影响.

####  

## 允许电池

`EnergySlot::allowBattery(boolean input, boolean output, boolean drops)`

* input -玩家是否能将电池放入此槽位.
* output - 玩家是否能将从此槽位拿出电池.
* drops - 机器被破坏时, 电池是否会掉落.

此方法只在玩家打开机器 UI 时有效. 目前只能控制你是否能往槽位中放入电池, 但以后也会有充电/放电功能.

####  

## 单元

`EnergySlot::setUnit(String unit)`

* unit - 这行文字会显示为这个槽位的 Tooltip.

单元的 langkey 是 "requious.unit.\[unit\]". 关于如何排版单元, 详见语言文件格式. 默认单元是 "fe".

####  

## 电力损耗

`EnergySlot::setPowerLoss(float loss)`

* loss - 每秒流失多少能量.

当设定为低于 1FE 时候,  则是每多少 Tick 流失 1FE 的效果, 如设置为 0.4 时候, 则是大约 4Tick 流失 1FE.

####  

## 过度填充

`EnergySlot::allowOverfill()`

此方法会将一个槽位设置为可被过度填充的. 这决定了当一个槽位为空时，第一次对此槽位的输入将会无视槽位容量. 比如一个 1000FE 容量的槽位第一次输入时可输入 8000FE. 对输出能量的配方来说很好用.

####  

## 材质

`EnergySlot::setTexture(int x, int y, GaugeDirection direction)` `EnergySlot::setTexture(String texture, int x, int y, GaugeDirection direction)`

* texture - 此槽位的量表使用的材质的位置.
* x,y - 此槽位的量表使用材质时的坐标. 会被自动乘以 18, 也就是说, 输入 0,1 时, 即为从图片 0,18 像素上的位置开始读取材质.
* direction - 此槽位的量表使用材质时的填充方向.

此方法为此槽位显示的量表制定了材质. 默认材质是 "requious:textures/gui/assembly\_gauges.png".

####  

## 自动输出

`EnergySlot::pushEnergy(int size)`

* size - 每 Tick 输出多少 FE.

此方法决定此槽位每 Tick 会向邻近的电池方块输出多少 FE.

