## 页签介绍

页签实际上是Toggle的基础上延伸出来的一种组合型组件，无论是在游戏中还是应用软件中，都有他的身影。下面的图即是它们的体现。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E9%A1%B5%E7%AD%BETabview/images/20160919171010.jpg)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E9%A1%B5%E7%AD%BETabview/images/20160919171130.jpg)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E9%A1%B5%E7%AD%BETabview/images/20160920104519.jpg)

页签的头，使用的是UITo孤寡老人组件来完成的，每个Toggle对应相应的内容使用相应的Panel或者UI容器来完成。

## 页签的制作

本节课将带领大家完成的效果如下。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E9%A1%B5%E7%AD%BETabview/images/20160920120404.jpg)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E9%A1%B5%E7%AD%BETabview/images/20160920120522.jpg)

1. 创建3个空游戏对象，命名为tagView,Tabs, Views。Tabs用于放置Toggle组件，Views用于放置每个Toggle对应的内容。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E9%A1%B5%E7%AD%BETabview/images/20160920130325.jpg)

2. 在Tabs中新建2个Toggle组件，使用Label显示Tab的名称。

3. 在Views游戏对象中，为每个Tab创建对应的内容，此处暂时使用Label显示一些文本，分别命名为View1， view2.

4. 在每个Toggle组件上添加Toggle Object或者Toggle Component组件，用来设置每个Toggle对应的内容。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E9%A1%B5%E7%AD%BETabview/images/20160920132156.jpg)

Avtive列表用于放置当前Toggle被选中时，需要显示的游戏对象，或者说选中时，激活游戏对象。

Deactive列表用于存放当前Toggle被选中时，不需要显示的游戏对象。

