## 认识kjs的文件夹
kjs在第一次运行后，会在版本文件夹下创建一个自己的魔改文件夹 **kubejs** ，在该文件夹里有**assets** **client_scripts** **config** **data** **server_scripts** **startup_scripts** 这些文件夹，下面会介绍这些文件夹所存放的类型

`assets` 是存放材质包的，比如lang文件或者物品贴图等都在该文件夹内进行更改

`data` 是写数据包的，是的kjs支持直接写全局数据包，让创建世界时默认加载该数据

`config` 是存放配置文件的，可以自己定义一些配置文件丢里面

`startup_scripts` 在游戏加载时运行的代码，比如添加物品、方块流体等 在游戏内可以使用`/kjs reload startup_scripts`进行重载

`server_scripts` 服务端运行的代码，在大部分逻辑处理代码都是由服务端运行，所以大部分代码写在该文件夹内就可以，使用reload时重载

`client_scripts` 客户端代码，除了逻辑处理代码可以写在客户端里，比如游戏内的物品渲染等，使用F3+T时重载