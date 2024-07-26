# tag和item
Item一般精准的表达一个物品，比如**红色的床'minecraft:red_bed'**，**绿色的床'minecraft:green_bed'**这种精准的物品

tag则是一个大范围的表达，一般表示一个集，比如**红色的床'minecraft:red_bed'**，**绿色的床'minecraft:green_bed'**，**橙色的床'minecraft:orange_bed'**这些都是床，他们的tag就是 **'#minecraft:beds'** -- (一般我们说的标签也是指的tag)

## 关于使用
### Item
Item一般直接写成 `"命名空间:物品id"` 的形式，如:`'minecraft:sand'、'minecraft:cactus'、'minecraft:raw_gold_block'`

也可以写成 `Item.of("命名空间:物品id", 个数(非必须), nbt(非必须))`

### tag
tag一般直接写成 `"#命名空间:标签id"` 的形式，如:`'#minecraft:sand'、'#minecraft:piglin_loved'、'#minecraft:beds'`

当你需要对标签进行更详细的设置时，就需要使用到 `Ingredient.of("#命名空间:标签id", 个数(非必须))`

### Fluid
Fluid流体使用`Fluid.of("命名空间:流体id", 数量(非必须))`来进行调用

## 将物品方块流体添加进tag


## 注意事项
1. 并不是所有物品都有tag标签
2. 当你在游戏内从手上获取到的物品tag可能会有多个，得适当做选择