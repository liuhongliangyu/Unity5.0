# 引语

在游戏中，显示的物品不能够在一屏显示全时，使用最频繁的组件便是ScrollRect.

## ScrollRect应用

【案例】使用UGUI 制作ScrollView滚动视图

1. 创建一个Canvas，在Canvas下创建一个Panel，命名为ScrollView，在ScrollView上添加组件Scroll Rect。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606150643718.png)

2. 在ScrollView下创建一个空物体命名为Grid，挂上GridLayoutGroup组件.

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606151911746.png)

3. 在Grid下创建一个Image，添加一个图片，然后复制N个，他们将自动排列，效果如下

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606152124362.png)

4. 添加拖拽，选中ScrollView，将Grid拖拽到ScrollRect组件的 Content 参数上

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606152324342.png)

5. 运行项目，现在可以拖动了，但是发现向各个方向都能拖动，我要的是上下拖动啊，现在需要设置ScrollRect 的参数。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606152521975.png)

说明:

* 选中Horizontal代表可以水平拖动

* 选中Vertical代表可以垂直拖动

再次运行,有竖直方向可以拖动了，但是还有问题，怎么拖拽都不能顺畅的滚动，

6. 设置 Grid 上 Gird Layout Group 组件上的参数

只说用到的参数，

CellSize 下的 X，Y 分别控制 Gird下Image的宽和高，在此都设置为 100

如果要控制Grid下Image 的宽高，必须要在此设置，直接设置Image 的宽高无效

Spacing 下的X， Y 分别控制 Image 的行间距和列间距

在此设置为 10， 10

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606153301130.pnghttps://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606153301130.png)

下面设置拖拽不流畅的罪魁祸首

选择Grid 看RectTransform的 width 和 Height

在此为 100， 100

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606153534806.png)

然后看Grid下10个Image，每个Image的宽高为 (100,100),也就是说Grid的宽高仅仅是一个Image的大小，所以导致Grid的范围不对

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606154914704.png)

下面计算一个Grid应该设置的宽高， 10 个Image，每个Image的宽高是 100,100， 行间距是10,

（100 + 10） * 10 = 1100；

现在设置Grid的宽高为 100， 1100

再次运行，已经能够比较顺畅的拖拽了。

第七步：设置ScrollView 的遮罩，给ScrollView添加 Mask组件

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606155535828.png)

通过调整ScrollView 的大小区域来控制显示区域

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/20_UI%E7%B3%BB%E7%BB%9F_UGUI%E4%B9%8B%E6%BB%9A%E5%8A%A8%E8%A7%86%E7%AA%97/images/20150606155730161.png)

















