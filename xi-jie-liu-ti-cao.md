---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Fluid-Slots'
---

# \[细节\] 流体槽

## 添加流体槽

`FluidSlot Assembly::setFluidSlot(int x, int y, ComponentFace face, int capacity)`

* x,y - 槽的位置.
* face - 可接受输入输出的机器朝向.
* capacity - 槽位 mb 容量.

####  

## 设置访问位置

`FluidSlot::setAccess(boolean input, boolean output)`

* input - 此槽位是否能被外部输入.
* output - 此槽位是否能向外输出.

此方法控制槽位是否接受外部流体输入输出. 配方不会被影响.

####  

## 允许桶

`FluidSlot::allowBucket(boolean input, boolean output, boolean drops)`

* input - 玩家是否能将液体容器放入此槽位.
* output - 玩家是否能从此槽位取走液体容器.
* drops - 机器被破坏时, 是否掉落液体容器.

此方法只在玩家打开机器 UI 时有效. 目前只能控制你是否能往槽位中放流体容器, 但以后也会像 GTCE 机器一样允许清空和填充流体容器.

####  

## 过度填充

`FluidSlot::allowOverfill()`

此方法会将一个槽位设置为可被过度填充的. 这决定了当一个槽位为空时，第一次对此槽位的输入将会无视槽位容量. 比如一个 1000mb 容量的槽位第一次输入时可输入 8000mb. 对输出流体的配方来说很好用.

####  

## 自动输出

`FluidSlot::pushFluid(int size)`

* size - 每 Tick 输出多少液体.

此方法决定此槽位每 Tick 会向邻近的流体容器输出多少液体.

