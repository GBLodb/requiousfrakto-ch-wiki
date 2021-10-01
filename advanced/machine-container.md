# \[细节\] MachineContainer

## 导包

`import mods.requious.MachineContainer;`

## 可用 ZenGetter

| ZenGetter | 返回类型 | 描述 |
| :----- | :----- | :--- |
| world | IWorld | 获取机器所在的世界 |
| pos | IBlockPos | 获取机器的坐标 |
| block | IBlock | 返回机器方块 (data getter 不为 null) |
| state | IBlockState | 返回机器方块的方块状态 |
| facing | IFacing | 返回机器的朝向 |
| random | [Random](random.md) | 返回一个 Random 对象 |

## 可用 ZenMethod

| ZenMethod | 返回类型 | 描述 |
| :-------- | :------ | :---- |
| getInteger(String name) | int | 获取指定 name 的 int 数据 |
| getDouble(String name) | double | 获取指定 name 的 double 数据 |
| getString(String name) | string | 获取指定 name 的 String 数据 |
| getItem(String name) | IItemStack | 获取指定 name 的物品 |
| getFluid(String name) | ILiquidStack | 获取指定 name 的流体 |
| getVector(String name) | IVector3d | 获取指定 name 的向量 |
| setInteger(String name, int value) | void | 设置指定 name 的 int 数据 |
| settDouble(String name, double value) | void | 设置指定 name 的 double 数据 |
| setString(String name, String value) | void | 设置指定 name 的 String 数据 |
| setFacing(String name, IFacing value) | void | 设置指定 name 的 IFacing 数据 |
| setColor(String name, [ColorCT](https://github.com/DaedalusGame/RequiousFrakto/blob/master/src/main/java/requious/compat/crafttweaker/ColorCT.java) value) | void | 设置指定 name 的 Color 数据 |
| setItem(String name, IItemStack value) | void | 设置指定 name 的物品 |
| setFluid(String name, ILiquidStack value) | void | 设置指定 name 的流体 |
| setVector(String name, double x, double y, double z) | void | 设置指定 name 的向量 |
| getItem(int x, int y) | IItemStack | 获取指定槽的物品 |
| getFluid(int x, int y) | ILiquidStack | 获取指定槽的流体 |
| getEnergy(int x, int y) | int | 获取指定槽的所有能量 |
| setItem(int x, int y, IItemStack stack) | void | 设置指定槽的物品 |
| setFluid(int x, int y, ILiquidStack stack) | void | 设置指定槽的流体 |
| setEnergy(int x, int y, int amount) | void | 设置指定槽的能量 |
| insertItem(String group, IItemStack stack) | IItemStack | 插入一个物品到指定组 |
| extractItem(String group, IIngredient filter) | IItemStack | 从一个指定组提取物品 |
| insertFluid(String group, ILiquidStack stack) | ILiquidStack | 插入流体到指定组 |
| extractFluid(String group, IIngredient filter) | ILiquidStack | 从一个指定组提取流体 |
| insertEnergy(String group, int energy) | int | 插入能量到指定组 |
| extractEnergy(String group, int energy) | int | 从一个指定组提取能量 |