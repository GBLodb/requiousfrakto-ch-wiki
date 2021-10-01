---
description: 世界输出可以使你的输出不再是机器内的物品, 流体之类的输出, 它可以使你跟世界交互
---

# \[细节\] 世界输出

## 调用

需要在 function 里返回一个 bool

```csharp
import mods.requious.AssemblyRecipe;

AssemblyRecipe.create(function(container) {
    container.addWorldOutput("worldOutput", function(machine) {
        return true
    });
});
```

## 上述的 `function(container) {}` 是什么?

此为 [MachineContainer](machine-container.md)

* 例子

```csharp
import crafttweaker.world.IFacing;
import mods.requious.AssemblyRecipe;

var recipe = AssemblyRecipe.create(function(container) {
    if(!container.jei) { // 判断配方是否添加到 JEI, 是则不执行大括号内的代码
        container.addWorldOutput("worldOutput", function(machine) {
            var world = machine.world;

            if(!world.remote) {
                world.setBlockState(<blockstate:minecraft:iron_block>, machine.pos.getOffset(IFacing.up(), 1));
                return true;
            }
            return false;
        });
    }
});

// 然后把这个配方添加到机器里 (addRecipe)

```
