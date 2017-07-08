# 引语

画布：画，绘画；布，载体。

绘制UI元素的载体。

画布可以理解为UI元素的容器，或者说为UI的根目录。

且所有的控件都必须在Canvas画布的根目录之下，即：只要有一个UI控件，就必须有至少一个Canvas画布。

## Canvas

Canvas画布是摆放容纳所有的 UI 元素的区域。画布是一个游戏对象上的某个Canvas component组件，所有的 UI 元素必须是这个画布的子对象。

当您想创建新的 UI元素，如Image，那么就单击菜单创建：GameObject > UI > Image或者Hierarchy面板中Create->UI->Image，同时一个画布也自动的创建，如果在场景中已经存在一个画布。那么新建的UI元素Image被创建之后就直接作为这早就存在的画布上。

画布区域被显示为一个矩形在场景视图中。这使得它易于定位 UI元素，在任何时候都可以看到，不需要有游戏视图。

画布上有一个Render模式设置：screen space(overlay/Camare) 或 world space，可以设置

Render Mode：渲染模式

* Screen Space - Overlay：覆盖模式 - 屏幕最前端（永远在屏幕最前端显示 - 联想：手机贴膜（贴在手机上，且在最上层）
所有的UI控件都在屏幕的最前端位置显示。无论场景中的任何物体，Camera都要以屏幕的形式显示出来，都是2D的显示效果。
此时，不能调整UI画布的大小（因为UI界面与屏幕大小相同）。
可以理解为UI罩在屏幕上，不与场景中任何物体产生冲突。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/ugui_001.gif)

Screen Space - Overlay：UI画布蒙在屏幕上

UI界面在任何游戏对象/元素，如图cube之上

* Screen Space - Camera：摄像机模式 - 绑定摄像机（用摄像机来渲染）
这是一个与Camera绑定的UI（需要指定一个Camera），可实现一些3D的效果。且UI是与摄像机做跟随移动的。
可以理解为UI罩在Camera上，即：对摄像机的属性改变会影响到UI的属性变化。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/ugui_002.gif)

Screen Space - Camera：UI画布蒙在摄像机上
任何游戏对象/元素可以在UI界面，如图cube之上

3. World Space：世界模式 - 世界空间
即：把UI理解成充当为场景中的一个物体（可进行通常的Transform属性的拖拽操作）。
可以把Canvas作为某个游戏对象的子集物体，比如产生血条效果。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/ugui_003.gif)

World Space：UI画布蒙在世界空间中的物体上

Pixel Perfect：像素完美。是否锐化整个屏幕的显示效果，勾选后，屏幕控件不再有糊化效果，使像素与屏幕像素对应匹配，达到完美显示的效果。

## Canvas Scalar 组件

调整Canvas画布控件的大小

* Constant Pixel Size：按照像素大小

* Scale With Screen Size：按照屏幕大小

* Constant Physical Size：按照物理大小

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/11ebc42e-6604-4c12-9800-ebf7dacf2c52.png)

## Canvas Raycaster 组件

调整射线相关，即调整射线关联OnClick事件所包含的物体

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/55e30faa-4a33-489e-b6ea-7593ee3f8bda.png)

## EventSystem 的组件介绍

EventSystem 控件上的组件：

EventSystem组件用来处理UI事件。是自动创建的。

EventSystem系统用来辅助读取UI界面中用户的输入相关，

通过EventSystem才能正常接收UI所显示的内容。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/c321eb4c-9937-4e4f-86c5-e2f8ffb50815.png)

## 基本组件应用

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/171211026576574.png)

## UGUI的核心元素：

* Anchor(锚点)：每个控件都有一个Anchor属性，控件的4个顶点，分别与Anchor的4个点保持不变的距离，不受屏幕分辨率变化的影响。
系统默认设置控件的Anchor位置在其父物体的中心处，且不能离开父物体的范围。

将Anchor设置在父物体的左侧，可以实现左对齐的效果。

将Anchor设置在父物体的4个顶点上，子物体将随父物体同步缩放。

* Pivot(轴)：控件的中心点（或称为轴），控件围绕Pivot发生旋转（若想控件围绕某个顶点旋转，改变Pivot位置即可）

Rec Transform中的PosX、PosY、PosZ指的是Pivot与Anchor间的相对位置

### UGUI的基本控件：

* Canvas(画布)：所有UI控件必须在Canvas上面绘制，也可以看做所有UI控件的父物体。

* Panel(面板)：主要的功能就是一个容器，可以放置其他控件，使其进行整体移动、旋转、缩放等。一个功能完备的UI界面，往往会使用多个Panel容器，甚至使用Panel嵌套。

* Text(文本)：富文本功能类似HTML中的标签。

* Image(图像)：图像源为2D Sprite格式。等比例调节图像大小，需要按住Shift键进行调节。Image Type的Sliced选项，需要对Sprite进行“九宫格”处理。

* Raw Image(原始图像)：图像源为Texture格式。

* Mask(遮罩)：遮罩并不是GUI的控件。它以父物体的范围约束子物体的显示，如果子物体过大，将只显示在父物体中的一部分。

### UGUI的复合控件：

* Button(按钮)：由两个控件组成：

* 1. 添加了Button组件的Image控件，

* 2. Text控件。Image控件是Text控件的父对象。

鉴于UGUI的高度自由，也可以理解为添加了Button组件、Image组件的空对象和添加了Text组件的空对象。

通过Transition对按钮的三态进行设置。

* InputField(输入框)：由三个控件组成：

* 1. 添加了Input Field组件的Image控件

* 2. Text控件（用作显示提示内容）

* 3. Text控件（接收输入内容）。Image控件是两个Text控件的父对象。

Content Type对输入的字符类型进行预处理功能。

* Toggle(开关)：即可以做单选框又可以做复选框，系统默认为复选框。

由四个控件组成：1.添加了Toggle组件的空对象，2.Image控件（显示状态框的背景图），3.Image控件（显示当前状态），4.Text控件（用作显示选项内容）。

如何制作单选框：创建一个空对象，添加Toggle Group组件。在空对象下创建若干个Toggle控件，设置Group，并保持其中一个Toggle控件的Is On开关为true，其余为false。

* Slider(滑动条)：由6个控件组成：

* 1. 添加了Slider组件的空对象，

* 2. Image控件（显示背景图像），
* 3. 空对象（控制填充区域），

* 4. Image控件（显示填充图像），

* 5. 空对象（控制滑块移动区域），

* 6. Image控件（显示滑块）

滑动条通过滑块驱动，在minValue和maxValue区间运动，根据当前的Value值，不断改变背景图像和填充图像的显示范围。

滑动条既可以用作音量控制等输入控件，去掉滑块后，也可以用作血量、进度等显示控件。

* ScrollBar(滚动条)：由3个控件组成：1.添加了Scrollbar组件的Image对象，2.空对象（控制滑块移动区域）,3.Image控件（显示滑块）

滚动条与滑动条的原理类似，对比而言，滚动条背景色单一，数值范围固定为0到1，偏重于单步数值的设置

滚动条既可以用作垂直滚动文本（背包），也可以用作水平滚动时间轴，还可以垂直+水平进行图像的缩放。

### UGUI的高级控件：

高级控件并不是UGUI直接提供的控件，需要自行组合，组合原理可以通过拆解复合控件学习。

* Scroll Rect(滚动区域)：在一个较小的区域显示较多的内部控件的时候使用的一种机制

* Scroll Rect(空对象，设置一定的区域范围，作为当前显示的窗口，添加组件：Scroll Rect、Image、Mask)

* Content(空对象，长度或宽度要大于Scroll Rect)

* Scroll View若干个(根据需要，Image、Button控件随意添加)

* ScrollBar(滚动条控件)
　
 在Scroll Rect组件中设置Content项和Scrollbar项即可

* TabPage(选项卡)：能够在有限的空间中，放入更多的展示内容

TabPage(空对象)

ToggleGroup(空对象，添加Toggle Group组件)

Toggle若干个(根据需要，将Toggle设置为单选框)

DisplayContent(Image，作为背景图。Toggle Group和DisplayContent可以根据需要进行垂直或水平布局)

Page若干个(根据需要，数量需要与Toggle对应)

在Toggle的On Value Changed(Boolean)中设置对应Page的SetActive

## Text文本

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/e5f7c936-f67a-4ace-806c-3a35b140920e.png)

* Line Spacing（文本行距）：两行文字之间的间隔，一般也就在1和2之间最佳。

* Rich Text（开启富文本）：这个默认是开启的，一般情况下也别去关闭它，除非你的字体不想变色、斜体以及添加各种造型。

* Alignment（对齐）：这个没什么好说的了。

* Horizontal overflow（水平溢出处理）：也就是说文本框里的文字在水平方向超出区域限制时候的处理方式，这里使用默认值wrap（隐藏）即可。

* Vertical overflow（垂直溢出处理）：也就是说文本框里的文字在垂直方向超出区域限制时候的处理方式，这里使用默认值truncate（截断超出部分）即可。

* best fit（最佳模式？）：这个具体的效果是什么我也暂时不清楚，就让他保持初始值吧。

RichText富文本

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E6%A6%82%E8%BF%B0/images/4f3208c3-7be9-487b-a188-d3d3e56eb587.jpg)


