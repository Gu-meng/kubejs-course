# 机械动力：筛子
本章将会介绍如何使用kubejs来修改机械动力的筛子

这里交代本章教程所用到的各个模组和forge的版本，如果版本不同导致报错，可能是作者进行代码更改:
1. forge-47.3.7
2. JEI-15.3.0.4
3. rhino-2001.2.2-build.18
4. architectury-9.2.14
5. kubejs-2001.6.5-build.7
6. probejs-6.0.1
7. create-0.5.1f
8. createsifter-1.20.1-1.8.1.e-22

## 注册筛网
机械动力：筛子提供了筛网的注册，我们只需要注册物品，并赋予材质(大概率可能是模型,孤梦这边没看官方怎么整的)和汉化就可以了

```js
StartupEvents.registry("item",event=>{
    event.create("meng:mesh","createsifter:mesh")
    event.create("meng:advanced_mesh","createsifter:advanced_mesh")
})
```

## 配方的修改
机械动力：筛子 提供了一个修改筛子的配方
```js
ServerEvents.recipes(event=>{
        const createsifter = event.recipes.createsifter;
        createsifter.sifting(output[],input[],processingTime,isWater,minimumSpeed);
});
```
`output` : 输出物品 -- ***必须填写***

`input` : 输入物品 -- ***必须填写***

`processingTime` :  处理时间(tick为单位) -- **非必填** -- 默认为 `100`

`isWater` ： 是否浸水处理 -- **非必填** -- 默认为`false`

`minimumSpeed` ： 最小处理速度 -- **非必填** -- 默认为`1.0`

问题1:

筛网填写在哪里

答:

我们可以看到output是一个数组，这里面一个参数为输入物品第二个参数则为筛网的物品id了

问题2:

两种筛子但是只有一个配方，我该怎么区分两种筛子配方

答:

在官方给的筛子中可以看到有高级黄铜筛网，如果将筛网填写为高级黄铜筛网或者你自己注册的物品类型为`advanced_mesh`，就会识别到黄铜筛子当中，其他的都会被识别到普通筛子当中