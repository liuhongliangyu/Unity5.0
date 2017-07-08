# 初始Unity引擎

## 创建Untiy工程

打开Unity引擎后可以看到如下界面,可以通过点击New键添加一个新的工程,也可以点击Open打开一个已有的工程,当然下边也有一些历史打开的工程可以打开.如果没有如下界面,有可能是Unity引擎没有破解,请看上节课程将引擎进行破解

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870201.png)

## 引擎界面介绍

### 1. 引擎窗口界面

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870206.png)

引擎工作编辑界面说明：

* 1. 标题栏：显示了标题的项目名称信息。(场景名,项目名,发布平台)

* 2. 导航菜单栏：包含了主要的菜单命令，是软件与用户交互的主要方式之一。我们可以通过导航菜单栏创建项目，执行常用的操作命令，加载资源、组件，创建地形等。

* 3. 工具栏：提供了方便场景操作的方式。可以方便控制项目对象的移动、旋转、缩放等。还可以控制项目游戏的播放、暂停、停止等。

* 4. 五大视图窗口区：是针对项目具体的监视和操作区域。

### 2. 五大视图区

* 场景视图：Scene [siːn]，主要把Hierarchy视图中的模型进行设计、摆放的区域。

* 游戏视图：GameObject，是展示效果的区域。

* 层次视图：Hierarchy [’haɪərɑːkɪ]，主要存放游戏场景中具体使用的项目对象。比如：摄像机、贴图、光源、模型、地形等。

* 项目视图：Project [’prɒdʒekt]，主要存放所有的资源文件。比如：脚本、预设、材质、动画片段、音频片段等。

* 检测视图：Inspector [ɪn’spektə]，可以理解为对项目中所有控件的属性修改、设置的地方。

### 场景视图-快捷工具栏

场景视图中，可以自由漫游整个游戏场景。可以单击选择场景中任意物体，对其进行编辑。Q、W、E、R、T键为快捷键：分别对应引擎左上方的工具栏的5个按钮：

* 小手图标：对场景屏幕进行一个拖动移动，改变的是观察角度、观察位置，并不改变场景中物体位置。

注：按住鼠标中键也会直接切换到小手拖动功能。

* 十字图标：对场景中物体进行位移拖动，改变场景中物体实际位置。

* 表面吸附：可拖动如图绿色区域在地面做水平方向的移动，即：不改变其y轴方向。

* 旋转图标：修改选中物体的旋转角度。

* 缩放图标：改变选中物体的大小尺寸（可整体缩放，可单方向缩放）。

* 2D图标：配合Unity的UGUI做2D的UI制作使用的。

### 移动物体

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870207.png)

### 定向定量移动方式

菜单栏->Edit->Snap Settings

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870208.png)

### 坐标陀螺（切换视图模式）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870209.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870210.png)

* Persp：透视、远景、广角视图。近大远小原则。

* Iso：没有近大远小原则。

* 点击小方块或者Persp、Iso文字做2种视图模式切换。

* 点击x、y、z轴（红、绿、蓝）任意一个轴方向可以得到对应的视野。

* Shift + 中间小方块得到广角模式下的标准45度角度视野。

### 移动观察视角

画面拉远/拉近：旋转鼠标齿轮(或者:Alt + 鼠标右键)

按住鼠标右键：以画面后方观测点为轴移动视图观察角度(幅度大)。即：对镜头的自由旋转。可以理解为在场景前面有一个镜头，我们的操作就是对此镜头做360度自由旋转，来观察场景。

Alt+鼠标左键：以画面中心点为轴移动视图角度(幅度小)。上一个快捷方式理解为旋转观察着自己（或者旋转观察镜头），这个快捷键则可以理解为旋转场景来观察。

### 漫游（飞行模式）

在Scene场景视图中漫游（三维漫游）：按住鼠标右键+W/A/S/D/Q/E（按Shift键，可加速）（透视模式下）

向“向方向键前进”（二维漫游）：Shift +方向键（正交模式下前后变上下）

### 定位

* 1. Ctrl+Alt+F:把选中物体移动到玩家视野中间位置（移动了物体位置）

* 2. Ctrl+Shift+F

  * A. 若选中摄像机：使摄像机与当前观察点同为一个重合位置：使Game与Scene的视角同步（移动了摄像机位置）

  * B. 若选中其他游戏对象：使游戏对象与当前观察点同为一个重合位置（移动了物体位置）

* 3. 视野与摄像机位置不是一回事。

快速定位一个物体的位置：Hierarchy层次面板->鼠标双击物体的名称

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870301.png)

### 创建物体

* 新场创建景（Create New Scene）：Ctrl+N

* 创建空物体(Create Empty)：Ctrl+Shift+N

## 总结：方便的快捷键

```
1.方便的快捷键：
2.转换观察角度	Q
3.移动物体	W
4.旋转物体	E
5.缩放物体	R
6.表面吸附	Shift+Ctrl+选择物体或鼠标点击拖动        中的绿色部分
7.以画面后方观测点为轴移动视图观察角度(幅度大)	鼠标右键
8.以画面中心点为轴移动视图角度(幅度小)	Alt+鼠标左键
9.画面放大/缩小观看	旋转鼠标齿轮
10.在Scene场景视图中漫游（三维漫游）	按住鼠标右键+W/A/S/D/Q/E（按Shift键，可加速）（透视模式下）
11.向“向方向键前进”（二维漫游）	Shift +方向键（正交模式下前后变上下）
12.运行/停止	Ctrl+P
13.暂停	Ctrl+Shift+P
14.复制/粘贴	Ctrl+D
15.恢复	Ctrl+Z
16.重命名	(选择物体名字)+F2
17.使Game与Scene的视角同步	在Hierarchy中选中摄像机->Ctrl+Shift+F：使游戏对象与当前观察点同为一个重合位置（移动了物体位置）
18.把选中物体移动到Scene视图的中心位置上	在Hierarchy或Scene视图中选中物体->Ctrl+Alt+F
19.快速定位一个物体的位置	Hierarchy层次面板->鼠标双击物体的名称
20.快速定位一个物体的位置	选中物体->(鼠标放到Scene视图中)->F
21.新场创建景（Create New Scene）	Ctrl+N
22.创建空物体(Create Empty)	Ctrl+Shift+N
```

## 工具栏_轴心切换工具

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870501.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870501.png)

Pivot[’pɪvət]：选择轴心（Pivot）意味着将使用各个物体的实际的自身轴心

Center：选择中心(Center)意味着使用当前所选所有物体加权重之后的共同轴心

### 工具栏_Pivot/Center实例

示例：如何改变一个物体的轴心位置（一般讲：一个物体的轴心都是在中间重心位置的）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870503.png)

步骤：

* 1、创建一个空物体（EmptyGameObject），Reset其Transform组件

* 2、创建一个Cube，Reset其Transform组件

* 3、把Cube拖放到空物体内，成为父子关系

* 4、修改Cube的Transform属性值，y轴设置为-1

* 5、选中空物体对象，对其进行手动旋转，观察旋转的轴心方向

相当于修改了其pivot中心轴

### 工具栏_世界/本地坐标切换工具

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870504.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870505.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870506.png)

* Global：全局的

* Local：本地的

* 陀螺仪 或者 说Global可以理解为东西南北 方向是固定的,而local本地坐标可以理解为上下左右 是相对的方向

### 工具栏_游戏运行、停止、暂停

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870507.png)

* 运行/停止 Ctrl+P

* 暂停 Ctrl+Shift+P

* 复制/粘贴 Ctrl+D

* 恢复 Ctrl+Z

* 重命名 (选择物体名字)+F2

### 工具栏_Layers层

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870510.png)
Layers：代表可视的图层。

对这个Layers进行设置可以让Scene场景中的某一层物体显示/隐藏，然后对其根据需要显示或隐藏所指定的图层。但是并不会影响Game场景中的物体

### 工具栏_窗口显示模式（布局）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870509.png)

可灵活拖拽各个窗口标签，摆放到自己更习惯的布局位置上。最后可以自定义并保存下自己习惯的显示模式。

Revert Factory Settings：恢复工厂原设置。

## 游戏视图：Game_游戏运行、停止、暂停

* Game视图，可以理解为游戏玩家真正看到的画面 或者说游戏运行时所看到的画面。

* 游戏可以一帧一帧播放。

* 要注意的是：在游戏运行的时候，如果对游戏对象进行操作，数据将不会保存下来。

* 当游戏关闭时，所有改变的游戏属性都将恢复到开启游戏播放前状态。

### 游戏视图：Game_游戏屏幕长宽比

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870601.png)

自由调节游戏画面的长宽比：

Free Aspect[‘æspekt]：自由外貌、方向（全屏显示）.可以通过点击’+’号来添加一个自定义的屏幕长宽比

### 层次视图：Hierarchy

Hierarchy视图：场景物体列表视图。与Scene场景视图中所有游戏资源一一对应的。可以理解为就是Scene场景视图中所有物体的一个列表。

双击一个物体列表名称，则会快速定位到此物体在Scene场景中的位置画面上。

可以利用关键字搜索场景中的相关系列物体。只有要搜索的物体会彩色高亮显示，而非选中的物体则以灰色效果显示。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870701.png)

### 项目视图：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870702.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870703.png)

Project视图：项目资源列表。

Project项目视图列表与本地的文件夹是一致的，对应的。可以通过鼠标右键->Show in Explorer来找到对应文件夹。

Unity对于每个文件或文件夹会自动生成对应的meta[’metə]文件，所以在移动项目资源时不要在原路径上操作，而应在Unity引擎上Project视图中操作。

### 项目视图：Project_搜索

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870706.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870706.png)

注:Project,良好的项目文件夹结构

### 检测视图：Inspector

Inspector检测视图：属性编辑。

Unity中，任何物体，以及项目资源都可以在Inspector视图中进行相应的编辑。我们可以理解为编辑资源、控件（组件）的属性面板。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/01_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/img/%E5%9B%BE%E7%89%870712.png)


