# 方块注册
kubejs可以在startup_scripts文件夹内创建去创建方块，注意所有的添加自定义的操作都是无法热加载的，写完之后需要重启游戏后才会加载进游戏内
## 基础写法
在kubejs当中注册方块是一件很容易的事情,它只需要下面这一行代码就可以注册好方块
```js
StartupEvents.registry("block", event => {
    //event.create(方块id, 方块类型)
    event.create("meng:my_block", "basic")
})
```
上面的代码中我们选择的是方块注册，将方块id设置为`"meng:my_block"`，这里前面的`meng`是[命名空间](/ti-wai-hua/ming-ming-kong-jian.md),主要关系到我们之后去添加[材质贴图](/cai-zhi/tie-tu.md)和[本地化（lang文件）](/cai-zhi/lang.md)的路径

## 方块类型
我们的方块类型设置的为`basic`也就是默认的、基本的方块类型，在kubejs中已经给我们提供了不少的方块类型，如下
|  类型  |    描述   |   示例  |
| :-----: | :--------: | :------: |
|  basic |  基础方块 |  待更新 |
| carpet |    地毯   | 待更新  |
|  crop  |   农作物  |  待更新 |
|  fence |    栅栏   |  待更新 |
| fence_gate | 栅栏门 |  待更新 |
| pressure_plate | 压力板 |  待更新 |
|  button |  按钮  |  待更新 |
|  slab  |   台阶  |  待更新 |
|  stairs |  楼梯  |  待更新 |
|   wall  |  墙   |  待更新 |
| cardinal | 待研究 |  待更新 |
| detector | 检测方块? |  待更新 |
| falling |  下落方块? |  待更新 |

在kubejs中，你并不用为方块单独去注册物品，kubejs已经帮你把方块物品注册好了，所以你可以直接获取到方块的物品，且物品id和方块id是一样的，在准备材质时，只需要准备方块的材质就可以了，无需单独为方块物品准备材质

## 通用方法参数
待更新--


# 最后更新时间 2024年7月12日-04点12分