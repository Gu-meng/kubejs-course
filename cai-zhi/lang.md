# 本地化lang(语言文件)
这章主要是教会大家如何添加以及修改别的Mod的本地化文件(语言文件)

* ### 文件路径
  `lang`文件主要存储于`assets/${modid}/lang`,不同的国家也有着不同的文件名称,具体请查看[**Wiki**](https://zh.minecraft.wiki/w/语言)或者文档[内部链接](/ti-wai-hua/lang-wen-jian-ming.md),而各文件都以`json`作为后缀,例如`en_us.json` `zh_cn.json` `zh_tw.json`等 

  `minecraft:sand` minecraft是modid

* ### 写法
  * `lang`主要由本地化键名和文本组成,例如
  ```json
  {
      "item.kubejs.test_item": "测试物品",
      "block.kubejs.test_block": "测试物品",
      "fluid.kubejs.test_fluid": "测试流体"
  }
  ```
  在写`lang`的时候最后一行**千万不可以加逗号**作为结尾,也**不可以不写逗号就写下一行,更不可以写注释!**
  * 而本地化键名(**key**)主要由`type.modid.id`组成
  `type`指的是类型,例如流体是`fluid`,物品是`item`,方块是`block`
  而在写代码的时候也可以自己添加一串自定义的`key`,例如给石头添加`Tooltip`,举个简单的例子
  ```js
  ItemEvents.tooltip((event) => {
	  // Text.translate()内的内容可以随便写,只要是字符串就行
  	  event.add('minecraft:stone', [Text.translate("tip.mc.stone")])
  })
  ```
  那就在`lang`写
  ```json
  {
	  "tip.mc.stone": "我是一块石头"
  }
  ```
  同时在写`lang`的时候也可以给文本添加`颜色`或者使用`转义字符`

* ### 修改&本地化
  * 在修改别的Mod的`lang`文件时需要先创建一个资源包,具体教程请看[**Wiki**](https://zh.minecraft.wiki/w/Tutorial:制作资源包)
  随后在`assets`文件夹创建一个和`Modid`相同的文件夹
    <details open>
    <summary>Modid查看(展开或收起)</summary>
    Fabric 的 Modid 在 ModFile.jar/fabric.mod.json

    Forge 或 NeoForge 的 Modid 在 ModFile.jar/META-INF/mods.toml
    </details>
  你也可以复制`ModFile.jar/assets`下的文件夹名称,然后自己创建一个文件夹,随后和开头所说的一样,`${modid}`下再创建一个`lang`文件,随后把需要修改的`lang`文件解压进去便是,如果是汉化Mod也一样,把原先的`lang`文件解压除来后改名为`zh_cn.json`

  **一切的Modid只能由`小写字母,数字和下划线(a-z,0-9和_)`组成**