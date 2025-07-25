# 全局静态类
kubejs提供了以下的全局静态类和对应的方法

## Utils
| 方法 | 方法参数 | 方法作用 | 方法返回参数 | 备注 | 
| :--: | :--: | :--: | :--: | :--: |
| toTitleCase(string) | -> | 将传入字符串第一个文本转化为大写 | 处理后的字符串 string | 除了"a", "an", "the", "of", "on", "in", "and", "or", "but" 和 "for" |
| getStat(ResourceLocation) | ~ | ~ | Stat<ResourceLocation\> | 后续补充 |
| snakeCaseToTitleCase(string) | -> | 将蛇形命名转换为标题大小写 | 处理后的字符串 string |  如a_bc_def 转为 A Bc Def |
| newCountingMap() | - | 获取一个新的CountingMap | CountingMap | - |
| toTitleCase(string,bool) | -> | 设置会true后将上面除了的内容也会进行大写 | 理后的字符串 string | - |
| parseDouble(any,number) | -> | 将第一个参数转化为Double类型，如果失败了，则返回第二个数 | number | - |
| getRandom() | - | 获取Random类 | Random | - |
| newList() | - | 获取一个列表 | List<T\> | - |
| rollChestLoot(ResourceLocation) | 战利品表id | 获取指定战利品表里的战利品数组 | List<ItemStack\> | - |
| newRandom(number) | -> | 用一个数字当作种子生成一个Random类 | Random | - |
| getRegistryIds(ResourceLocation) | -> | 获取指定注册表里的的所有id | List<ResourceLocation\> | - |
| emptyList() | - | 获取一个不可变的空列表? | List<T\> | - |
| getSystemTime() | - | 获取当前系统时间，以毫秒为单位 | number | - |
| supplyAsync(Supplier<any\>) | ~ | ~ | CompletableFuture<any\> | 后续补充 |
| id(string,string) | -> | 将字符串转为ResourceLocation | ResourceLocation | - |
| lazy(Supplier<T\>) | ~ | ~ | Lazy<T\> | ? |
| isWrapped(any) | -> | 判断传入对象是否为WrappedJS | boolean | - |
| snakeCaseToCamelCase(string) | -> | 将蛇形命名转化为驼峰命名 | 处理后的字符串 string | 如 a_bc_def 转为 aBcDef |
| findCreativeTab(ResourceLocation) | id | 获取该id的所在创造物品栏 | CreativeModeTab | - |
| emptyMap() | - | 获取一个空的不可变的map? | Map<K, V\> | - |
| expiringLazy(Supplier<T\>,number) | ~ | ~ | Lazy<T\> | 后续补充 | 
| getSound(ResourceLocation) | id | 从id中获取SoundEvent | SoundEvent | - |
| randomOf(Random,Collection<any\>) | ~ | 使用传入的参数从列表中获取随机对象? | any | ? |
| newMap() | - | 获取一个map | Map<any, any\> | - |
| getRegistry(ResourceLocation) | id | 通过id获取对应的注册信息 | RegistryInfo<any\> | - |
| particleOptions(any) | ~ | ~ | ParticleOptions | - |
| copy(any) | -> | 复制一份传入的对象，如果不可以则返回本身 | any | - |
| regex(string,number) | string pattern / number flags | ~ | Pattern | - |
| id(string) | -> | 将字符串直接包装成ResourceLocation | ResourceLocation | - |
| regex(any) | -> | ~ | Pattern | - |
| runAsync(Runnable) | -> | ~ | CompletableFuture<void\> | - |
| parseBlockState(any) | -> | 从输入内容中解析方块状态可能会抛出无效输入 | BlockState | - |
| queueIO(Runnable) | -> | 立即在try-catch块中运行传递的可运行函数，并在它抛出异常时记录异常? | void | - |
| parseInt(any,number) | -> | 将第一个参数转化为整数，如果失败则返回第二个参数 | number | - |
| getServer() | - | 获取游戏服务端，如果是在没有服务器的地方调用则为null(startup和client) | MinecraftServer | - |
| rollChestLoot(ResourceLocation,Entity) | 战利品表id，触发实体 | 用指定实体生成一个战利品表物品列表 | List\<ItemStack\> | 不一定是箱子 |

## JsonIO
| 方法 | 方法参数 | 方法作用 | 方法返回参数 | 备注 | 
| :--: | :--: | :--: | :--: | :--: |
| readJson(path) | 路径字符串 | 读取指定路径的文件 | JsonElement | 文件必须为json |
| toPrettyString(JsonElement) | -> | 将json转化为字符串 | string | - |
| getJsonHashString(JsonElement) | -> | 获取json的hash值 | string | - |
| toObject(JsonElement) | -> | 将json转化为对象??? | any | 后续测试 |
| primitiveOf(any) | ? | ? | JsonPrimitive | 后续测试 |
| readString(path) | 路径 | 读取指定路径的文件 | string | 读取为string格式 |
| writeJsonHash(DataOutputStream,JsonElement) | ? | ~ | void | 后续测试 |
| parseRaw(string) | ? | ? | JsonElement | 后续测试 |
| write(path,JsonObject) | -> | 将json对象写入到指定路径的文件里 | void | 一定要是json对象，不能是数组 |
| read(path) | -> | 读取指定路径的文件 | Map<any,any\> | 建议使用readJson |
| toArray(JsonElement) | -> | 将JsonElement转为JsonArray | JsonArray | - |
| parse(string) | -> | ? | any | 后续测试 |
| toPrimitive(JsonElement) | -> | ? | any | 后续测试 |
| copy(JsonElement) | -> | 复制一份JsonElement | JsonElement | - |
| toString(JsonElement) | -> | 将json转为字符串 | string | - |
| getJsonHashBytes(JsonElement) | -> | 将json转为hashByte | number[] | - |
| of(any) | ? | ? | JsonElement | - |

## BlockPos
| 方法 | 方法参数 | 方法作用 | 方法返回参数 | 备注 | 
| :--: | :--: | :--: | :--: | :--: |
| asLong(number,number,number) | 依次顺序为X,Y,Z坐标 | 通过坐标获取对应的数值 | number | - |
| betweenClosed(n1,n2,n3,n4,n5,n6) | 依次顺序为x1,y1,z1,x2,y2,z2 | 通过两个坐标获取该区域内的所有坐标 | Iterable<BlockPos\> | - |
| betweenClosedStream(BlockPos,BlockPos) | - | 同上 | Stream<BlockPos\> | - |
| breadthFirstTraversal(BlockPos,number,BiConsumer<BlockPos, Consumer<BlockPos\>\>,Predicate<BlockPos\>) | 坐标，最大距离，-，回调用于处理每个遍历到的方块位置 | 按广度优先的顺序遍历周围的方块 | number | - |
| containing(Position) | -> | 根据Position返回BlockPos | BlockPos | - |
| findClosestMatch(BlockPos,number,number,Predicate<BlockPos\>) | ~ | ~ | Optional<BlockPos\> | - |
| getFlatIndex(number) | ~ | ~ | number | - |
| getX(number) | -> | 获取对应值 | number | - |
| getY(number) | -> | 获取对应值 | number | - |
| getZ(number) | -> | 获取对应值 | number | - |
| of(number) | 坐标数值（asLong获取的这种数字数值 | - | BlockPos | - |
| offset(number,number,number) | ~ | ~ | number | - |
| offset(number,Direction) | ~ | ~ | number | - |
| offsetCodec(number) | ~ | ~ | Codec<Vec3i\> | - |
| randomBetweenClosed(RandomSource,n1,n2,n3,n4,n5,n6) | -> | 在一个区域内随机生成坐标 | Iterable<BlockPos\> | - |
| randomInCube(RandomSource,number,BlockPos,number) | ? | 通过一个坐标中心点向外延申到指定距离的方块区域内生成坐标? | Iterable<BlockPos\> | - |
| spiralAround(BlockPos,number,Direction,Direction) | ~ | 按照螺旋式路径遍历周围的方块位置 | Iterable<BlockPos$MutableBlockPos\> | - |
| withinManhattan(BlockPos,number,number,number) | -> | 获取在曼哈顿距离范围内的所有坐标 | Iterable<BlockPos\> | - |
| withinManhattanStream(BlockPos,number,number,number) | -> | 同上 | Stream<BlockPos\> | - |

## Block 
## Vec3d
## KMath
| 方法 | 方法参数 | 方法作用 | 方法返回参数 | 备注 | 
| :--: | :--: | :--: | :--: | :--: |
| block(n1,n2,n3) | -> | 根据xyz返回blockPos | BlockPos | - |
| deg(number) | ? | ? | number | - |
| v3d(n1,n2,n3) | -> | 根据xyz返回Vector3d | Vector3d | - |
| ceil(number) | ? | ? | number | - |
| map(n1,n2,n3,n4,n5) | value,min1,max1,min2,max2 | ? | number | ? |
| clamp(n1,n2.n3) | value,min,max | ? | number| ? |
| v4f(n1,n2,n3,n4) | -> | 根据xyz和w（猜测是宽度）返回Vec4f | Vec4f | - |
| rad(number) | ? | ? | number | - |
| degreesDifference(n1,n2) | current,target | ~ | number | 待测试 |
| floor(number) | -> | 向下取整 | number | - |
| poseStack() | - | -> | PoseStack | - |
| lerp(n1,n2,n3) | value,min,max | 线性插值，通过修改value的比例，返回特定的数值 | number | 举个栗子value=0.5,min=0,max=10,则会返回5 |
| clampedLerp(n1,n2,n3) | 同上 | 同上但是不会超值max的值 | number | 同上但是不会超出max |
| v3f(n1,n2,n3) | -> | 通过xyz返回Vec3f | Vec3f | - |
| rotateIfNecessary(n1,n2,n3) | current,target,max | ~ | number | - |
| m4f() | - | ` | Matrix4f | - |
| v3(n1,n2,n3) | -> | 通过xyz获取Vec3d | Vec3d | - |
| quaternion(n1,n2,n3,n4) | 根据xyz和w（猜测是宽度）返回Quaternionf | Quaternionf | - |
| wrapDegrees(number) | -> | 处理角度 | number | - |
| m3f() | - | - |Matrix3f | - |
| approachDegrees(n1,n2,n3) | current,target,speed | ~ | number | - |
| approach(n1,n2,n3) | current,target,speed | ~ | number | - |
| isPowerOfTwo(number) | -> | 判断是否为 2 的幂次方 | bool | - |
| PI | - | - | 3.141592653589793 | - |
| RADIANS_TO_DEGREES | - | - | 57.29577951308232 | - |
| DEGREES_TO_RADIANS | - | - | 0.017453292519943295 | - |
| E | - | - | 2.718281828459045 | - |
 
## RotationAxis
## ResourceLocation
## Items
## SoundType
| 类型常量 | 对应方块/物品类型 |
| :--: | :--: |
| EMPTY | 空类型（无声音） |
| SAND | 沙子 |
| DECORATED_POT | 装饰性陶罐 |
| TUFF | 凝灰岩 |
| GRAVEL |  gravel |
| SHROOMLIGHT | 菌光体 |
| MOSS | 苔藓 |
| SOUL_SOIL | 灵魂土 |
| WEEPING_VINES | 垂泪藤 |
| ANCIENT_DEBRIS | 远古残骸 |
| SCULK_SENSOR | 幽匿感测体 |
| POINTED_DRIPSTONE | 滴水石锥 |
| ROOTED_DIRT | 植根泥土 |
| FROGSPAWN | 青蛙卵 |
| NETHER_ORE | 下界矿石 |
| COPPER | 铜 |
| LANTERN | 灯笼 |
| BONE_BLOCK | 骨块 |
| FROGLIGHT | 蛙明灯 |
| SNOW | 雪 |
| SCULK_VEIN | 幽匿脉络 |
| CHERRY_WOOD | 樱花木 |
| POLISHED_DEEPSLATE | 抛光深板岩 |
| NYLIUM | 菌岩 |
| DEEPSLATE | 深板岩 |
| SPORE_BLOSSOM | 孢子花 |
| BASALT | 玄武岩 |
| CHERRY_WOOD_HANGING_SIGN | 樱花木悬挂牌 |
| SMALL_AMETHYST_BUD | 小型紫水晶芽 |
| CANDLE | 蜡烛 |
| FLOWERING_AZALEA | 开花杜鹃 |
| ANVIL | 铁砧 |
| SCAFFOLDING | 脚手架 |
| DEEPSLATE_BRICKS | 深板岩砖 |
| CORAL_BLOCK | 珊瑚块 |
| BAMBOO_SAPLING | 竹子幼苗 |
| LILY_PAD | 睡莲 |
| MOSS_CARPET | 苔藓地毯 |
| LADDER | 梯子 |
| LARGE_AMETHYST_BUD | 大型紫水晶芽 |
| GLOW_LICHEN | 发光地衣 |
| CROP | 农作物 |
| PINK_PETALS | 粉色花瓣 |
| AZALEA_LEAVES | 杜鹃树叶 |
| POWDER_SNOW | 细雪 |
| METAL | 金属 |
| HONEY_BLOCK | 蜂蜜块 |
| NETHER_BRICKS | 下界砖块 |
| SUSPICIOUS_SAND | 可疑的沙子 |
| GILDED_BLACKSTONE | 镶金黑石 |
| HARD_CROP | 坚硬农作物 |
| SCULK_CATALYST | 幽匿催化体 |
| DEEPSLATE_TILES | 深板岩瓦 |
| PACKED_MUD | 压实泥土 |
| SCULK | 幽匿块 |
| VINE | 藤蔓 |
| BAMBOO | 竹子 |
| GLASS | 玻璃 |
| DRIPSTONE_BLOCK | 滴水石块 |
| CHERRY_SAPLING | 樱花树苗 |
| CALCITE | 方解石 |
| MUD_BRICKS | 泥砖 |
| STEM | 茎（如蘑菇茎） |
| BAMBOO_WOOD | 竹材 |
| SOUL_SAND | 灵魂沙 |
| MUD | 泥土 |
| BIG_DRIPLEAF | 大型滴水叶 |
| BAMBOO_WOOD_HANGING_SIGN | 竹材悬挂牌 |
| TWISTING_VINES | 扭曲藤 |
| NETHERRACK | 下界岩 |
| AMETHYST_CLUSTER | 紫水晶簇 |
| SLIME_BLOCK | 史莱姆块 |
| SCULK_SHRIEKER | 幽匿尖啸体 |
| CHAIN | 链条 |
| WOOD | 木材 |
| AZALEA | 杜鹃花 |
| MANGROVE_ROOTS | 红树根 |
| CHISELED_BOOKSHELF | 雕花书架 |
| NETHER_GOLD_ORE | 下界金矿 |
| CHERRY_LEAVES | 樱花树叶 |
| AMETHYST | 紫水晶 |
| DECORATED_POT_CRACKED | 破损的装饰性陶罐 |
| CAVE_VINES | 洞穴藤 |
| SUSPICIOUS_GRAVEL | 可疑的 gravel |
| LODESTONE | 磁石 |
| FUNGUS | 真菌 |
| SMALL_DRIPLEAF | 小型滴水叶 |
| HANGING_ROOTS | 悬挂的根 |
| SWEET_BERRY_BUSH | 甜浆果丛 |
| NETHER_WOOD | 下界木材 |
| NETHER_WART | 下界 wart |
| STONE | 石头 |
| NETHER_WOOD_HANGING_SIGN | 下界木材悬挂牌 |
| HANGING_SIGN | 悬挂牌 |
| WET_GRASS | 湿润的草 |
| NETHERITE_BLOCK |  Netherite块 |
| MEDIUM_AMETHYST_BUD | 中型紫水晶芽 |
| MUDDY_MANGROVE_ROOTS | 泥泞的红树根 |
| WOOL | 羊毛 |
| ROOTS | 根部 |
| WART_BLOCK | Wart块 |
| NETHER_SPROUTS | 下界苗 |

## Stats
使用方法简单示例1：
```Utils.server.getPlayer("gu__meng").getStats().get(Stats.BLOCK_MINED.get(Block.getBlock("stone")))```

使用方法简单示例2：
```Utils.server.getPlayer("gu__meng").getStats().get(Stats.SWIM_ONE_CM)```

| 状态常量 | 描述 | 备注 |
| :--: | :--: | :--: |
| SWIM_ONE_CM | 游泳的总距离 | - |
| FLY_ONE_CM | 飞行的总距离 | - |
| WALK_ONE_CM | 步行的总距离 | - |
| CLIMB_ONE_CM | 攀爬的总距离 | - | 
| FALL_ONE_CM | 下落的总距离 | - |
| BOAT_ONE_CM | 乘船的总距离 | - |
| STRIDER_ONE_CM | 骑炽足兽的总距离 | - |
| HORSE_ONE_CM | 骑马的总距离 | - |
| PIG_ONE_CM | 骑猪的总距离 | - |
| MINECART_ONE_CM | 乘坐矿车的总距离 | - |
| WALK_ON_WATER_ONE_CM | 在水上行走的总距离 | - |
| WALK_UNDER_WATER_ONE_CM | 在水下行走的总距离 | - |
| SPRINT_ONE_CM | 奔跑的总距离 | - |
| CROUCH_ONE_CM | 蹲下移动的总距离 | - |
| AVIATE_ONE_CM | 滑翔（如用鞘翅）的总距离 | - |
| PLAYER_KILLS | 杀死玩家的数量 | - |
| MOB_KILLS | 杀死生物的数量 | - |
| DEATHS | 死亡次数 | - |
| DAMAGE_DEALT | 造成的总伤害 | - |
| DAMAGE_DEALT_RESISTED | 对有抗性的目标造成的伤害 | - |
| DAMAGE_DEALT_ABSORBED | 被目标吸收的伤害 | - |
| DAMAGE_TAKEN | 受到的总伤害 | - |
| DAMAGE_RESISTED | 抵抗的伤害（如通过盔甲） | - |
| DAMAGE_ABSORBED | 吸收的伤害（如通过吸收效果） | - |
| DAMAGE_BLOCKED_BY_SHIELD | 用盾牌格挡的伤害 | - |
| ENTITY_KILLED | 杀死的实体类型 | 需要get(实体类型) |
| ENTITY_KILLED_BY | 被哪些实体杀死 | 需要get(实体类型) |
| ITEM_PICKED_UP | 捡起的物品 | 需要get(物品) |
| ITEM_DROPPED | 丢弃的物品 | 需要get(物品) |
| ITEM_USED | 使用的物品 | 需要get(物品) |
| ITEM_BROKEN | 损坏的物品 | 需要get(物品) |
| ITEM_CRAFTED | 合成的物品 | 需要get(物品) |
| BLOCK_MINED | 挖掘的方块 | 需要get(方块) |
| POT_FLOWER | 种植的花数量 | - |
| EAT_CAKE_SLICE | 吃掉的蛋糕片数量 | - |
| OPEN_CHEST | 打开箱子的次数 | - |
| OPEN_ENDERCHEST | 打开末影箱的次数 | - |
| OPEN_SHULKER_BOX | 打开潜影盒的次数 | - |
| OPEN_BARREL | 打开木桶的次数 | - |
| TRIGGER_TRAPPED_CHEST | 触发陷阱箱的次数 | - |
| INSPECT_DISPENSER | 查看发射器的次数 | - |
| INSPECT_DROPPER | 查看投掷器的次数 | - |
| INSPECT_HOPPER | 查看漏斗的次数 | - |
| INTERACT_WITH_CRAFTING_TABLE | 使用工作台的次数 | - |
| INTERACT_WITH_FURNACE | 使用熔炉的次数 | - |
| INTERACT_WITH_BLAST_FURNACE | 使用高炉的次数 | - |
| INTERACT_WITH_SMOKER | 使用烟熏炉的次数 | - |
| INTERACT_WITH_BREWINGSTAND | 使用酿造台的次数 | - |
| INTERACT_WITH_ANVIL | 使用铁砧的次数 | - |
| INTERACT_WITH_GRINDSTONE | 使用砂轮的次数 | - |
| INTERACT_WITH_STONECUTTER | 使用切石机的次数 | - |
| INTERACT_WITH_LOOM | 使用织布机的次数 | - |
| INTERACT_WITH_CARTOGRAPHY_TABLE | 使用制图台的次数 | - |
| INTERACT_WITH_SMITHING_TABLE | 使用锻造台的次数 | - |
| INTERACT_WITH_LECTERN | 使用讲台的次数 | - |
| INTERACT_WITH_BEACON | 使用信标的次数 | - |
| ENCHANT_ITEM | 附魔物品的次数 | - |
| TOTAL_WORLD_TIME | 游戏世界总时间 | - |
| PLAY_TIME | 玩家游戏时长 | - |
| TIME_SINCE_REST | 上次睡觉至今的时间 | - |
| TIME_SINCE_DEATH | 上次死亡至今的时间 | - |
| LEAVE_GAME | 退出游戏的次数 | - |
| SLEEP_IN_BED | 在床上睡觉的次数 | - |
| JUMP | 跳跃次数 | - |
| CROUCH_TIME | 蹲下的总时间 | - |
| BELL_RING | 敲响铃铛的次数 | - |
| INTERACT_WITH_CAMPFIRE | 与营火交互的次数 | - |
| FISH_CAUGHT | 钓到鱼的数量 | - |
| USE_CAULDRON | 使用炼药锅的次数 | - |
| FILL_CAULDRON | 装满炼药锅的次数 | - |
| PLAY_NOTEBLOCK | 播放音符盒的次数 | - |
| TUNE_NOTEBLOCK | 调谐音符盒的次数 | - |
| PLAY_RECORD | 播放唱片的次数 | - |
| TARGET_HIT | 击中目标的次数 | - |
| CLEAN_SHULKER_BOX | 清理潜影盒的次数 | - |
| CLEAN_ARMOR | 清理盔甲的次数 | - |
| CLEAN_BANNER | 清理旗帜的次数 | - |
| DROP | 丢弃物品的总次数 | - |

## Duration
## OutputItem
## Fluid
## InputItem
## DamageSource
## Platform
## Vec3f
## Vec4f
## Notification
## Quaternionf
## JavaMath
## BlockProperties
## Vec3i
## Matrix3f
## Matrix4f
## Blocks
## Component