## Mecanim动画系统简介

Unity 4.0于2012年11月15日正式发布，该版本最大变化之一就是引入了新动画系统——MecAnim，通过MecAnim新的动画系统，开发者可以非常方便地实现角色的各种动画的控制。

Mecanim具有以下特征:

* Mecanim动画系统是通过Avatar这个代理来实现设置角色动画中的骨架和蒙皮的。

* 开发者可以利用角色动画的重定向功能（Retargeting），将其他的任意动画动作绑定到开发者所指定的任何角色模型上，使得被绑定的角色也具有指定的动画功能，从而实现动画动作的可重复利用，极大提高游戏的开发效率。

即：Avatar可以识别角色中的骨骼结构、包含的动画，并通过Retargeting操作应用的其他的模型中。

* 在处理人类角色动画时，开发者可以使用动画状态机来处理各个不同动画之间的过渡和各种逻辑。

* 可以通过图形界面的方式很方便的来实现，而不必用脚本去一点点实现一些逻辑操作。

* 我们还可以通过身体遮罩的方法来处理和改变角色身体上不同部位的一些动画行为，而不必修改动画本身资源。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415210555.jpg)

## 如何应用Mecanim动画系统

当将一个人物模型文件（*.fbx或*.obj）导入到Unity中，选中人物模型，在Inspector面板中选择Rig标签。如图所示

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415212541.jpg)

其中，Animation Type（动画类型）属性分4中类型供其选择:

* None(无动画类型)

* Legacy（老动画类型）

* Generic（一般的，通常的动画类型）

* Humanoid（人类的动画类型）

请选择Humanoid并点击Apply。Mecanim会尝试匹配已有的骨骼结构和Avatar的骨骼结构。大多数情况，它通过分析刚体的骨骼结构自动匹配。

如果匹配成功，你会在Configure...菜单旁边看到一个复选框（如下图）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415212919.jpg)

成功匹配的同时，会添加一个Avatar子资源到FBX资源，您在project视图里面可以看到它。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415213046.jpg)
![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415213046.jpg)

左图：不带Avatar子资源的模型  右图：带Avatar子资源的模型

如果Mecanim没能创建Avatar，您会在Configure按钮旁边看到一个十字叉，不会添加Avatar子资源。此时，您需手动配置Avatar。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/noavatar.png)

## 配置Avatar

Avatar是Mecanim的一个如此重要方面，他需要被配置地符合你的模型。因此不论自动Avatar床键失败还是成功，你都需要进入Avatar配置模式来确保你的Avatar是有效且合适低配置了。你的角色骨骼匹配Mecanim的预定义骨骼结构并且模型是T字形姿势是非常重要的。

如果 自动Avatar床键失败，你讲会看到一个叉号出现在Configure按钮旁边。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415213616.jpg)

如配置成功，将会看到Configure...旁边出现一个对号

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415213736.jpg)

在这里，成功仅仅意味着需要的骨骼被匹配上了，但是为了获得更好的结果，你可能会想也匹配上可选的骨骼以及让模型进入一种合适的T字姿势。

当你进入Configure按钮，编辑器将会问你是否保存场景。之后进入Configure模式，场景视图用来单独显示指定模型的骨骼，肌肉和动画信息，不显示场景的其他部分。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415213917.jpg)

一旦你保存了场景，你就会看到一个带有骨骼映射的新Avatar配置检视器。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415214009.jpg)

检视器显示哪些骨骼是需要的还有哪些骨骼是可选的-可选的骨骼运动可以自动用差值计算出来。为了让Mecanim产生有效的陪，你的骨架需要至少含有必须的骨骼在适当的位置。为了提高查找匹配Avatar的机会，可以使用反应身体部位的命名你的骨骼（像“LeftArm” “RightFoream”这样的名称都是合适的）。

如果模型没有产生一个有效的匹配，你可以手动按照类似Mecanim内部的处理方式做一下：

1. Sample Bind-pose:采用绑定姿势（尝试让模型接近它建模时候的姿势，一个合理的最初的姿势）

1. Automap：自动映射（从最初的姿势创建一个骨骼映射）

1. Enforce T-pose 强制T字姿势：强制让模型更接近T字姿势，这是Mecanim使用的默认姿势。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415214219.jpg)

如果自动映射（Mapping->Automap）完全或者部分失败，你可以通过从场景或者体系结构视图拖拽它们来赋值到骨骼。如果Mecanim认为骨骼合适，它会用绿色在Avatar检视器中显示，否则会以红色显示。

最后如果骨骼被正确赋予了，但是角色不是在正确的姿势，你将会看到消息“Character not in T-Pose（角色不是在 T字姿势）”。你可以尝试Enforce T-pose(强制T字姿势)或者旋转余下的骨骼到T字姿势。

### 人体模板（human template）

你可以用“人体模板文件”（扩展名.ht)的形式保存雇个人到你Avatar骨架的映射到磁盘上，你可以在任意角色上重用这个映射。这个非常有用，比如，如果你的动画使用一致布局和命名约定到所有的骨架上但是Mecanim不知道如何解释它。你可以为模板载入.ht文件，这样手动重映射只需做一次。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animator%E5%9F%BA%E7%A1%80/images/20170415214348.jpg)










