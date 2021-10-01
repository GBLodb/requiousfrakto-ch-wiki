---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Recipes'
---

# \[细节\] 配方

## 创建配方

`AssemblyRecipe mods.requious.AssemblyRecipe.create(function(container) { ... })`

## 需求项

需求项是一个有序列表, 这意味着它们将按照被添加到配方中的顺序被结算. 这一点在创建具有持续时间槽或选择槽的配方时很重要.

如果您将选择槽放在任何其他需求项之前, 相关的选择列表将始终显示图标.

如果您将选择槽放在其他需求项之后, 则只有在满足这些需求项之后才会显示选择槽图标.

持续时间始终应是最后一个要检查的需求项.

所有的需求项只能从一个槽中抽取, 所以如果你在一个槽中有 10 个物品, 而在另一个槽中有 10 个物品, 就不能满足一个 20 物品的需求项. 

### 物品

`AssemblyRecipe::requireItem(String group, IIngredient ingredient)`  
 `AssemblyRecipe::requireItem(String group, IIngredient ingredient, int min, int max)`

* group - 从哪个组抽取物品.
* ingredient - 需要抽取的物品.
* min - 最少需要抽取多少物品.
* max - 最多需要抽取多少物品.

默认情况下, `min` 和 `max` 的大小与 `IIngredient` 相同. 你可以标记 \(见 CraftTweaker 文档\) `IIngredient`, 使其在容器中可用.

### 流体

`AssemblyRecipe::requireFluid(String group, ILiquidStack ingredient)`  
 `AssemblyRecipe::requireFluid(String group, ILiquidStack ingredient, int min, int max)`

* group - 从哪个组抽取流体.
* ingredient - 需要抽取的流体.
* min - 最少需要抽取多少 mb 流体.
* max - 最多需要抽取多少 mb 流体.

默认情况下, `min` 和 `max` 的值与 `ILiquidStack` 相同. 你可以标记 \(见 CraftTweaker 文档\) `ILiquidStack`, 使其在容器内可用.

### 能量

`AssemblyRecipe::requireEnergy(String group, int energy, String mark)`  
 `AssemblyRecipe::requireEnergy(String group, int min, int max, String mark)`

* group - 从哪个组抽取能量.
* energy - 需要抽取的能量.
* min - 最少需要抽取多少能量.
* max - 最多需要抽取多少能量.
* {可选} mark - 设置此变量使容器上的能量提取量可用.

### 激光

`AssemblyRecipe::requireLaser(String group, int energy, String mark, SlotVisual slotVisual)`  
 `AssemblyRecipe::requireLaser(String group, String type, int energy, String mark, SlotVisual slotVisual)`

* group - 从哪个组抽取激光能量.
* type - 抽取何种激光能量.
* energy - 最少需要抽取多少激光能量.
* {可选} mark - 设置此变量使容器上的激光能量提取量可用.
* {可选} slotVisual - 此激光需求在 JEI 中呈现的槽位效果.

Marking Laser requirements will give you all power currently flowing into the machine, not just the energy you actually required.

标记激光需求会提供当前流入机器的所有功率, 而不仅仅是所需的实际功率.

### 世界需求

`AssemblyRecipe::requireWorldCondition(String group, function(machine) {return true}, int interval)`

* group - 组名 (随便填, 但不要重复)
* function(machine) {{return true} - 请看[世界需求](advanced/world-require.md)
* interval - 多久触发一次

### 选择

`AssemblyRecipe::requireSelection(String group, IItemStack stack, boolean reset)`

* group - 从哪个组抽取需求. 注意, 此处指的是普通组, 不是选择组.
* stack - 在选择组中渲染的图标.
* reset - 是否在完成配方后重置选择.

### 持续时间

`AssemblyRecipe::requireDuration(String group, int duration)`

* group - 从哪个组获取持续时间, 这需要一个持续时间槽位.
* duration - 执行此配方所需的时间, 以 Tick 为单位.

一个配方可以拥有多个持续时间, 每次执行配方都填充一个.

### 子处理

`AssemblyRecipe::setSubProcess(String processGroup)`

* processGroup - 此配方将在哪个处理组执行.

Sometimes you might want to run multiple recipes per tick. A machine can run one recipe per processGroup.

你可能会想在 1Tick 内处理多个配方. 一台机器可以从每个处理组执行一个配方.

## 容器

`mods.requious.RecipeContainer`

Recipe containers are used to exchange data between the machine and the recipe function. You can use the container to get marked ingredients and to post outputs.

配方容器用于在机器和配方功能之间交换数据. 可使用容器来获取标记的原料和标记输出.

### JEI

`boolean RecipeContainer::jei` `boolean RecipeContainer::isJEI()`

使用此属性来检查此配方函数是否在 JEI 中执行. 当配方函数在 JEI 中执行时，则不会返回任何标记. 可使用该属性进行替代配方计算, 以便在 JEI 中显示。

### 标记

`IItemStack RecipeContainer::getItem(String mark)` `ILiquidStack RecipeContainer::getFluid(String mark)` `int RecipeContainer::getEnergy(String mark)`

You can use these functions to retrieve previously marked ingredients. For example, you can create a recipe that accepts any oreIron with a mark "ironOre", and when queried with `container.getItem("ironOre")` you will receive the specific ore stack that was matched.

使用这些函数来检索之前标记的原料. 如创建一个接受任何带有 `"ironOre "` 标记的铁矿石的配方, 当使用 `container.getItem("ironOre")` 查询时, 则会返回匹配的特定 `ore stack`.

### 物品

`RecipeContainer::addItemOutput(String group, IItemStack item)`  
 `RecipeContainer::addItemOutput(String group, IItemStack item, int minInsert)`

* group - 向哪个组输出物品.
* item - 输出的物品.
* minInsert - 处理配方所需的实际最少物品量.

### 流体

`RecipeContainer::addFluidOutput(String group, ILiquidStack fluid)`  
 `RecipeContainer::addFluidOutput(String group, ILiquidStack fluid, int minInsert)`

* group - 向哪个组输出流体.
* fluid - 输出的流体.
* minInsert - 处理配方所需的实际最少流体量 \(mb\).

### 能量

`RecipeContainer::addEnergyOutput(String group, int energy)`  
 `RecipeContainer::addEnergyOutput(String group, int energy, int minInsert)`

* group - 向哪个组输出能量.
* energy - 输出的能量.
* minInsert - 处理配方所需的实际最少能量.

### 激光

`RecipeContainer::addLaserOutput(String group, String type, int energy, LaserVisual visual, SlotVisual slotVisual)`

* group - 向哪个组输出激光.
* type - 输出何种激光.
* energy - 输出的激光能量.
* visual - 激光在世界中渲染时的效果.
* {可选} slotVisual - 在 JEI 中显示的槽位效果.

### 世界输出

#### 带有世界输出的配方不能直接添加到 JEI 里

`RecipeContainer::addWorldOutput(function(machine) {return true})`

* function(machine) {return true} - 请看[世界输出](advanced/world-output.md)

## 将配方添加到机器中

`Assembly::addRecipe(AssemblyRecipe recipe)`

将配方添加到机器中, 你可以将一个配方添加到多个机器中.

`Assembly::addJEIRecipe(AssemblyRecipe recipe)`

This will add the recipe to the machine's JEI handler. You can only add a recipe to one machine's JEI handler!

将配方添加到机器的 JEI 处理器. 一台机器的 JEI 处理器中只能添加一个配方.
