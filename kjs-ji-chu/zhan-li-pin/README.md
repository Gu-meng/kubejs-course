# 战利品
在这章中会采用原生的KubeJs实现战利品的修改和添加，并不会使用LootJs进行修改战利品，LootJs的修改在模组篇章中

在原生kubeJs中，作者一共给我们提供了以下6种战利品修改或添加的方式

|   战利品事件调用                |     用途   |   添加  |  覆盖 |  用法 |
| :----------------------------: | :-------: | :----------: | :--------: | :-----------------------------------: |
| ServerEvents.genericLootTables | 全局战利品 | modify       | addGeneric | [全局战利品](quan-ju-zhan-li-pin.md)   |
| ServerEvents.blockLootTables   | 方块战利品 | modifyBlock  | addBlock   | [方块战利品](fang-kuai-diao-luo.md)    |
| ServerEvents.entityLootTables  | 生物战利品 | modifyEntity | addEntity  | [生物战利品](sheng-wu-diao-luo.md)     |
| ServerEvents.giftLootTables    | 礼物战利品 | modify       | addGift    | [礼物战利品](li-wu-zhan-li-pin.md)     |
| ServerEvents.fishingLootTables | 钓鱼战利品 | modify       | addFishing | [钓鱼战利品](diao-yu-zhan-li-pin.md)   |
| ServerEvents.chestLootTables   | 宝箱战利品 | modify       | addChest   | [宝箱战利品](bao-xiang-zhan-li-pin.md) |

