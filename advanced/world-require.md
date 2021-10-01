---
description: 世界需求可以使你根据世界内的不同来决定机器工不工作 (返回 true 代表可以工作, false 代表不可以工作)
---

# \[细节\] 世界需求

## 调用

需要在 function 里返回一个 bool

```csharp
AssemblyRecipeObj.requireWorldCondition("group", function(machine) {
    return true;
});
```

## 上述的 `function(container) {}` 是什么?

此为 [MachineContainer](machine-container.md)

* 例子

```csharp
import crafttweaker.world.IFacing;
import mods.requious.AssemblyRecipe;

var recipe = AssemblyRecipe.create(function(container) {
    container.addItemOutput("output", <minecraft:iron_ingot>);
}).requireWorldCondition("world_condition", function(machine) {
    var world = machine.world;

    if(!world.remote && world.getBlockState(machine.pos.getOffset(IFacing.down(), 1) == <blockstate:minecraft:stone>)) {
        return true;
    }

    return false;
}, 1);

// 然后把这个配方添加到机器里 (addRecipe)

```
