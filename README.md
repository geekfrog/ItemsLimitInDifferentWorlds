# ItemsLimitInDifferentWorlds
### 限制物品在不同世界

##### [插件使用说明](https://github.com/geekfrog/ItemsLimitInDifferentWorlds/wiki/)
##### 构建地址:[http://ci.frog.gg/jenkins/job/ItemsLimitInDifferentWorlds/](http://ci.frog.gg/jenkins/job/ItemsLimitInDifferentWorlds/)
##### 前置插件Vault下载地址:[https://dev.bukkit.org/projects/vault/](https://dev.bukkit.org/projects/vault/)

使用时必须使用Vault前置插件.

#### 功能描述：

A世界的物品或方块只能在A世界使用，无法在B世界进行使用、放置等操作。

支持定义哪个物品在哪几个世界能进行什么操作(放置、丢弃、合成等).

#### 应用案例：

空岛服开放了地狱世界，但是玩家直接去地狱世界挖方块在空岛世界建筑，这样游戏进度就会被加快。
用了这个插件后地狱世界挖出的方块将只能在地狱世界放置。
# 空岛世界买的地狱岩却可以在空岛放置但不能在地狱世界放置。
可配置那些方块在哪个世界无法使用。

#### 插件原理：

当玩家获取(包括但不限于从地上捡起、容器拿出等)物品后，判断是否为需要处理的物品并且是否设置了“物品生产世界”。
如果是需要处理的物品并且没有设置“物品生产世界”，就设置“物品生产世界”。
当玩家使用(包括但不限于手持、右键、丢弃、放到容器、附魔、合成等)时进行判断，是否是合法操作。
如果非法就终止操作，并进行提示，否则正常操作。

#### 配置大致如下：
```
#白名单模式 
#不开启则为黑名单模式，即全服所有物品正常使用，只监控下列物品。
#否则所有物品只能在本世界使用，下列物品进行特殊处理。
whitelist: false
items: 
  i1:
    type: STONE
    meta:
      meta-type: STONE
      display-name: 石头
      lore:
      - 以上信息是通过插件命令的生成的，不是手填的。
    limit:
      l1:
        action:
		- all
		worlds:
		- world
		- world2
	  l2:
		action:
		- place #放置
		- use #使用 如：吃等右键操作
		- hand #放在手里 防止作为武器使用
		- inventory #放在GUI容器、合成台、铁站、各种箱子等
		- drop #丢弃
	    worlds:
		- world3
		- world4

```

#### 插件计划：

加粗项已完成

- 项目初始化
- 配置文件相关
- 物品限制功能
- GUI化部分功能

#### 使用统计：
[https://bstats.org/plugin/bukkit/ItemsLimitInDifferentWorlds](https://bstats.org/plugin/bukkit/ItemsLimitInDifferentWorlds)
