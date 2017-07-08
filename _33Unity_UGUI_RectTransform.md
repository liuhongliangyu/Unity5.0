# 引语

UI元素有专门的RectTransform组件来描述元素的几何信息，继承于Transform，理解Anchors和Pivot后，将对我们有很大的帮助,下面是Inspector面板的属性图：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-22cced0431fed13f.png)

## Anchors锚点

我们首先需要认识Anchors。官网上的图片很好表达了Andhors的功能，请恕我实践下拿来主义。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-220e11e70a5def02.gif)

锚点全在中间的情况

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-0c15d344dc0dad1c.gif)

锚点全在右下角的情况

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-c2f23bcd628ef49d.gif)

锚点在两个角的情况

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-671094a181f26840.gif)

锚点分开的情况

善于观察的同学可能已经发现，不管什么情况，button的四个顶点到相应锚点的相对位置是不变的：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-daaf44f85a3e6000.png)

规律：button的四个顶点到相应锚点的相对位置是不变的

当4个锚点都在一起的时候，RectTransform会显示Pos X，Pos Y，Width，Height四个属性可供修改。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-dbe0f01f6d838000.png)

当4个锚点都在一起

当不在一起的时候，RectTransform可调整的属性会有变化。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-198c0e7bbc414831.png)

锚点不在一起的时候，Inspector中变化1

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-860dfe5e10e57a3b.png)

锚点不在一起的时候，Inspector中变化2

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-7f477aa3a395b010.png)

锚点不在一起的时候，Inspector中变化3

Anchors的Min和Max分别是正规化的值(从0到1)，表示占父RectTransform的百分比，下图中AnchorMin=(0.1,0.1) AnchorMax=(0.9,0.9)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-9f65e0d13aecc3be.png)

## Pivot，UI的中心点

UI元素的旋转和缩放是围绕pivot进行的。RectTransform组件中，Pivot属性是一个正规化的二维向量，用来描述中心点在本身矩形大小的位置。默认值为(0.5, 0.5)，即几何中心。

以上是RectTransform可视化的编辑属性，实际上RectTransform类的属性是怎样的？查阅RectTransform的官方文档如下：

### anchoredPosition

The position of the pivot of this RectTransform relative to the anchor reference point.

### anchoredPosition3D

The 3D position of the pivot of this RectTransform relative to the anchor reference point.

### anchorMax

The normalized position in the parent RectTransform that the upper right corner is anchored to.

### anchorMin

The normalized position in the parent RectTransform that the lower left corner is anchored to.

### offsetMax

The offset of the upper right corner of the rectangle relative to the upper right anchor.

### offsetMin

The offset of the lower left corner of the rectangle relative to the lower left anchor.

### pivot

The normalized position in this RectTransform that it rotates around.

### rect

The calculated rectangle in the local space of the Transform.

### sizeDelta

The size of this RectTransform relative to the distances between the anchors.

乍一看有点费解，这里有必要解释下：

anchoredPosition

可以理解为Pivot点相对于Anchor reference点的位置。Anchor reference点，我是这样理解的：当四个anchors点在一起的时候，这个点就是anchor reference点；否则这四个点的中心点就是anchor reference点。
照这个推理，anchorMax和anchorMin的值将影响anchoredPosition的值。具体还需要demo研究来确认。

但可以确定的是，当一个UI元素不需要自动拉伸行为时，用anchoredPosition + sizeDelta来设置位置和大小是比较方便的方法。

anchorMax、anchorMin和Inspector中的意义一致，需要注意的是，当UI元素不需要自动拉伸时，AnchorMax和AnchorMin是相等的。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_RectTransform%E8%AF%A6%E8%A7%A3/images/301341-3f848986df9d0568.png)

AnchorMin与AnchorMax
UI元素需要自动拉伸时，使用anchorMax、anchorMin + offsetMax、offsetMin来设置UI的位置及大小会比较方便。
其中，anchorMax.x == anchorMin.x，height会自动拉伸，width固定不变。
anchorMax.y == anchorMin.y，width会自动拉伸，height固定不变。


