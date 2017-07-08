## 引语

对于模型动画的分割，不论是Animator还是Animation，在动画分割上稍有一些不同，但整个操作思路是一样的。

## 分割动画

导入一个角色资源，可能只有一个角色模型资源，也可能包含动画资源。动画资源也分两种情况：

1. 各个动画部分都是独立的

1. 所有的动画集成在一个动画片段中。

注：第2种情况，需要在导入资源之后手动分解成不同功能的动画片段。

## 动画分割案例

1. 选中角色资源，在Inspector面板中会显示Inspect Setting（输入设置）。

1. 在Animations动画标签中可以看到Clips动画片段。Clips就只有一个动画片段，叫Take 001.其动画预览范围为：0-330帧。播放下面预览窗口的播放按钮可以看到整个动画里包含2个动作行为。

1. 因为动画片段的原始帧范围为1-330，而不是0-330，则下面会显示“The clip range is outside of the range of the source take",表示片段的范围已经超出原始资源片段的帧范围。需要单击ClampRange（强制实行范围）按钮来剪切。

1. 根据需求单击加号来添加动画片段，并确定2个动画片段的帧范围，并命名对应的动画片段。idle为：1-240，walk为;300-330

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%8A%A8%E7%94%BB%E5%88%86%E5%89%B2%E4%B8%8E%E8%AE%BE%E7%BD%AE/images/cutanim.png)

## 动画片段设置

在Unity的Mecanim系统中可以对不同的动画片段进行动画融合和动画过渡等操作，这就要求需要有循环质量比较高的动画片段来保证动画效果。Mecanim提供了一些工具和属性，对于动画片段的循环进行监测和优化调整。

在Project面板中选中一个动画模型，在Inspector面板中的Animations标签下，可以选中一个动画片段，则在下面会显示针对此动画片段所对应的动画循环属性监测。在此属性编辑器中，提供了一些显示，来描述其动画片段的各种循环质量的参数。如图所示。

分别有四个属性设置：

* Loop Time，勾选这个选项之后，如果Animator处于播放这个动画状态时，在播完第一遍这个动画片段之后，会自动循环从开始帧再次开始播放动画，如此循环往复。

如果我们不勾选这个选项，例如Animator一直处于这个动画的状态，那么动画会定格在动画结束帧，直到我们通过Animator切花这个Animator状态机的状态，切换到其他的动画

Loop Pose用于控制动画循环播放时，从结束帧切换到起始帧时，动画的动作可以无缝的衔接上

Cycle Offset就是用于控制循环的时候起始帧偏移用的

* Root Transform Rotation 根旋转变换

* Root Transform Position（Y）根位置变换（Y）根节点位移信息（Y轴）

* Root Transform Rotation（XZ）根位置变换（XZ）根节点位移信息（水平面，XZ轴）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%8A%A8%E7%94%BB%E5%88%86%E5%89%B2%E4%B8%8E%E8%AE%BE%E7%BD%AE/images/20170415220437.jpg)

(注：Original是角色原始位置，Center of Mass为角色中心在y轴的投影位置）

以上4个属性分别匹配的非常好的时候（即动画的起始帧与结束帧比较吻合），右面对应的loop match会呈现绿色

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%8A%A8%E7%94%BB%E5%88%86%E5%89%B2%E4%B8%8E%E8%AE%BE%E7%BD%AE/images/jdfw.gif)

除了查看动画质量，还可以对动画片段做一些微调节，在此我们举2个例子

### [案例1]Root Tranfrm Position(Y)

根位置变换（Y）根节点位置信息（Y轴）应用

如图所示，在动画预览中，我们看到模型与地面保持有一点空间距离，这样会导致人物在游戏运行时浮空在游戏场景中。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%8A%A8%E7%94%BB%E5%88%86%E5%89%B2%E4%B8%8E%E8%AE%BE%E7%BD%AE/images/eb8de5a5-1bc3-4f72-aba2-222e4befc472.jpg)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%8A%A8%E7%94%BB%E5%88%86%E5%89%B2%E4%B8%8E%E8%AE%BE%E7%BD%AE/images/9a60e9da05d6.jpg)

我们可以调节Root Transform Position（Y）属性，勾选Bake Into Pose(烘焙到姿势中)选项，并调整Offset（位移）数据，使其贴附在地面上。

### [案例2] Root Transform Position（XZ）

根位置变换（XZ）根节点位置信息（水平面， XZ轴）

如图所示。在X轴方向上有一定的运动量。我们调整Offset偏移量，使Average Velocity（平均速度）属性在X轴的运动量为0.这样可以保证人物模型沿着X轴直线跑动而不产生角度便宜了。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%8A%A8%E7%94%BB%E5%88%86%E5%89%B2%E4%B8%8E%E8%AE%BE%E7%BD%AE/images/a31867b44044.jpg)














