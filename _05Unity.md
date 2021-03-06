# 坐标系和向量

## 坐标系基本概念

我们需要三个轴来表示三维坐标系，前两个称作x轴和y轴，这类似于2D平面，第三个轴称作z轴。一般情况下，3个轴互相垂直。也就是每个轴都垂直于其他两个轴。图1展示了一个3D坐标系。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image001.png)

图1 3D笛卡尔坐标系

实际上,我们是位于z轴负方向面向xy平面来进行操作。当我们面对计算机屏幕并且坐标系没有旋转的情况下，实际看到的应该是图2的情况，这时候z轴垂直屏幕向里。在这里的三维空间中，z属性表示深度。当对象向右移动时，x 属性的值会增大。当对象向上移动时，y 属性的值会增大。当对象远离视点时，z 属性的值会增大。若使用透视投影和缩放，则对象在靠近屏幕时会显得大一些，而在远离屏幕时会显得小一些。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image002.png)

图2 面对计算机实际看到xy平面

2D平面中我们指定x轴向右为正，y轴向上为正的坐标系为标准形式，但是3D中并没有标准形式。不同的作者、不同的研究领域使用不同的标准。但这里我们统一使用图1所示坐标系。

把3D中的x轴、y轴等同于2D中的x轴、y轴是不准确的。3D中，任意一对轴都定义了一个平面并垂直于第3个轴（例如，包含x，y轴的xy平面，垂直于z轴。同样，xz平面垂直于y轴，yz平面垂直于x轴）。我们指定+x，+y和+z分别指向右方，上方和前方。

在3D中定位一个点需要三个值：x，y和z，分别代表该点到yz，xz和xy平面的有符号距离1。例如x值是到yz平面的有符号距离，此定义是直接从2D中扩展来的。如图3所示：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image003.png)

图3 3D中定位点

### 左手坐标系与右手坐标系

3D坐标系存在两种完全不同的坐标系：

* 左手坐标系

* 右手坐标系

如果同属于左手坐标系或右手坐标系，则可以通过旋转来重合，否则不可以。

“左手”和“右手”分别代表什么意思呢？

我们先学习一下怎样判断坐标系的类型。伸出左手，让拇指和食指成“L”形，大拇指向右，食指向上。中指指向前方。现在，我们就已经建立了一个左手坐标系，拇指、食指和其余手指分别代表x、y、z轴的正方向。如图4所示：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image004.png)

图4 左手坐标系

同样，伸出右手，使食指向上，中指向前，拇指这时指向左，这就是一个右手坐标系，拇指、食指和其余三个手指分别代表x、y、z轴的正方向。右手坐标系如图5所示：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image005.png)

图5 右手坐标系

无论你怎么转动手腕，也不可能让两只手代表的坐标系重合。

在Unity3D中使用的是左手坐标系。

左手坐标系与右手坐标系对于“正向旋转”的定义也是不一样的，假设空间有一条直线，我们需要绕该直线旋转一定的角度，首先我们叫这个轴为“旋转轴”，不要想当然的认为这里的“轴”是基准轴（x，y或z轴），旋转轴可以取任意方向。这时候如果希望绕轴旋转30度，我们怎么知道该如何旋转呢？

我们首先要知道哪个方向为正，哪个方向为负，这样才能进行下一步操作。标准区分左手坐标系中的正向与负向的方式叫做“左手法则”。如何操作呢？首先明确一个前提，虽然旋转轴理论上是无限长的，但是我们还是认为它和基准轴一样有一个正方向和一个负方向；左手法则的使用方式：左手握住旋转轴，竖起拇指指向旋转轴正方向，正向旋转方向就是其余手指卷曲的方向；相同的操作方式在右手坐标系就是“右手法则”；如下图6，7

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image006.png)

图6 左手法则

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image007.png)

图7 右手法则

可以发现，在左手坐标系统中，从旋转轴正方向看下去，正向旋转方向就是顺时针方向；而在右手坐标系统中，从旋转轴正方向看下去，正向旋转方向就是逆时针方向；

左手坐标系与右手坐标系可以互转，最简单的方式就是将某一个基准轴的正方向和负方向调转；如果掉转了两个轴，相当于绕第三个轴旋转了180度，并没有坐标系的变化。

### 世界坐标系与物体坐标系

#### 世界坐标系

3D的世界坐标有三轴(x，y，z)，如图8：

#### 窗口与世界坐标

图8 窗口与世界坐标
世界坐标的Z轴垂直于视口平面。

#### 物体坐标系

每个3D元素都有自身坐标，在默认情况下，新创建一个3D元素时，该元素的自身坐标与世界坐标重合。下图新建一球（3D基本元素），该球自身坐标与世界坐标重合。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image009.png)

图9 自身坐标

当3D元素被移动或转动时，其自身坐标也跟着移动和转动。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E5%9D%90%E6%A0%87%E7%B3%BB%E5%92%8C%E5%90%91%E9%87%8F/images/image010.png)

图10 自身坐标相对世界坐标旋转（rotationZ=30）

将图9里的球的绕z轴旋转30度时就的到图2。图中黑线描出世界坐标。

### 坐标系转换

* 1. World Space（世界坐标）：
我们在场景中添加物体（如：Cube），他们都是以世界坐标显示在场景中的。
transform.position可以获得该位置坐标。

* 2. Screen Space（屏幕坐标）：
以像素来定义的，以屏幕的左下角为（0，0）点，右上角为（Screen.width，Screen.height），Z的位置是以相机的世界单位来衡量的。
Screen.width = Camera.pixelWidth
Screen.height = Camera.pixelHeigth
鼠标位置坐标属于屏幕坐标，Input.mousePosition可以获得该位置坐标，
手指触摸屏幕也为屏幕坐标，Input.GetTouch(0).position可以获得单个手指触摸屏幕坐标。
clip_image001

* 3. ViewPort Space（视口坐标）：
视口坐标是标准的和相对于相机的。相机的左下角为（0，0）点，右上角为（1，1）点，Z的位置是以相机的世界单位来衡量的。
clip_image002

* 4. 绘制GUI界面的坐标系：
这个坐标系与屏幕坐标系相似，不同的是该坐标系以屏幕的左上角为（0，0）点，右下角为（Screen.width，Screen.height）。
clip_image003

### 四种坐标系的转换

1. 世界坐标→屏幕坐标：
camera.WorldToScreenPoint(transform.position);
这样可以将世界坐标转换为屏幕坐标。其中camera为场景中的camera对象。

2. 屏幕坐标→窗口坐标：
camera.ScreenToViewportPoint(Input.GetTouch(0).position);
这样可以将屏幕坐标转换为视口坐标。其中camera为场景中的camera对象。

3. 窗口坐标→屏幕坐标：
camera.ViewportToScreenPoint();

4. 窗口坐标→世界坐标：
camera.ViewportToWorldPoint();

## 向量的理解

参考资料: [http://www.cnblogs.com/chrisfxs/p/5737173.html](http://www.cnblogs.com/chrisfxs/p/5737173.html)











