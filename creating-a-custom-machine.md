---
description: >-
  https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BWorkflow%5D-Creating-a-Custom-Machine
---

# \[流程\] 新建自定义机器

## 第一步 : JSON 文件

机器将被在 `/config/requious/assembly.json` 中定义, JSON 文件包含一个 JSON 对象的单一列表, 其中一些已预先填充了默认值. 其语法是这样的:

```json
{
  "resourceName": "item_gate",
  "model": "requious:assembly_block",
  "placeType": "Horizontal",
  "hasGUI": true,
  "colorA": {
    "r": 255,
    "g": 255,
    "b": 255,
    "a": 255
  },
  "colorB": {
    "r": 255,
    "g": 255,
    "b": 255,
    "a": 255
  }
}
```

上述 JSON 中的 "model" 所指的并不是真正的模型, 而指向 ``requious/blockstates/assembly_block.json``, 再在此 blockstate 中指向真正的模型文件.

接下来, 你需要创建一个 CraftTweaker 的 ``.zs`` 文件以定义机器的其他元素. 详见 [CraftTweaker 文档](https://docs.blamejared.com/)获取更多相关信息.

所有可用的 ``placeType`` 参数如下 : 

```text
Any
Up
Down
Horizontal
Vertical
HorizontalUp
HorizontalDown
```

## 第二步 : 添加槽位

每台机器有一个 9X5 槽位大小的 GUI, 你为机器添加的插槽都会直接显示在 GUI 上. 在下面的例子中, 我将为上述的 `item_gate` 机器增加 2 个物品槽位.

```csharp
import mods.requious.ComponentFace;

var machine = <assembly:item_gate>;

machine.setItemSlot(1, 1, ComponentFace.back(), 40)
       .setAccess(true, false)
       .setGroup("input");
machine.setItemSlot(3, 1, ComponentFace.front(), 40)
       .setAccess(false, true)
       .setGroup("output");
```

运行此脚本将会为 `item_gate` 机器添加两个槽位:

* 在 `1,1` 的槽位可从机器的 `back` 面交互, 有 `40` 物品的容量,  仅允许 `输入` , 且处于 `input` 组中
* 在 `3,1` 的槽位可从机器的 `front` 面交互, 有 `40` 物品的容量, 仅允许输出, 且处于 `output` 组中. 

每个槽位可以为自己定义多个组. 组是用来与配方交互的. 你只需要在同一个槽位上多次调用 `setGroup` 就可以给它多个组. 大多数类型的插槽必须定义一个 `ComponentFace`, 它定义了此槽位可以从外部交互的位置. 

换句话说, `group` 是用于机器内部交互, `face` 是用于机器外部交互.

另见 : [槽位](slots/).

所有可用的 ```ComponentFace``` 参数如下 : 

```text
ComponentFace.all()
ComponentFace.front()
ComponentFace.back()
ComponentFace.side()
ComponentFace.frontBack()
ComponentFace.frontSide()
ComponentFace.backSide()
ComponentFace.none()
ComponentFace.up()
ComponentFace.down()
ComponentFace.north()
ComponentFace.south()
ComponentFace.east()
ComponentFace.west()
ComponentFace.horizontal()
ComponentFace.vertical()
```

## 第三步 : 配方

一旦你配置好了槽位, 你就可以开始给槽位添加配方了.

```csharp
import mods.requious.AssemblyRecipe;

var tenOfAny = <*>.marked("inputItem")*10;

var transferItem = AssemblyRecipe.create(function(container) {
    container.addItemOutput("output", container.getItem("inputItem"));
}).requireItem("input", tenOfAny);

machine.addRecipe(transferItem);
```

一个更简单的, 更利于理解的例子:
```csharp
import mods.requious.AssemblyRecipe;
var dirtToGravel =
AssemblyRecipe.create(function (container) {

container.addItemOutput("output", <minecraft:gravel>);
}).requireItem("input", <minecraft:dirt>);

machine.addRecipe(dirtToGravel);
```

配方由一个配方函数和任何数量的需求组成. 尽管可以在配方函数中执行任何计算. 但最简单的方法是只向容器中添加输出. 配方必须使用 `addRecipe` 方法被添加到机器中.

此配方将会从 `input` 组的任意一个槽位输入任意十个物品, 在输出到 `output` 组中任意一个有效槽位. 从例子中可以看出, 配方是支持标记的. 如有需要, `transferItem` 配方也可以直接被其他机器重新调用.

另见 : [配方](recipes.md).

## 第四步 : JEI

从上面的例子可以看出, 配方可以被制作的十分复杂, 且即使是再简单的配方, 在被转换成 JEI 配方时效果可能也非常差. 解决方案则是单独定义 JEI 配方 : JEI 配方和机器配方其实是完全分离的, 机器的表示方式和在 JEI 中的表示方式也是分开的.

所以要创建一个 JEI 处理器, 我们需要先创建一个 JEI 表示. 这点与第二步中的定义槽位类似.

```csharp
import mods.requious.SlotVisual;

var arrowRight = SlotVisual.create().addPart("requious:textures/gui/assembly_gauges.png", 0, 8);

machine.setJEIItemSlot(0,0,"input");
machine.setJEIItemSlot(2,0,"output");
machine.setJEIDurationSlot(1,0,"duration", arrowRight);
```

这样就创建了一个与第二步的槽相匹配的两个槽和一个额外的持续时间槽, 此持续时间槽将被 JEI 处理成一个装饰箭头 \( 如果为配方设置了处理时间, 此箭头还将在其 Tooltip 中显示处理配方所需的时间 \).

所有的 JEI 槽位必须定义一个组. 且 JEI 插槽只能属于一个组, 不能属于多个.

现在我们已经创建了 GUI 的表示, 接下来创建配方的表示, 并将其添加到 JEI 处理器中.

```csharp
var transferItemJEI = AssemblyRecipe.create(function(container) {
    container.addItemOutput("output", <minecraft:cobblestone>);
}).requireItem("input", <minecraft:cobblestone>);

machine.addJEIRecipe(transferItemJEI);
```
