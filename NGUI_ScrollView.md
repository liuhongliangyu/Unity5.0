## 滚动视图介绍

通常要显示的内容，不能一屏显示的，我们可以将显示的内容采用滚动的形式显示，这样的效果实现，在NGUI中使用ScrollView组件进行实现。

下图表示一个例子。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E6%BB%9A%E5%8A%A8%E8%A7%86%E5%9B%BEScrollView/images/20160919192326.jpg)

## 滚动视图的制作

* 1. 创建一个Panel作为整个滚动区域的容器，并添加上ScrollView组件

UIPanel重要属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E6%BB%9A%E5%8A%A8%E8%A7%86%E5%9B%BEScrollView/images/20160919202504.jpg)

* cs Alpha:面板的透明度

* Depth：面版在所有UI上的层次等级

* Clipping：面板剪切 None（无剪切效果）

* texture Mask：蒙版剪切

* Soft Clip:软剪切，有边缘模糊效果

* Constrain But Dont Clip：显示所有内容，但是是剪切区域存在

UIScrollView重要属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E6%BB%9A%E5%8A%A8%E8%A7%86%E5%9B%BEScrollView/images/20160919202943.jpg)

```
movement 移动方向
Horizontal 水平
Vertical 垂直
Unresticted 无限制
Custom 自定义水平x和垂直y滚动范围

Drag Effect 内容拖动时候显示的效果
Scroll Wheel Factor：使用鼠标进行滚动时，滚动时候的因子
Momentum Amount：快速滑动时产生的冲力
Restrict Within Panel：在面板里进行约束
Cancel Drag if Fits：如果有组件适应了面板的大小，取消组件在面板里的拖动
Smooth Drag Start：平滑拖动
IOS Drag Emulation：在苹果上仿真滑动效果
Scroll Bars：在进行拖动时，可以加入一个Scroll Bars来控制或者显示进度
```

* 2. 新建一个Empty，命名为UIGrid，作为滚动小项的容器，并添加UIGrid组件，利用UIGrid的排列方式使每项内容整齐排列。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E6%BB%9A%E5%8A%A8%E8%A7%86%E5%9B%BEScrollView/images/20160919203702.jpg)

UIGrid重要属性

```
cs Arrangement：表格的显示方向 
Sorting：对表格内的内容进行排序，Alphabetic（以字母顺序排序），Horizontal（水平方向进行排序）， Vettical（垂直方向进行排序），Custom（自定义的排序） 
Column Limit 限定每行的列的个数 
Cell Widht：单个显示的宽度 
Cell Height：单个显示的高度 
Animate Smoothly：使用平滑动画过度效果 
Keep Within Panel：保持在一个面板里显示 
```

* 3. 在UIGrid下创建Sprite，显示一副图片。作为滚动区域的列表项，在列表项上添加UIDragScrollView组件和BoxCollider，并通过Ctrl+D复制多个。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E6%BB%9A%E5%8A%A8%E8%A7%86%E5%9B%BEScrollView/images/20160919202342.jpg)

* 4. 运行进行测试，即可以实现滚动区域的拖动。
