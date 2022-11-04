---
description: 世界输出使你不再仅限于机器内数量的加加减减, 它可以使你跟世界交互
---

# \[细节\] 世界输出

## 导包

`import requious.fluid.IWorldFunction;`

## 调用

需要在 function 里返回一个 bool

```csharp
import mods.requious.AssemblyRecipe;

AssemblyRecipe.create(function(container) {
    container.addWorldOutput("worldOutput", function(machineContainer) {
        return true;
    });
});
```

## 上述的函数中的 `machineContainer` 是什么?

此为 [MachineContainer](machine-container.md) 类的实例

* 例子

```csharp
import mods.requious.AssemblyRecipe;
import crafttweaker.world.IFacing;
import crafttweaker.world.IWorld;
import crafttweaker.world.IBlockPos;

var recipe = AssemblyRecipe.create(function(container) {
    if(!container.jei) { // 判断配方是否添加到 JEI, 是则不执行大括号内的代码
        container.addWorldOutput(function(machineContainer) {
            var world = machineContainer.world;

            if(!world.remote) {
                world.setBlockState(<blockstate:minecraft:iron_block>, machineContainer.pos.getOffset(IFacing.up(), 1));
                return true;
            }
            return false;
        });
    }
});

// 然后把这个配方添加到机器里 (addRecipe)

```
