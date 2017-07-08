# 常用组件及系统资源

## 引言

接下来学习如何创建一个就基本游戏物体,这些游戏物体都是一些白色的标准形状体,也称作白膜,那么这些“白膜”的性质实际上是和我们游戏中的玩家模型是同一个性质的,只不过外表不同而已,那么有了这些模型之后一定是需要对这些游戏物体进行一些控制的,那么如何控制这些游戏物体就离不开Unity引擎中提供的组件,脚本可以用来控制逻辑,碰撞器可以检测碰撞 等等…这些组件都有它们各自的功能,当添加到游戏物体上的时候就可以作为这个物体的一个功能,Unity中给我们提供了很多便捷的功能,熟练使用这些功能配合快捷键,能够极大的提高我们的开发效率,本讲主要是对一些系统资源和基本组件进行学习.

## Unity引擎与资源管理

### Game Object游戏对象

游戏物体（Game Object）指的是出现在Hierarchy面板或者在Scenes场景中所有的游戏资源。包括空物体（Empty Object）、标准几何体、模型、摄像机、粒子、灯光、地形、树木等等。万物皆对象。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%871.png)

在3DObject选项中,可以创建一些基本物体,一些标准的几何体,一些平面,还有可以使用Terrain 来创建一个地形,来手动绘制游戏地形

### Component功能组件

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%872.png)

功能组件（Component[kəm’pəʊnənt]），是挂载到游戏物体上的功能组件。游戏对象通过添加不同的Component组件，从而使不同的游戏对象具备了不同的功能。所以我们可以说游戏对象（Game Object）是由一系列不同功能组件的集合。

比如我们给游戏物体添加了刚体组件，可以使其具有物理系统功能。而给游戏角色添加动画组件，也可以使其具有了动画的能力。甚至脚本也是一种组件。

Unity为我们提供了丰富的组件，如刚体组件，粒子系统，摄像机组件，GUILayer组件等。要注意的是，每一个游戏对象都至少有一个或多个组件。比如最简单的空物体对象（Empty Object），拥有一个Transform组件。而Transfrom组件包含了一个游戏物体的Position（位置），Rotation（旋转），Scale（缩放）三组信息。

### 组件右上角小齿轮属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%873.png)

* 1. Reset：复位。恢复该组件的默认数值。如果是Transform组件，则会回到坐标系0,0,0原点。

* 2. Move to Front：对多个子物体，将其移动到这些子物体的最上方。

* 3. Move to Back：对多个子物体，将其移动到这些子物体的最下方。

* 4. Remove Component：移除组件。销毁对应的组件，即把该组件从当前物体中去除。

* 5. Move Up：上移组件的排列顺序。

* 6. Move Down：下移组件的排列顺序。

* 7. Copy Component：拷贝组件。此选项可以把组件中所有的属性信息值赋值到内存中。

* 8. Paste Component As New：粘贴组件。当选择Copy Component选项后，可以在一个新的游戏物体中粘贴该组件，并把对应的所有信息也赋值过来。

* 9. Paste Component Values：仅仅复制拷贝过来的其它组件的数值信息。

## 地形系统

http://blog.csdn.net/pleasecallmewhy/article/details/8519577

## Camera摄像机

摄像机，Unity的核心组件之一。显示场景中，摄像机所照射的部分，是向玩家捕获和显示世界的设备。

摄像机的特性：

* 1. 可以自定义和操纵摄像机；

* 2. 可以在场景中不受限制其数量；

* 3. 可以设定成任意的渲染次序；

* 4. 可以渲染到屏幕上的任意位置。

摄像机实质上是用于将游戏显示给玩家看的，它们可以被定制，在上面写脚本或者挂载到其他物体上面以获得想象中的各种效果。对于较小的固定场景，可以对游戏的全部视图保持摄像机静止即可；对于第一人称射击游戏，可以将摄像机挂载到玩家角色上面；对于一个赛车游戏，也可以让摄像机跟随赛车。

还可以创建多个摄像机，然后为每一个赋予不同的深度值。摄像机是从低深度值到高深度值的次序进行绘制，一个深度值为2的摄像机将会在深度值为1的摄像机绘制之后再绘制。同时可以调整Viewport Rect属性来调整摄像机视图在屏幕上的位置和大小，使用这个可以创建多个迷你视图。

#### Camera摄像机 基本属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%874.png)

* 1. Clear Flags：清除标记。显示背景内容，默认为天空盒子。

* 2. Background：背景颜色。

* 3. Culling Mask：剔除遮罩。用于显示某些层（可以过滤不需要显示的层）。

* 4. Projection：摄像机投射方式（透视->广角/正交->平行）。

  * Perspective(透视):以3D方式观察物体

  * Orthographic(正交):以2D方式观察物体
* 5. Field of View：视野范围。可以用这个选项来做狙击镜的效果.

* 6. Clipping Planes 裁剪面。相机到开始和结束渲染的距离。

* 7. Viewport Rect：矩形视窗（可控制视窗的偏移量与长度和宽度，即：分屏显示功能）。

* 8. Depth：摄像机深度（若存在若干摄像机，则先渲染数值小的摄像机画面）。

* 9. Rendering Parth：渲染路径。

* 10. Target Texture：目标贴图纹理。

* 原理：就是将此摄像机摄像的画面影响实时打在一张指定的目标纹理贴图上，此时，这张贴图存有这个摄像机所摄的”实况转播信息“了，则此贴图可以随便放在某个Plane地板或者UI界面中。

* 11. Occlusion Culling：是否使用遮罩剔除。

* 12. HDR：启用摄像机的高动态范围渲染（High Dynamic Range Rendering）。

#### 关于层：Culling Mask 剔除遮罩

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%875.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%876.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%877.png)

#### 关于深度：Depth属性

一个游戏场景中使用了多个摄像机。需要用到摄像机的Depth属性来控制叠加显示效果。Depth属性反应了相机在渲染顺序上的位置。

主摄像机默认的Depth为-1，之后不管创建几个新的摄像机，默认的Depth都为0的。通过修改Depth属性，数值越大，越在最后渲染显示。即：数值大的层会遮挡住数值小的层。

## 系统资源_Light 光源

灯光用来照亮场景和对象，可以创造完美的视觉气氛。灯光可以用来模拟太阳、燃烧的火柴、探照灯、手电筒、枪火光、爆炸等等。

我们通过在Hierarchy面板->Create->Light来创建4种不同的灯光效果。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%871.png)

### 不同类型光源照射的角度、范围

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%872.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%873.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%874.png)

### 4种类型光源的定义、区别

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%87100.png)

### Light灯光组件属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%875.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%876.png)

* 1. Type：光源的类型。

* 2. Color：光照颜色。

* 3. Intensity：[ɪn’tensɪtɪ] 光照浓度。

* 4. Cookie：设置贴图Alpha通道。（在此属性中放置一张透明贴图作为蒙版，从而通过灯光照射打到地面上形成一个预期形状的光影效果）。

* 5. Cookie Size：设置贴图Alpha通道尺寸大小。

* 6. Shadow Type：阴影类型。（Soft Shadows参数最耗费资源）。

* 7. Draw Halo：绘制光晕（在点光源中使用雾蒙蒙的效果）。如果勾选该选项，一个球形的光晕将被绘制。光晕的半径等于范围(Range)。

* 8. Flare：设置光源的闪光效果。用于在光照位置上渲染的闪光。

* 9. Render Mode：光源的渲染模式（渲染优先级）。选择光源是作为顶点光(vertex)，像素光(pixel)，还是自动的渲染方式。

注：要说明的是，灯光有对渲染速度有非常大的影响，因此必须权衡前后照明质量和游戏速度。由于像素光照比顶点光照奢侈得多(更耗费资源)，Unity将只在最亮的光逐个像素渲染。

* 10. Culling Mask：通过层设置指定图层不受到光照影响。

* 11. Lightmapping：设置光照贴图模式。

  * Realtime Only：实时光照。动态光源

  * Auto：自动的

  * Baked Only：烘焙后的。静态光源

注意: 只有平行光默认有影子,其他光源将Shadow Type修改即可。

### Area Light实例

1. 创建场景内道具模型物体：Plane、Cube

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%8710.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%8711.png)

![]()https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%8711.png

2. 创建Area Light

注：Transform角度为90度（影响区域方向线冲下）

调节Color颜色：比如绿色

Intensity浓度要低：设置为0.1

影响区域：Width为1；Height为6

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%8713.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%8714.png)

3. 打开Lightmapping（场景烘焙窗口）窗口面板,选中所有要烘焙的物体：Plane、Cube,在Lightmapping面板下Object选项卡中，把所有物体打成“静态”，即：勾选Lightmap Static

4. 烘焙场景：点击Bake Scene

### Area Light实例

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%8715.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img3_%E5%9B%BE%E7%89%8716.png)

可以看出：由于各个点的位置不同，会烘焙成不同的光照亮度效果,当挪动Cube，会发现：光照效果没有变化（不是实时变化的）,实际上此时的光类似于贴图的方式，静态的绘制在各个经过烘焙的物体上了

## 系统资源_Texture贴图纹理

Texture资源是Unity中用途最广泛的资源之一。它可以应用在

* 界面UI

* Mesh模型

* 粒子效果

* 视频资源

* Movie Texture：视频资源

* Render Texture：渲染贴图

Texture 属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%871.png)

1. Texture Type：贴图类型 *

* Alpha from Grayscale：从灰度图中是否产生Alpha通道

* Wrap Mode：贴图与贴图之间的拼接模式 *

* Filter Mode：过滤模式

* AnIso Level：异向性过滤等级

### Texture Type

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%872.png)

1. Texture：普通贴图

* Normal map：法线贴图

* Editor GUI and Legacy GUI：UI贴图

* Sprite（2D and UI）：精灵

* Cursor：鼠标指针

* Reflection：反射贴图

* Cookie：遮罩贴图

* Lightmap：烘焙贴图

* Advanced：高级（可自定义一些贴图属性）

### Texture 修改Tilling参数

创建Plane，并拖拽到Plane上做为贴图，修改Tiling参数

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%873.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%874.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%875.png)

### Texture Wrap Mode（贴图间拼接模式）

修改Wrap Mode参数：

Repeat：连续的分开状态

Clamp：拉伸状态

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%876.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%877.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%878.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%879.png)

## Materials材质

Material[mə’tɪərɪəl]材质用来把网格（Mesh）或粒子渲染器（Particle Renderers）贴到游戏对象上。Material是控制游戏中物体的外观的资产，影响着对象被显示的效果。
这些组件不能在没有材质的情况下显示。
而任何材质的属性取决于选定的着色器（Shader）发生变化。
许多物体可以共用同一个材质球。好处：节省资源的开销、修改的效率。缺点：容易不知情下修改了多个物体。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8712.png)

### Material材质的基本属性：

* 1. Shader：着色器。将被材质（Material）使用的着色器。

* 2. Main Color：主颜色。默认为白色。

* 3. Base：基本纹理贴图。（皮肤）。

Mesh是指模型的网格，MeshFilter一般是用于获得模型网格的组件，而MeshRender是用于把网格渲染出来的组件。

我们可以理解为：Mesh Filter决定了物体的形状、模样；Mesh Render决定了物体的颜色和纹理。

即: Mesh Filter获取我们的模型; Mesh Render把它在场景中渲染

### 纹理贴图、材质球与着色器关系

材质（材质球）是由贴图与着色器的渲染而形成的。最终应用到场景内物体的身上。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8717.png)

### 创建立方体 + 添加Materials材质

创建一个立方体：Hierarchy面板->Create->Cube；

再创建一个材质：Project面板->Create->Material。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8718.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8719.png)

### 在Mesh Filter中指定Mesh网格

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8720.png)

### 在Mesh Renderer中指定Materials

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8721.png)

Cast Shadows：是否产生阴影效果

Receive Shadows：是否接收阴影

动态改变材质颜色的代码为：

Getcomponent«Renderer»().material.color = Color.Red//把材质编辑为红色

## Shader着色器

我们如果想对选择的材质做更丰富的显示效果，需要编辑材质中Shader的属性。根据选择的着色器类型，在Inspector检视面板会出现许多不同的属性。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8722.png)

### Unity内置Shader标准着色器

Unity中提供了一些基本的着色器,我们可以进行一些简单的了解,在实际开发中,如果Unity提供的Shader效果不能满足要求,那么还需要自己来写一些Shader效果

* 1. Bumped Diffuse：[bʌmpt]。凹凸散射（凹凸漫反射）。

凡Bumped凹凸的，都是带法线贴图的，使用Normal map来表现物体表面的细节。

* 2. Bumped Specular：凹凸高光（法线凹凸贴图 + 高光）。

* 3. Decal：[’diːkæl]。贴花纸。（制作两个贴图叠加效果）。

贴花着色器，需要主纹理、贴花纹理（带alpha）。

* 4. Diffuse：[dɪ’fjuːz]。漫反射。（弥漫的散开的）。默认的Shader。

* 5. Diffuse Detail：[’diːteɪl]。漫反射 + 细节（漫反射细节着色器）。比如地形，当镜头更接近时，使其拥有更清晰、更细节的效果。

* 6. Parallax Diffuse：[’pærəlæks]。视差（高度图） + 漫反射。（实现很强的明暗关系（立体感），如鹅卵石效果)。

* 7. Parallax Specular：视差（高度图） + 高光。即：视差高光。像镜面般会反射。

* 8. Specular：[’spekjʊlə]。 高光。（镜子的；会反射的；带金属质感）。且随着镜头动态的显示其高光效果的。

* 9. VertexLit：[’vɜːteks]。定点光，顶点照亮。

### Unity内置的着色器库

* 1. Mobile：移动的

* 2. Nature：自然的

* 3. Particles：粒子系统的

  * Particles/Additive：[’ædɪtɪv]附加的。（一般会把背景剔除）。
  * Particles/Alpha Blended：Alpha混合。（双面透视效果，比如红旗正反可以观看）。

* 4. Reflective：反射的。反射周围图像效果。一张主帖图，一个Cubemap用于反射。
　
 主纹理的alpha通道定义在物体表面的反射强度。
　
 任何场景灯光将会增加反射表面的照明。

* 5. RenderFX：着色

RenderFx/SkyBox：天空盒着色器。

* 6. Self-Illumin：自发光的。主要用于发光物体。
　　
  一张主帖图，一张自发光纹理。
　
 发光基于发光纹理的alpha值，alpha为0的不发光，1表示充分发光。不需要任何灯光照射来发光。
　
 任何顶点灯光或像素灯光将简单增加更多光照到自发光上。

* 7. Toon：卡通的

* 8. Transparent：[træn’spær(ə)nt]。透明的。透明着色器用于实现全透明或者半透明效果。

选中该选项后,调整Main Color中的R/G/B/A色值中的A选项,从而达到调整透明度的效果。

Transparent/Cutout/..透明镂空着色器。

* 9. Unlit：[ʌn’lɪt]。不发光的，不受灯光影响的。比如: 场景中需要一张背景贴图,而又需要使其不受环境灯光颜色和亮度的影响时使用.

Mobile->Unlit(Supports Lightmap) : 支持一个Lightmap贴图的,即“自身光照的”.可以理解为一种自发光的方式不受环境和灯光的影响

* 10. Legacy Shaders：[’legəsɪ]。遗留着色器。。(老版本着色器)

分类：

* 标准着色器：Normal

* 透明着色器：Transparent

* 镂空着色器：Transparent/Cutout

* 自发光着色器：Self-Illumin

* 反射着色器：Reflective

### 手动创建法线

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8724.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8725.png)

Bumped需要增加Normal法线贴图来实现凹凸效果，在Project面板中选中图片素材：

* ->Ctrl+D（复制）一个图片

* ->在Inspector面板中调节Texture Type（图片类型）属性为Normal map（法线图）

* ->Apply（应用属性修改）。要注意的是勾选Alpha from Grayscale（阿尔法从灰度）选项会让凹凸感更强烈。

* ->回到Material材质球上，选中要修改的材质球，在Inspector面板上修改Shader属性，调节为：Bumped Diffuse，并把法线贴图拖放进来。

### 不同Shader产生不同光照及纹理效果

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8726.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8727.png)

这里只列举两个不同的Shader效果,剩下更多的效果可以自己去试验

## RenderTexture渲染贴图 A

渲染贴图最大的特色是贴图为动态的，其具体呈现的内容是由专门的一个摄像机捕捉，经常应用于小地图或者实时同步监控录像。

1. 创建一个Quad。

2. 创建渲染贴图（RenderTexture）。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%87131.png)

B

3. 创建Camera（摄像机）。

4. 把Render Texture渲染贴图拖放到新创建的摄像机中的Target Texture属性中。这样摄像机看到的内容都会实时反映到渲染贴图中。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%8714.png)

C

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/%E5%9B%BE%E7%89%8715.png)

5. 创建New Material材质，在材质上加载渲染贴图。Shader调节为自发光材质，添加到RenderTexture中。

6. 把带着Render Texture信息的材质球赋予给Quad面片。

实现原理:

将Render Texture拖放指定至摄像机的Target Texture属性后，此时摄像机所照射渲染出的属性将不会打到屏幕上，而是直接打到这张Render Texture贴图上。
（即：利用Render Texture来捕捉摄像机所捕捉到的内容，并渲染成动态的贴图，从而实现一些特殊的效果）

## 天空盒,视频资源,音频资源,雾效,预设

在游戏中我们经常可以看到漂亮的天空,炫酷的开场动画,以及打击感十足的背景音乐,接下来就来告诉大家这些效果在Unity引擎中都是如何来实现的.以及Prefab的作用

### Sky Box天空盒子

Unity集成开发环境自带了强大的天空盒资源。SkyBox天空盒实际上使用了特殊的Shader材质，可以笼罩在整个游戏场景之外，并根据材质中制定的纹理模拟出类似远景、天空等效果，使游戏场景看起来更完整。

在Unity中，天空盒的使用方法有两种：

1. 在Unity中Lighting（渲染设置）里进行指定，这种方法是针对游戏场景的，简单地讲，就是在同一个游戏场景中，无论使用哪个摄像机对象，天空盒都保持不变，并且该方式指定天空盒可以在Scene视图中直接显示。

2. 为摄像机对象添加天空盒组件，然后在天空盒组件中进行指定，这种方法只针对摄像机本身，简单地讲，就是在同一个游戏场景中，如果切换摄像机，天空盒会随之变换，为摄像机指定的天空盒优先级会高于在渲染设定中指定的天空盒。

### 通过Lighting(渲染设置)指定天空盒（A）

1. 导入Unity系统的天空盒资源：

讲天空盒资源导入到工程中,导入资源后，会在Project面板上导入的资源里看到9个代表不同天空效果的材质球。

B

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8738.png)

注：用于渲染天空盒的材质，包括6个纹理。这种材质应该用天空盒着色器（Skybox Shader），而每个纹理应该配置适当的全球的方向。

C

2. 打开Lighting面板：菜单栏->Window->Lighting

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_Lighting.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_Lighting%E9%9D%A2%E6%9D%BF.png)

3. 将天空盒的材质球拖拽到Skybox中即可看到效果

### 为摄像机对象添加天空盒组件（A）

1. 对摄像机添加一个组件:Skybox

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8742.png)

2. 把之前导入的天空资源的材质球拖放到Skybox组件中就可以完成天空盒子的制作部署。

注意在Lighting中添加天空盒与对摄像机添加天空盒的区别

### 自定义天空盒步骤（A）

除了skybox资源包中提供的天空盒外，Unity还支持用户自制天空盒。这需要提前准备好6张图片纹理，分别用于贴在天空盒材质的前、后、左、右、上、下等6个面上。图片需要将其处理成无缝连接的操作。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8743.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E8%87%AA%E5%AE%9A%E4%B9%89%E5%A4%A9%E7%A9%BA%E7%9B%92.png)

1. Project面板->鼠标右键->Create->Material，创建一个材质。

在Inspector面板中属性里点击Shader下拉列表里选择Skybox->6 Sided

B

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8745.png)

2. 单击Front（+Z）项右侧纹理预览窗中的Select按钮，在弹出的Select Texture对话框中选择相应的纹理。
（其他图片纹理同理）。

C

3. 选择菜单栏中的Window->Lighting选项，在Inspector视图中会显示出Render Settings的参数面板，将制作好的材质球拖放到Skybox中，即指定游戏场景中刚才创建的天空盒材质。

D

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8747.png)

4. 仔细观察天空盒的效果，可以发现在天空盒的转折处有明显的接缝，这是由于纹理的Warp Mode（循环模式）设置方式造成的。

E

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img4_%E5%9B%BE%E7%89%8748.png)

5. 选中6张纹理图片，将该纹理在Inspector面板中的Warp Mode设置为Clamp(固定)就可以了，操作完成以后，可以发现，天空盒转折处的接缝完全消失。

## 雾效

http://jingyan.baidu.com/article/4d58d5411e49de9dd4e9c037.html

## MovieTexture 视频贴图（A）

在Unity中，可以将视频文件作为一种动态的贴图纹理贴附在指定物体表面上，从而实现在场景中播放视频的效果。

1. 因为Unity播放视频资源时需要使用QuickTime播放器,所有需要在本地电脑安装Unity认识的QuickTime软件，并将其设置为默认播放。

2. 导入Unity系统认识的视频资源（如.mov格式或者mp4格式）。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img10_%E5%9B%BE%E7%89%875.png)

B

4. 在Scene场景中创建Quad（面片），作为播放荧幕。

5. 制作脚本如下图：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img10_%E5%9B%BE%E7%89%877.png)

C

6. 将脚本拖放到Quad上。并指定视频文件属性。

7. 将视频贴图中的音频文件拖放到Quad上。如资源导入到Project中依然无法识别,需要重启电脑.这是因为当前Unity的配置信息没有找到刚安装的QuickTime.

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img10_%E5%9B%BE%E7%89%878.png)

D

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img10_%E5%9B%BE%E7%89%879.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img10_%E5%9B%BE%E7%89%8710.png)

如果画面不够亮,可以使用材质球中的Shader效果来更改渲染方式

## Audios音效

### Audios音效 介绍

音频是多媒体的重要组成部分，在游戏中是不可或缺的元素，是构成游戏背景音乐、特效音乐等内容必须的资源。音乐不仅能渲染出玩家攻略游戏时的氛围，还能增加提高玩家对游戏的认知度，可以立马变得“高大尚”起来。

Unity支持对音乐格式的压缩，对于较短的音乐文件，通常是做为短促的音效使用，音质要求高，则不需要再进行压缩。而对于较长的音乐文件，一般都作为背景音乐使用，则通常会对音乐文件进行压缩。而压缩后音质会有轻微损失，但压缩后的文件会缩小，从而节省了资源。

Unity支持多种音乐格式的文件：.WAV、.AIFF适合较短音乐文件（比如游戏打斗音效）；.OGG、.MP3适用于较长音乐文件（比如游戏背景音乐）。

### 创建Audio Source 音频源组件

声源组件(声音的发出者,绑定到发生的物体上)

Inspector面板->Component->Audio->Audio Source

Audio Source 音频源在场景中播放音频剪辑(Audio Clip)。如果音频剪辑(Audio Clip)是一个3D剪辑，音频源是在一个给定的位置，并会随距离衰减这样的方式进行播放。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img13_%E5%9B%BE%E7%89%8715.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img13_%E5%9B%BE%E7%89%8716.png)

### 创建Audio Listener 音频侦听器（耳朵）

声音监听组件(相当于人类的耳朵,可以用来收听声音,一般绑定在游戏中的角色物体上),可以决定3D音效效果的收听位置,这个组件默认会在主摄像机中存在一个

Inspector面板->Component->Audio->Audio Listener

Audio Listener 音频侦听器可以接收任何在场景输入的音频源（Audio Source），并通过计算机的扬声器播放声音。音频监听器本身没有属性，它必须被添加才能使用，并总是默认地添加到主照相机。而每个场景只能有1个音频侦听器正常工作。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img13_%E5%9B%BE%E7%89%8718.png)

### Audio Source 音频源属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/02_%E5%BC%95%E6%93%8E%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86/img/img13_%E5%9B%BE%E7%89%8719.png)

1. Audio Clip：音频剪辑。将被播放的声音剪辑文件 *

* Mute：静音。如果启用，声音仍然会播放，只是没有声音（静音）

* Bypass Effects：直通效果。可直接打开/关闭所有特效。

* Play On Awake：唤醒时播放。如果启用，则声音会在场景启动的时候开始播放。如果禁用，则需要从脚本中使用的play()命令来启动它。 *

* Loop：循环。启用这个属性使音频剪辑（Audio Clip）在播放结束后循环 。 *

* Priority：优先权。确定场景所有并存的音频源之间的优先权。（0=最重要的优先权。256 =最不重要。默认为128）。

* Volume：音量。 *

* Pitch:音调。改变音调（Pitch）值，可以减速/加速音频剪辑的播放。1是正常播放速度。 *

* 3D Sound Settings：3D声音设置。

* Pan Level：平衡调整级别。设置多少，3D引擎在音频源上有效果。

* Spread：扩散。设置3D立体声或者多声道音响在扬声器空间的传播角度。

* Doppler Level：多普勒级别。决定了多少多普勒效应将被应用到这个音频信号源（如果设置为0，就是无效果）。

* Min Distance：（声音衰减）最小距离。

* Max Distance：（声音衰减）最大距离。

* Volume Rolloff：声音衰减。

* Logarithmic Rolloff：对数衰减。当你接近的音频源，声音响亮，但是当你远离对象，声音下降显着快。

* Linear Rolloff：线性衰减。越是远离音频源的，你可以听到的声音越小。

* Custom Rolloff：自定义衰减。根据你设置的衰减图形，来自音频源的声音行为。

* 2D Sound Settings：2D声音设置。如果是一个二维的声音，应用到音频源的设置

* Pan 2D：2D平衡调整。设置多少，引擎在音频源上有效果。

需要说明的是，3D声音与2D声音的区别为当角色离音源物体近的时候才能听到声音,离得远就不能听到或者听到很小的声源发出的声音。修改3D声音为2D声音:选中音频资源->Inspector面板->3D sound->(Apply)。

```C#
public AudioClip ac;
 void Start () {
 }
 void Update () {
       if (Input.GetMouseButtonDown(0))
       {
           AudioSource.PlayClipAtPoint(ac,Camera.main.transform.position)
       }
 }
```

### 常用音频函数如表

* AudioSource audio; //声明一个音频文件的资源引用

* AudioListener listener; //声明音频侦听器的引用（耳朵）

* AudioClip clip; //声明一个音频片段类型的资源

* audio.loop = true; //声音是否循环播放

* audio.isPlaying //声音是否在播放中(现在声音源中有没有正在播放的声音)

* audio.Play(); //播放声音

* audio.Pause(); //暂停声音

* audio.Stop(); //停止声音

* audio.volume //声音的音量

* Audiosource.PlayClipAtPoint(clip : AudioClip, position : Vector3, volume : float = 1.0F);

* audio.Delayed(); //声音延长多少时间进行播放

* audio.OnAwake(); //是否一实例就进行播放*

## Prefab预设

### Prefab预设的特点

预设在Unity中是一种非常重要的资源类型，是一种可被重复使用的游戏对象。它有如下几个特点：

特点1：它可以被置入多个场景中，也可以在一个场景中多次置入。

特点2：当你在一个场景中增加一个Prefabs，即实例化了一个Prefabs。

特点3：所有Prefabs实例都是Prefab的克隆，所以如果在运行中生成对象会有(Clone)的标记。

特点4：只要Prefabs原型发生改变，所有的Prefabs实例都会产生变化。

我们需要在实践中多体会其功能和作用。

### Prefab预设的创建步骤

创建步骤：

1. 手动创建方式：即从Hierarchy面板中，用鼠标拖动对象物体，直接拖放到Project面板中。

2. 脚本动态创建代码：Instantiate(Prefabs,transform.position,transform.rotation)

### Prefab预设的几点说明

关于预设的几个说明：

1. 通过在Hierarchy面板中的预设的实例对象找此实例物体在Project面板中的位置:

Hierarchy面板->选中实例物体->Inspector面板->Prefab->Select。

2. 如果对预设做改变,则所有的此预设对应的实例物体,都将做改变(即:预设的继承性)

3. 关于对预设属性的重载:即,对某一个实例对象的属性的修改后,哪怕重新对预设对象属性重新做了调整,也不会影响之前其他实例对象的属性值

4. 如果对其中的一个实例对象属性做了修改后,想让预设其他实例对象都做同样调整,则:

选中已修改的实例对象->Inspector面板->Prefab->Apply

注:此时,预设对象对应的这个修改的属性已不具有单独的重载的特性了

5. 如何丢弃重载特性:

选中已修改的实例对象->Inspector面板->Prefab->Revert

6. 预设的优点:提升效率,节省空间

### Prefab预设的实例应用

```C#
public GameObject cubePrefab;
	void Start ()
    {
        for (int i = 0; i < 10; i++)
        {
            for (int j = 0; j < 10; j++)
            {
                Instantiate(cubePrefab, new Vector3(i, j, 0), Quaternion.identity);
            }
        }
	}
```
