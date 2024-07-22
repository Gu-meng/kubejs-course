## 添加自定义物品
kubejs可以在startup_scripts文件夹内创建去创建物品，注意所有的添加自定义的操作都是无法热加载的，写完之后需要重启游戏后才会加载进游戏内
### 基础写法
```js
StartupEvents.registry("item",event=>{
    event.create("meng:my_item","basic")
})
```
kjs创建物品是非常简单的，只需要一行就可以解决

`create`里的第一个参数为物品id,这里如果写成"xxx:xxx"，冒号前面的是你的命名空间(类似于模组id),后面的才是你的物品id,如果你只是写成"xxx"并不加冒号也是可以的，kjs为默认为你创建在kubejs下,最后呈现形式就是"kubejs:xxx"

`create`里的第二个参数为物品类型，在下面会给大家列举出来他的物品类型和描述

### 物品类型
|      类型参数      |   作用   |          描述         |                示例                 |
| ----------------- | -------- | -------------------- | ----------------------------------- |
|        basic      |  基础物品 |          无          |                    待更新            |
|      music_disc   |    唱片   | 可以在唱片机里播放的  | [添加唱片](./item-type/chang-pian.md) |
| smithing_template |  锻造模板 |          无          |                    待更新            |
|       helmet      |    头盔   |          无          |                    待更新            |
|     chestplate    |    胸甲   |          无          |                    待更新            |
|      leggings     |    护腿   |          无          |                    待更新            |
|        boots      |    鞋子   |          无          |                    待更新            |
|         axe       |    斧子   |          无          |                    待更新            |
|         hoe       |    锄头   |          无          |                    待更新            |
|       pickaxe     |    镐子   |          无          |                    待更新            |
|       shovel      |    铲子   |          无          |                    待更新            |
|        sword      |     剑    |          无          |                    待更新            |
|     shears_item   |    剪刀   |          无          |                    待更新            |

### 通用方法参数
|        方法调用      |     传入参数     |                  用处                   |
| ------------------- | --------------- | --------------------------------------- |
|   displayName(str)  |  str -> 显示名称 |      在没有配置lang文件时直接显示的名称   |
|    burnTime(num)    |  num -> 燃烧时间 |      设置燃烧时间，让物品可被当作燃料     |
| fireResistant(bool) | bool -> 是否抗火 |             设置物品的防火效果           |
|       tag(str)      |  str -> 添加tag  |        将物品添加进一个tag标签组里       |
|    maxDamage(num)   |  num -> 最大耐久 |             设置物品的最大耐久           |
|   maxStackSize(num) |  num -> 最大堆叠 |  设置物品的最大堆叠,虽然能超过64但是不建议 |
|    barColor()
|         待更新      |      待更新       |          待更新                  |