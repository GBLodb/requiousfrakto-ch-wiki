---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-SlotVisual'
---

# \[细节\] 槽位效果

## 基础槽位效果

### 一个类似物品槽的普通槽位:

`SlotVisual mods.requious.SlotVisual.itemSlot()`

### 一个带有红色刻度, 类似流体容器的槽位:

`SlotVisual mods.requious.SlotVisual.fluidSlot()`

### 一个红色的垂直填充的能量表, 类似 RF 电表:

`SlotVisual mods.requious.SlotVisual.energySlot()`

### 一个带有白色 'i' 标志的蓝色圆圈, 类似 JEI 中的信息分类:

`SlotVisual mods.requious.SlotVisual.infoSlot()`

### 一个如果被选中就会显示红色选择标记的空槽位, 类似 BuildCraft 中的装配桌子:

 `SlotVisual mods.requious.SlotVisual.selectionSlot()`

### 接下来的 4 个是箭头样式的的仪表, 并按照箭头的方向进行填充:

```text
SlotVisual mods.requious.SlotVisual.arrowRight()
SlotVisual mods.requious.SlotVisual.arrowDown()
SlotVisual mods.requious.SlotVisual.arrowLeft()
SlotVisual mods.requious.SlotVisual.arrowUp()
```

## 创建一个简单的槽位效果

`SlotVisual mods.requious.SlotVisual.createSimple(String texture, int x, int y)`

* texture - 此仪表所使用材质的位置.
* x,y - 此槽位的量表使用材质时的坐标. 会被自动乘以 18, 也就是说, 输入 0,1 时, 即为从图片 0,18 像素上的位置开始读取材质.

## 创建一个简单的仪表槽位效果

`SlotVisual mods.requious.SlotVisual.createGauge(String texture, int x1, int y1, int x2, int y2, GaugeDirectionCT direction, boolean inverse, @Optional int width, @Optional int height, @Optional int[] rgb)`

* texture - 此仪表所使用材质的位置.
* x1,y1 - 仪表的背景部分, 如果使用宽度/高度, 必须是左上角.
* x2,y2 - 仪表的填充部分, 如果使用宽度/高度, 必须是左上角, 将覆盖背景部分.
* direction - 填充仪表时的方向.
* inverse - 是否反向填充. 意味着槽位越满, 槽位效果看起来反而会更空.
* width, height - \( 默认为1 \), 仪表的大小, 以槽位为单位.
* rgb - 为此槽位添加一个 RGBA 或 RGB 格式的着色. \( 例如 \[255,64,16\] 或 \[255,255,255,128\]\).

## 创建一个复杂的槽位效果

`SlotVisual mods.requious.SlotVisual.create(int width, int height)`

* width, height - 槽位效果的大小, 以槽位为单位.

`SlotVisual::addPart(String texture, int x, int y, @Optional int[] rgb)`  
 在槽位效果中添加一个静态元素.

* texture - 此元素所使用材质的位置.
* x,y - 此槽位的量表使用材质时的坐标.
* rgb - 为此槽位添加一个 RGBA 或 RGB 格式的着色.

`SlotVisual::addDirectional(String texture, int x, int y, GaugeDirectionCT direction, boolean inverse, @Optional int[] rgb)`  
 Adds a directional part to the slot visual. This part will fill in the direction specified, just like a simple gauge, but multiple parts that fill in different directions can easily be supplied.

为槽位效果添加一个方向性元素. 此元素将按照指定的方向被填充, 类似简易量表, 但可以很简单的添加多个不同方向的元素。

* texture - 此元素所使用材质的位置.
* x,y - 此槽位的量表使用材质时的坐标.
* direction - 填充元素时的方向.
* inverse - 是否反向填充. 意味着槽位越满, 槽位效果看起来反而会更空.
* rgb - 为此槽位添加一个 RGBA 或 RGB 格式的着色.

