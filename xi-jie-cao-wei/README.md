---
description: 'https://github.com/DaedalusGame/RequiousFrakto/wiki/%5BDetails%5D-Slots'
---

# \[细节\] 槽位

## 槽位种类

* [物品槽](xi-jie-wu-pin-cao.md)
* [流体槽](xi-jie-liu-ti-cao.md)
* [能量槽](xi-jie-neng-liang-cao.md)
* [激光槽](xi-jie-ji-guang-cao.md)
* [选择槽](xi-jie-xuan-ze-cao.md)
* [持续时间槽](xi-jie-chi-xu-shi-jian-cao.md)

## 所有种类的槽位都可用的方法

### 组

`Slot::setGroup(String group)`

* group - 要将槽位添加到的组.

将槽位添加到一个组中. 组用于配方对槽位的内部访问. 一个槽可以属于组，你可以通过多次调用这个方法来为槽位添加更多所属的组.

### 隐藏槽

`Slot::setHidden()`

将槽位设置为在 GUI 中隐藏, 可以避免玩家直接于槽位互动.

