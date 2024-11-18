# 添加自定义工具材料与盔甲材料
本章节中将会提到如何注册新的工具材料（或继承）、注册新的盔甲材料（或继承）并使用自定义的盔甲模型贴图

## 注册工具材料
```js
// 在startup_scripts文件夹下
ItemEvents.toolTierRegistry(tool => {
    tool.add('tier_id', tier => {   // 注册新的工具材料
        tier.setUses(225)
        tier.setAttackDamageBonus(1.5)
        tier.setSpeed(6)
        tier.setEnchantmentValue(15)
        tier.setRepairIngredient('#forge:ingots/iron')
        tier.setLevel(2)
    })
    tool.add('tier_id_2', 'parent_tier', tier => {  // 继承'parent_tier'工具材料并注册新的工具材料
        /* .... */
    })
})
```

> 参考[wiki](https://zh.minecraft.wiki/w/工具材料)

|方法名                 |参数类型          |用途描述|
|:---:                 |:-----:          |:-----:|
|setUses()             |Integer          |设置**最大耐久度**，该工具材料所有的工具的最大耐久度|
|setAttackDamageBonus()|Float            |设置**攻击伤害加成**<br>工具的实际攻击伤害受到**攻击伤害基准**和**攻击伤害加成**和**玩家属性attack_damage（默认为1）**影响，实际攻击伤害为三者相加|
|setSpeed()            |Float            |设置**挖掘倍率**|
|setEnchantmentValue() |Integer          |设置**附魔能力**，附魔能力越高，在附魔台中遇到到稀有和高级附魔的概率越高。为0时无法附魔|
|setRepairIngredient() |物品或物品标签     |设置**修复所用物品**，用于在铁砧中修复工具|
|setLevel()            |Integer          |设置**挖掘等级**，0~4分别为：木质/金质、石质、铁质、钻石质、下界合金质|

> **注意**：工具材料是以字符串形式保存，而非命名空间。在调用时也是如此

## 注册盔甲材料

### 代码部分
```js
// 在startup_scripts文件夹下
ItemEvents.armorTierRegistry(armor => {
    armor.add('tier_id', tier => {  // 注册新的盔甲材料
        tier.setDurabilityMultiplier(5),
        tier.setSlotProtections([0, 0, 0, 1])
        tier.setEnchantmentValue(30)
        tier.setEquipSound('item.armor.equip_leather')
        tier.setToughness(0)
        tier.setKnockbackResistance(0)
        tier.setRepairIngredient('#minecraft:flowers')
    })
    armor.add('tier_id_2', 'parent_tier', tier => {      // 继承'parent_tier'盔甲材料并注册新的盔甲材料
        /* ..... */
    })
})
```

> 参考[wiki](https://zh.minecraft.wiki/w/盔甲材料)

|方法名                    |参数类型          |用途描述|
|:---:                    |:-----:          |:-----:|
|setDurabilityMultiplier()|Integer          |设置**耐久倍率**，各个部位的最大耐久值为**基础耐久值**×**耐久倍率**。各个部位的基础耐久值分别为：头部11、上身18、腿部15、足部13|
|setSlotProtections()     |Integer[]        |设置各部位提供的**护甲值**，传入的参数是一个包含四个整数的数组，索引从0~3分别为足部、腿部、上身、头部的护甲值|
|setEnchantmentValue()    |Integer          |设置**附魔能力**，附魔能力越高，在附魔台中遇到到稀有和高级附魔的概率越高。为0时无法附魔|
|setEquipSound()          |声音事件          |设置**护甲穿戴上时的声音**|
|setToughness()           |Float            |设置**盔甲韧性**|
|setKnockbackResistance() |Float            |设置**击退抗性**|
|setRepairIngredient()    |物品或物品标签     |设置**修复所用物品**，用于在铁砧中修复盔甲|

> **注意**：工具材料是以字符串形式保存，而非命名空间。在调用时也是如此

### 材质部分

假设一套使用了`normal`盔甲材料的盔甲分别为`kubejs:normal_helmet`、`kubejs:normal_chestplate`、`kubejs:normal_leggings`、`kubejs:normal_boots`

则这些盔甲的盔甲模型材质应位于`assets/kubejs/textures/models/`下，其中分别有两个模型材质文件`normal_layer_1.png`与`normal_layer_2.png`。

`xxx_layer_1.png`包括了盔甲头部、上身和足部的模型材质，而`xxx_layer_2.png`包括了盔甲腿部的模型材质。