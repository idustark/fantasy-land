## Fantasyland Document

***
Devoloped by

邱宇航   谢天   杜佳豪  （同济大学 软件学院）  

2016.6
***

# 目录

1. 项目简介
2. 游戏背景
3. 操作说明
4. 源代码与项目资源
5. 代码实现
6. 开发历程
7. 产品测试  

## 项目简介

Fantasyland是一款3D单机即时战斗游戏，本游戏基于cocos2d-x引擎开发，支持在Windows环境下运行。玩家可选择膜法师、武士和弓箭手等职业，和其它英雄一起打击怪物、保卫家园。

游戏运行环境：Windows平台 VS2015 cocos2dx-3.10

硬件要求：硬盘（至少40MB）

## 游戏背景

在遥远的中世纪，有一片祥和宁静的土地——Fantasyland。

土地上的居民们过着安居乐业、自由和谐的生活。有一天，来自遥远的Dark Forest的怪物军团入侵了这里，烧毁村庄，掠夺财物，妄图占领这片土地。

Fantasyland的勇士们组成抗敌联盟，团结一致、同仇敌忾，希望能把怪物军团赶出自己的土地。英雄们，你们愿意拿起武器，保卫自己的家园吗？

玩家可选择膜法师(Mage)、武士(Knight)和弓箭手(Archer)等英雄，一路消灭怪物、保护家园，杀死怪物军团的首领鼠大王(Rat)夺取胜利。

## 操作说明

玩家进入游戏后，可在“职业与装备选择界面”选择对应的职业与武器装备。

可供选择的职业有：膜法师(Mage)，武士(Knight) 和弓箭手(Archer)。

鼠标左右滑动可切换职业。将对应的铠甲、头盔和武器拖动到角色身上可切换装备。

单击Battle按钮进入游戏界面。玩家可控制自己选择的职业角色，队友由系统自动控制。

玩家需要和队友配合消灭怪物，怪物会随着上一批的死亡不断涌现。玩家单击地图空白处可移动到指定地点，单击怪物执行攻击指令。

角色受到怪物攻击会损失HP，血槽为空时角色死亡。玩家在达到指定地点之后，将会迎战怪物军团首领鼠大王(Rat)。英雄阵营中有一人以上存亡且击败鼠大王即可获得游戏胜利，若英雄阵容全体阵亡，游戏失败。

在战斗过程中，角色会积累怒气。当角色的怒气槽集满时，对应角色上方出现光点。此时玩家单击屏幕右下方任意角色（含非玩家所选角色）的头像可激发特殊技能，对怪物造成意想不到的打击效果。同时，玩家在战斗过程中有一定几率出现暴击效果，打击效果加倍。

- 附：英雄职业和武器对照表

|英雄职业|武器|远/近距离|
|-------|----|--------|
|膜法师(Mage)|冰球|远距离|
|武士(Knight)|刀|近距离|
|弓箭手(Archer)|箭|远距离|

- 附：英雄职业属性表  

|英雄职业|膜法师(Mage)|武士(Knight)|弓箭手(Archer)|
|:---|:--|:---|:--|
|等级|23|23|23|
|攻击力|280|250|200|
|血量|1100|1850|1200|
|防御力|120|180|130|
|特殊攻击力|250|350|200|

## 源代码与项目资源

### 源代码管理

邱宇航(Scene) 谢天(Logic) 杜佳豪(Actor)

### 源代码介绍

#### Actor  
 Actor.cpp 所有角色（英雄和怪物的基类），储存角色的各类等属性，处理角色模型和显示、角色的各类状态及切换、攻击和受伤害、角色属性更新等各类工作。  
 
 Archer.cpp 处理弓箭手的攻击和受伤害、动画及音效播放及装备更换等工作。  
 
 Mage.cpp 处理膜法师的攻击和受伤害、动画及音效播放及装备更换等工作。  
 
 Knight.cpp 处理武士的攻击和受伤害、动画及音效播放及装备更换等工作。  
 
 Dragon.cpp 处理龙（怪物）的攻击、死亡事件及动画及音效播放等工作。  
 
 Piglet.cpp 处理猪（怪物）的攻击、死亡事件及动画及音效播放等工作。  
 
 Slime.cpp 处理精灵（怪物）的攻击、死亡事件及动画及音效播放等工作。 
  
 Rat.cpp 处理鼠大王（怪物）的攻击和受伤害、死亡事件及动画及音效播放等工作。 
  
AttackCommand.cpp 攻击(Attack)的基类BasicCollider以及子类ArcherNormalAttack、MageIceSpikes、DragonAttack、BossNormal等。负责处理攻击事件，播放攻击特效，调用受伤害事件。  

### Scene 
 
BattleFieldUI.cpp 战斗界面UI显示，包括血槽、怒气槽、游戏计时、角色头像等。  

BattleScene.cpp 加载战斗场景，执行场景加载、相机移动等工作。  
ChooseRoleScene.cpp 加载职业角色界面。
  
HPCounter.cpp 计算伤害、加载和刷新血槽、播放扣血动画。  

LoadingScene.cpp 加载加载界面，并加载游戏所需资源。
  
MainMenuScene.cpp 加载主菜单界面。  

### Logic

GameMaster.cpp 游戏逻辑的控制中心。执行加载怪物等工作。  

 GlobalVaribles.cpp 存储和加载全局变量（绝大多数是游戏中的数值，例如攻击力）。  
 
 Helper.cpp 函数库，一些其他文件会用到的小函数统一放在这个文件里面。  
 
 JumpBy3D.cpp 加载JumBy3D动画(从网上找的)。  
 
 Manager.cpp 英雄与怪物管理器，负责位置检测、碰撞检测等工作。
   
 MessageDispatchCenter.cpp 消息传输与分发中心，连接逻辑和屏幕显示的桥梁。  
 
 ParticleManager 粒子管理器，加载粒子特效并在适当时候使用。  
 
### 项目资源
../Resouces/  
 audios 音频文件  
 battlefieldUI 战斗场景UI素材  
 chooseRole 角色选择界面素材  
 fonts 字体文件  
 FX 特效素材  
 loadingScene 加载界面素材  
 mainMenuScene 主菜单素材  
 model 角色素材  
 particle 粒子素材  
 shader3D 3D阴影素材  

## 代码实现 
 
### 状态机(AI Machine)
 
本项目中，玩家控制一个英雄角色，而另外两个英雄角色均需要系统控制。

实例中给每一个Actor类设置了一个状态机，并给每一个Actor类设置idleMode，walkMode，knockMode，attackMode，dyingMode五种状态。

通过Actor类成员函数stateMachineUpdate()切换角色状态。

状态切换由事件触发：如血槽已空、检测到攻击范围内的怪物（findEnemy()返回true）、受到攻击。

状态机在游戏运行中起着至关重要的作用，保证所有怪物和非玩家控制英雄角色正常执行功能。

### 攻击  

当Actor类成员函数`findEnemy()`返回true或玩家单击怪物时，Actor状态变为AttackMode。此时执行`NormalAttack()`函数（玩家单击角色头像英雄角色执行`SpecialAttack()`函数）。

函数会在事件发生地点创建一个BasicCollider的子类，如Dragon发动攻击创建DragonAttack，Knight发动普通攻击创建KnightNormalAttack，并创建攻击特效、加入AttackManager中。全局函数`solveAttack()`会调用`OnUpdate()`函数移动攻击特效，当攻击特效与目标碰撞时，调用目标的`hurt()`函数，产生伤害效果。

### 自动寻怪 
 
Actor类会不断执行`findEnemy()`函数。

对于英雄，遍历MonsterManager，寻找攻击范围内最近目标；

对于怪物，遍历HeroManager，寻找攻击范围内最近目标。

### 加载怪物  

游戏进程由一个整型stage表示。

当场上怪物小于设置的最小怪物时，GameMaster的成员函数`logicUpdate()`会调用randomshowMonster(bool isFront)随机生成怪物，同时stage=stage+1。当stage达到一定数值时，场上不再加载新的普通怪物，而是`调用showBoss()`加载终极怪物鼠大王(Rat)。

### 消息分发
  
当场上产生怒气值改变、血量改变或特殊攻击等事件时，调用`MessageDispatchCenter::dispatchMessage
(enum MessageType messageType, Actor* param)`传递相关参数。相关参数被传至UILayer，刷新血槽和怒气槽。

### 场景

  - 加载场景  
    载入游戏所需的资源，并进入主菜单
  - 主菜单
  - 英雄选择场景  
    换英雄的装备，并选择英雄，开始游戏
  - 战斗场景
    创建相机，加载3D地图，ui层，并驱动游戏主逻辑

## 开发历程  

Using:  
Windows 8.1/10  
Microsoft Visual Studio 2015  
Cocos2d-x 3.10  
CocoStudio  
Github  

## 时间线：

- 2016/4/27 成立项目组，开始规划项目需求

- 2016/5/10 确立项目选题

- 2016/5/15 完成项目需求分析，确立项目分工、建立git仓库

- 2016/5/16 完成项目概要设计，建立组织结构

- 2016/5/19 完成项目详细设计，建立类的层次结构及调用关系，明确函数和算法

- 2016/6/5 完成编码，开始软件测试。

- 2016/6/15 第一阶段测试结束，项目已可以流畅地运行，所有功能均可以实现。

- 2016/6/18 第二阶段测试结束，撰写项目文档。

## 产品测试  
在交由用户进行测试的过程中，我们收到一些细节上的反馈。如：

1. 弓箭手攻击动画不够流畅，箭没有从弓弦位置射出。  
2. 怒气值增长过快，导致游戏难度下降。  
3. 游戏音效与游戏格格不入。  
4. 怪物Slime攻击能力过强，英雄角色容易被Slime围攻，游戏难度加大。  
5. 角色可供选择的装备过少。  
6. 血槽变化没有动态效果，显得突兀。  
7. 当Boss说话的时候，应该设置所有角色不可移动。  

除第5点因素材缺少无法实现之外，我们一一接受了反馈并逐一修改。在此对提出宝贵意见的同学们表示衷心的感谢！  