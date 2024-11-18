# 工具类
在本章节中将会提供简单的工具类型的写法和可调用的方法

## 基础写法
```js
StartupEvents.registry("item", event => {
    // 斧子
    event.create("meng:my_axe", "axe")
    // 锄头
    event.create("meng:my_hoe", "hoe")
    // 镐子
    event.create("meng:my_pickaxe", "pickaxe")
    // 铲子
    event.create("meng:my_shovel", "shovel")
    // 剑
    event.create("meng:my_sword", "sword")
})
```
以上是kubejs提供的工具类型

## 可调用的方法
|                 方法名                 |                         传入参数                         |                                 用处                                 | 返回类型 |
| :------------------------------------: | :------------------------------------------------------: | :------------------------------------------------------------------: | :------: |
|speedBaseline()|Float| 设置**攻击速度基准**，原版默认情况下由**工具类型**和**工具材料**决定：剑类为-2.4、锹类为-3、镐类为-2.8；斧类中木质与石质为-3.2、铁质为-3.1、金质与钻石质与下界合金质为1；锄类中木质与金质为-3、石质为-2、铁质为-1、钻石质与下界合金质为0。<br>*玩家20游戏刻（1秒）内能进行完整伤害近战攻击的次数为攻击速度*。<br>工具的实际攻击速度受到**攻击速度基准**和**玩家属性attack_speed（默认为4）**影响，实际攻击速度为二者相加。|this|
|speed()|Float|设置**挖掘倍率**，原版默认情况下由**工具材料**决定：木质为2x、石质为4x、铁质为6x、钻石质为8x、下界合金质为9x、金质为12x|this|
|attackDamageBaseline()|Float|设置**基准攻击伤害**，原版默认情况下由**工具类型**决定：剑类为3、锹类为1.5、镐类为1、斧类为6、锄类为0。<br>工具的实际攻击伤害受到**攻击伤害基准**和**攻击伤害加成**和**玩家属性attack_damage（默认为1）**影响，实际攻击伤害为三者相加|   this|
|attackDamageBonus()|Float|设置**攻击伤害加成**，原版默认情况下由**工具材料**决定：木质为+0、石质为+1、铁质为+2、钻石质为+3、下界合金质为+4、金质为+0。<br>工具的实际攻击伤害受到**攻击伤害基准**和**攻击伤害加成**和**玩家属性attack_damage（默认为1）**影响，实际攻击伤害为三者相加|this|
| modifyTier(tier => {...})|Function|移步至添加工具材料[添加工具材料](/KubeJSBasic/Customs/TierRegistry.md#注册工具材料)|this|
|tier(Tier)|[mcwiki](https://zh.minecraft.wiki/w/%E5%93%81%E8%B4%A8)|设置工具材料，原版默认情况下有6种工具材料：木质（wooden）、石质（stone）、铁质（iron）、钻石质（diamond）、下界合金质（netherite）、金质（gold）|this|