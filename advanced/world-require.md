---
description: 世界需求可以使你根据世界内的不同以决定机器工作与否
---

# \[细节\] 世界需求

## 导包

`import requious.fluid.IWorldFunction;`

## 调用

需要在 function 里返回一个 bool (返回 ``true`` 代表可以工作, ``false`` 代表不可以工作)

```csharp
AssemblyRecipeObj.requireWorldCondition("group", function(machineContainer) {
    return true;
});
```

## 上述的函数中 `machineContainer` 是什么?

此为 [MachineContainer](machine-container.md) 类的实例

* 例子

```csharp
import mods.requious.AssemblyRecipe;
import requious.fluid.IWorldFunction;
import crafttweaker.world.IFacing;
import crafttweaker.world.IWorld;
import crafttweaker.world.IBlockPos;

var recipe = AssemblyRecipe.create(function(container) {
    container.addItemOutput("output", <minecraft:iron_ingot>);
}).requireWorldCondition("world_condition", function(machineContainer) {
    var world as IWorld = machineContainer.world;
    var pos as IBlockPos = machineContainer.pos;
    if(!world.remote && world.getBlockState(pos.getOffset(IFacing.down(), 1)) == <blockstate:minecraft:stone>){
        return true;
    }
    return false;
}, 1);

// 然后把这个配方添加到机器里 (addRecipe)

```
