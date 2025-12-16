# 匠魂3获取所有强化属性

本章主要涉及内容：JSONIO、LoadClass，本章所有代码部分都在`server_scripts`里

## 完整代码
获取部分
```js
let file = new FileHelper("tconstructModifiers.json");
const $ModifierManager = Java.loadClass("slimeknights.tconstruct.library.modifiers.ModifierManager")
let list = []
$ModifierManager.INSTANCE.getAllLocations().forEach(value => {
    list.push({
        key:value.toString(),
        name:Text.translatable(`modifier.${value.getNamespace()}.${value.getPath()}`).getString(),
        flavor:Text.translatable(`modifier.${value.getNamespace()}.${value.getPath()}.flavor`).getString(),
        description:Text.translatable(`modifier.${value.getNamespace()}.${value.getPath()}.description`).getString()
    })
})
file.updateJson(list);
```
文件处理部分
```js
// priority: 10

function FileHelper(fileName,path){
    if (path == undefined) path = "./meng";
    path = path + "/" + fileName;
    this.json = JsonIO.readJson(path);

    this.getJson = () =>{
        try {
            return JSON.parse(this.json.asJsonObject.get("data"))
        }catch(err){
            console.warn(err);
            return null
        }
    }

    this.updateJson = (newJson) =>{
        JsonIO.write(path,{data:newJson});
    }
}
```

## 注意事项

1. 该项目只是作为示例，很多地方并不是最优解，可自行进行解决
2. 代码可能存在的问题：如果路径存在未创建的文件夹则会出现无法创建文件的情况，所以提前创建好指定文件夹
3. 项目中FileHelper可以被替代，孤梦懒得修改所以直接全部复制上来了，但是使用时，一定要将`// priority: 10`加上，让其提前加载
4. 如果对该项目代码部分不满可以将修改好的代码上传至[gitee项目仓库](https://gitee.com/gumengmengs/kubejs-course)

