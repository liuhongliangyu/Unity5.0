## 引语

利用Avatar系统，我们可以通过对骨骼操控实现动画的重利用效果，这也是Mecanim系统中的动画重定向功能。

## Avatar工作原理

对于人类角色来说，都包含着相同或类似的骨骼。而Avatar，可以对角色中包含的骨骼结构或角色模型进行分析与识别，并与Mecanim中已有的标准人类骨骼进行对比，并进行标示它是一个接口，通过它可以被Mecanim系统所识别，成为一种可悲Mecanim系统所识别的通用的骨骼结构，并把一副骨骼的动作指定应用到另一幅雇个人中，即实现Retargeting重定向。

## 创建并配置Avarice

选中人物模型，在inspector面板中选择Rig（装备）标签。如图所示。其中，AnimationType（动画类型）属性分4种类型供其选择。分别是

* None（无动画类型）

* Legacy(老动画类型)

* Generic（一般的，通常的动画类型）

* Humanoid（人类的动画类型）

如果应用Avatar，则需要选择最后一个类型，即Humanoid类型选项。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_9.png)

选择Humanoid类型之后，则可以看到AVatar Definition（Avatar定义）属性选项。分为Create From This Model（为此模型创建Avatar）、Copy From Other Avatar（复制其他的Avatar）两种选项。选择第一项并Apply，确定后，则会自动创建Avatar。如果创建成功，则会在下面的Configure..（配置）按钮前有一个对勾，表示Avatar被创建成功 

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_10.png)

点击Configure按钮，我们可以图形化手动配置Avatar。Mecanim要利用Scene场景视图来显示骨骼图形界面。所以当点击Configure按钮后，Unity会提醒保存当前场景。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_11.png)

在Inspector面板中，Avatar以图形方式绘制显示在Mapping（绘图）映射图表标签中。其中圆形代表了人体骨骼的关节点。通过点击某个图形图标，可以选中不同部位的骨骼。而图形图标分为实线和虚线两种。虚线圆表示为Optional Bone（可选的骨骼），而实线圆则表示为Avatar必须要设置的骨骼。

在Mapping绘图标签中，有4个按钮分别代表了人物骨骼的4个不同的细节部位。Body（身体）、Head（头部）、Left Hand（左手）。Right Hand（右手）。

当骨骼匹配都正确时，则图案都为绿色，只有在骨骼匹配错误时，才会在错误的对应点显示为红色，并自动弹出一些错误提示。如图所示。这时开发者可以通过手动方式重新为其添加正确的骨骼 。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_12.png)

除了手动调整骨骼Avatar的骨骼匹配，Unity的Mecanim还为我们提供令了一些自动匹配方式：

* 选择Pose（姿势）属性下拉菜单中的Sample Bind-Pose（取样姿势绑定）选项。如图所示，

* 选择Mapping（映射）属性下拉菜单中的Automap（自动映射）选项。如图所示。

* 选择Pose（姿势）属性下拉菜单中的Enforce T-Pose（强制T-Pose）选项。如图所示。

* （可选）选择Mapping（映射）属性下拉菜单中的Save（保存）选项，对新的骨骼映射进行保存，这样可以为以后其他人物资源配置应用骨骼映射了。再应用的时候可以选择Mapping（映射）属性下拉菜单中的Load（加载）骨骼映射选项。

* 最后，不要忘记Apply应用一下。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_13.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_14.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_15.png)

## Avatar的Retargeting重定向

只有在通过Avatar处里过的骨骼(且必须为人类的骨骼)才能通过Retargeting重定向，即经过Avatar处理过的骨骼具有相同的或类似额骨骼结构，这样可以使骨骼（或者说不同的动画片段）在不同的角色中重用或互用。即A人物的骨骼或者说动画片段可以应用在B人物模型身上（甚至B人物身上可以没有任何动画片段或者有自己的动画片段都没关系）使之具有A人物模型身上的动画行为，反之亦可。

所以，当骨骼经过Avatar处理后，只需要对每个模型添加一个Animator Controller（动画控制器），则在播放游戏时不同的模则具有可相同的动画。如图所示。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_16.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_17.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_18.png)

## Avatar肌肉设定

除了正确匹配骨骼位置，还可以通过Muscles（肌肉）属性来微调骨骼的运动范围，从而使骨骼动画更加合理协调，避免在骨骼动画中出现身体叠加或者失真的现象。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/14_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Avatar%E7%B3%BB%E7%BB%9F/images/20170419_19.png)

如图所示，在Muscle Group Preview（肌肉组合预览）中，可以观察一系列多个不同骨骼组合的共同运动效果。

可以点击Reset All（重置所有）按钮来恢复成默认的预览。

而在Per-Muscle Setting（每个肌肉的设置）中，可以调整社体不同部位的单独骨骼肌肉拉伸范围，并对其微调设置。如果我们想恢复默认值，则可以点击最下面的Muscle下拉菜单，选择Reset（重置）选项来恢复。也可以在点击Apply应用之前，点击最下面的Revert（重置）按钮恢复。

最后一组设置为Additional Setting（附加设置）。可以微调骨骼的扭曲效果。

最后选择Apply应用，并选择Done（完成）按钮来保存微调设置并回到游戏场景中。








