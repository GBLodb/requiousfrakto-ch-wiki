---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Laser-Slots'
---

# \[细节\] 激光槽

## 前言

激光在 RequiousFrakto 中是一种特殊的能量供应方式.

* 它们可以定义一个能量量和一个能量类型.
* 接收器可以过滤它们接受的能量类型.
* 激光器发射器是无线的, 其目标是可以定义的一定区域.
* 方块不会干扰激光传输.
* 聚集在同一接收器上的多到激光将被合并为一个功率值.
* 激光发射器对朝向有要求 : 一台激光接收器在北面的机器只从北面接受激光.

## 添加激光槽

`LaserSlot Assembly::setLaserSlot(int x, int y, ComponentFace face)`

* x,y - 槽的位置.
* face - 可接受激光的机器朝向.

## 设置访问位置

`LaserSlot::setAccess(boolean input, boolean output)`

* input - 此槽位是否能被外部输入.
* output - 此槽位是否能向外输出.

## 设置激光类型

`LaserSlot::setType(String type)`

* type - 要添加的类型.

此方法限制可输入的激光的类型.

## 限制激光功率

`LaserSlot::setLimit(int min, int max)`

* min - The minimum cutoff at which a laser is not accepted.
* max - The maximum cutoff at which a laser is not accepted.

此方法限制激光接收功率范围. 功率低于最小值的激光发射器不会被接受，而高于最大值的激光发射器则被限制在最大值以内.

## 设置目标区域

`LaserSlot::setArea(int x1, int y1, int z1, int x2, int y2, int z2)`

* x1,y1,z1 - The first point of the defined area
* x2,y2,z2 - The second point of the defined area

区域是相对于向上的方向. 旋转时，正 y 指向机器的前方.

