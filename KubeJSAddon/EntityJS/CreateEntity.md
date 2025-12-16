# 实体注册
EntityJS总共提供了以下几种注册类型
```js
StartupEvents.registry('entity_type', event => {
    event.create('bat', 'entityjs:living') // 生物
    event.create('sasuke', 'entityjs:mob') // 普通生物
    event.create('wyrm', 'entityjs:animal') // 动物
    event.create('dragon', 'entityjs:tamable') // 可驯服的生物
    event.create('arrow', "entityjs:arrow") // 箭矢实体
    event.create('projectile', "entityjs:projectile") // 投掷物吧
    event.create('serpent', "entityjs:watercreature") // 水生 生物
    event.create('dummy', "entityjs:nonliving") // 无生命的实体
    event.create('projectile', "entityjs:geckolib_projectile") // Projectile builder with Geckolib modelling
})
```

## 常用方法
### 在首次加载设置的参数
|             方法名              |                    参数作用                    |                方法作用                 |                  备注                  |
| :-----------------------------: | :--------------------------------------------: | :-------------------------------------: | :------: | :------------------------------------: |
|       immuneTo(string[])        |                   方块id数组                   |         设置实体免疫的方块[^1]          |                      -                    |
|   canSpawnFarFromPlayer(bool)   |                       ->                       |   设置实体是否可以在远离玩家位置生成    |                      -                    |
|   clientTrackingRange(number)   |                       ->                       | 设置实体的客户端跟踪范围(渲染范围?)[^2] |                   默认值5                 |
|       mobCategory(string)       |                    设置种类                    |             设置实体的种类              |     [可用种类](#实体种类) / 默认值为misc  |
|      setRenderType(string)      |                  设置呈现类型                  |          设置实体呈现类型[^3]           |          [可用呈现类型](#呈现类型)        |
|     sized(number1,number2)      |             num1 宽度 / num2 长度              |        设置实体类型的碰撞箱[^4]         |              长度和宽度默认为1            |
|   modelSize(number1,number2)    | num1 长度(scaleHeight) / num2 宽度(scaleWidth) |             设置模型的比例              |                      -                    |
|     updateInterval(number)      |                       ->                       |           设置实体的更新间隔            |                默认为 1 tick              |
|     defaultDeathPose(bool)      |                       ->                       |       设置实体死亡时是否倒下[^5]        |    翻译是：死亡是否转向一边 / 默认为 true |
| repositionEntityAfterLoad(bool) |                       ->                       |     设置加载后是否重新定位实体[^6]      |                      -                    |
| isAlwaysExperienceDropper(bool) | -> | 设置实体是否始终被视为经验掉落[^7] |  - |
| setDeathSound(string) | 死亡音效资源路径 | 设置实体死亡时播放的声音 |  类似于:`"minecraft:entity.generic.death"` |
| isPushable(bool) | -> | 设置实体是否可以被推动[^8] |  - |
| canBreatheUnderwater(bool) | -> | 设置实体是否可以在水里呼吸 |  - |
| eatingSound(string) | 资源路径 | 设置实体吃东西的声音 |  类似于:`"minecraft:entity.zombie.ambient"` |
| fallSounds(string1,string2) | string1 小的下落音效资源路径 / string2 大的下落音效资源路径 | 设置下落音效资源路径 |  原版的:`minecraft:entity.generic.small_fall` `minecraft:entity.generic.large_fall`|
| fireImmune(bool) | -> | 设置实体是否免疫火焰 |  - |
| mainArm(string) | "left"/"right" | 设置实体的主手为左或右 |  - |
| mobType(string) | 生物类型 | 设置生物的类型 |  [生物类型](#生物类型) |
| saves(bool) | -> | 设置实体是否应该序列化其数据[^9] |  默认为true |
| setSoundVolume(number) | -> | 设置实体的音量[^10] |  - |
| setSummonable(bool) | -> | 设置实体是否可以召唤[^11] |  - |
| setSwimSound(string) | 资源路径 | 设置实体的游泳声音 |  类似于：`"minecraft:entity.generic.swim"`|
| setSwimSplashSound(string) | 资源路径 | 设置实体游泳产生的水花声音?[^12] |  类似于：`"minecraft:entity.generic.splash"` |
| setWaterSlowDown(number) | -> | 设置实体在水中的减速因子 |  默认为0.8，（此为猜测：相比于陆地上的减速比，默认的0.8也就是陆地上的80%速度） |
| mountJumpingEnabled(bool) | -> | 设置实体是否可以在玩家骑乘时跳跃 |  默认为false，(实验性内容) |
| eggItem(Consumer\<item\>) | ~ | 设置刷怪蛋物品 |  **后续测试补充** |
| newGeoLayer(Consumer\<GeoLayerJSBuilder\>) | ~ | 设置额外渲染层 |  **等示例**，新的渲染比如爆炸的苦力怕和凋零 |
| addAnimationController(string,number,IAnimationPredicateJS) | 动画控制器名，动画播放的tick，动画谓词，定义播放条件 | 用指定的参数向实体添加动画控制器。 |  **等示例** |
| onInteract(Consumer\<MobInteractContext\>) | ~ | 实体交互事件 |  **后续补充示例** |
| addPartEntity(string,num1,num2,Consumer\<PartBuilder\>) | 部位名，宽度，长度，PartBuilder的回调 | 给生物增加额外的碰撞箱 |  类似于末影龙的多个命中碰撞箱，**等待示例** |
| aiStep(Consumer\<LivingEntity\>) | ~ | 设置生物的AI行为 |  **等示例** |
| render(Consumer\<RenderContext\>) | ~ | 定义实体的渲染[^13] |  **等示例** |
| scaleModelForRender(Consumer\<ScaleModelRenderContext\>) | ~ | 在不影响核心逻辑的情况下确认模型的缩放和呈现逻辑[^14] |   **等示例** |
| jumpBoostPower(Function\<LivingEntity,any\>) | ~ | 设置实体跳跃增加的效果[^15] |  **等示例** |
| setBlockJumpFactor(Function\<LivingEntity,any\>) | ~ | 设置实体的跳跃因子[^16] |  猜测：实体在跳跃时相对于方块高度的跳跃倍数 |
| setMaxFallDistance(Function\<LivingEntity, any\>) | ~ | 设置实体的在下落多少格会收到伤害[^17] |   **等示例** |
| animationResource(Function\<T,any\>) | ~ | 设置一个function来确定动画播放资源[^18] | **等示例**，默认返回`<namespace>:animations/<path>.animation.json` |
| 


#### 实体种类
| 种类名 | 种类 |
| monster | 怪物/敌对生物 |
| creature | 普通/非敌对生物 |
| ambient | 环境生物 |
| water_creature | 水生生物 |
| misc | 其他/杂项 |

#### 呈现类型
> 这里解释的不是很好，如果有大佬知道怎么的可用issue反馈一下
| 呈现类型 | 解释 |
| solid | 用于完全实心 |
| cutout | 用于那些要么是完全透明，要么是完全不透明的 |
| translucent | 用于那些具有部分透明像素的，与 cutout 类型不同，translucent 类型的允许光线穿过，因此它们可以显示半透明效果 |

#### 生物类型
| 生物类型 | 解释 |
|  undead | 亡灵生物 |
| water | 水生生物 | 
| arthropod | 节肢生物 |
| illager | 灾厄村民 |
| undefined | 不确定的 | 

#### 一些不好解释的原话
[^1]: Sets the list of block names to which the entity is immune. 
[^2]: Sets the client tracking range for the entity.
[^3]: Sets the render type for the entity.
[^4]: Sets the hit box of the entity type.
[^5]: Boolean determining if the entity will turn sideways on death.
[^6]: Sets whether to reposition the entity after loading.
[^7]: Sets whether the entity is always considered as an experience dropper.
[^8]: Sets whether the entity is pushable.
[^9]: Determines if the entity should serialize its data.
[^10]: Sets the overall sound volume for the entity.
[^11]: Sets whether the entity is summonable.
[^12]: Sets the swim splash sound for the entity using either a string representation or a ResourceLocation object.
[^13]: Defines logic to render the entity.
[^14]: A Consumer to determing logic for model scaling and rendering without affecting core logic such as hitbox sizing.
[^15]: Sets the jump boost power for the entity.
[^16]: Sets the block jump factor for the entity.
[^17]: Sets the minimum fall distance for the entity before taking damage.
[^18]:
[^19]:
[^20]:


## 独有的方法
### Methods Exclusive to the Animal/Mob Builder (Not in LivingEntity Builder) 
|           方法名            | 参数作用 | 方法作用 | 返回类型 | 备注  |
| :-------------------------: | :------: | :------: | :------: | :---: |
| isPersistenceRequired(bool) |    ->    |    ~     |   this   |   -   |
| canJump(bool) | -> | 设置实体是否可用跳跃 | · - |
| ambientSoundInterval(number) | ~ | ~ | this | - |
| followLeashSpeed(number) | ~ | ~ | this | - | 
| setAmbientSound(string) | ~ | ~ | this | `"minecraft:entity.zombie.ambient"` |
| shouldDespawnInPeaceful(bool) | -> | ~ | this | - |
| canFireProjectileWeapon(ItemStack[]) | ~ | ~ | this | - |
| 

### Methods Exclusive to the TamableMob Builder
|           方法名            | 参数作用 | 方法作用 | 返回类型 | 备注  |
| :-------------------------: | :------: | :------: | :------: | :---: |
| tamableFood(Ingredient[]) | ~ | ~ | this | - |


### Methods Exclusive to the Animal Builder
|           方法名            | 参数作用 | 方法作用 | 返回类型 | 备注  |
| :-------------------------: | :------: | :------: | :------: | :---: |
| isFood(Ingredient[]) | ~ | ~ | this | - |
| setBreedOffspring(?) | ~ | ~ | this | 未知参数等待测试 |