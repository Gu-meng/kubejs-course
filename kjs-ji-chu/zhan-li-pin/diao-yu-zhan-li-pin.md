# 钓鱼战利品
本章中将会举例简单的钓鱼战利品原生kubejs写法
## 基础写法
下面代码中使用`addFishing`覆盖掉原来的战利品列表(如果只想在原来的战利品表里添加使用)
```js
ServerEvents.fishingLootTables(event=>{
    event.addFishing("minecraft:fish",loot=>{
        loot.addPool(pool=>{
            pool.addItem("arrow")
            pool.addItem("glass")
            pool.addItem("bamboo_planks")
        })
    })
})
```