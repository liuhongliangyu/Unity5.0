## 引语

在Unity引擎中，大致上可分为两大类动画控制系统，分别是Animation和Mecanim动画系统。

Animation是低版本中的动画控制系统。而Animator是Unity新的动画系统。Mecanim动画系统的核心组件.通过它能够实现对动画的重定向

## 模型导入的常见问题

### 1. 模型材质或纹理丢失

当模型中出现紫红色区域或模型没有纹理，很有可能是材质或纹理丢失。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404221335.jpg)

材质丢失

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404221425.jpg)

纹理丢失

当遇到材质丢失这种问题，找到相应材质，赋给模型便可解决。

当遇到纹理丢失，将纹理赋值给材质球，便可解决

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404221654.jpg)

### 2. 模型太小或太大

当将模型拖动到场景中时，会太小或太大，此时，可能会想到将模型通过缩放工具调整到合适大小，但是这种方法并不正确，正确地方式是通过模型导入设置中的Scale Factor项进行调整

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404221959.jpg)

## 动画的切割方法

将参考字两种的Animation动画素材导入到Unity项目中，选中Charactor.fbx文件，在Inspector面板中进行相应的设置

Rig标签设置如下：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404224403.jpg)

Animation标签设置如下：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404222353.jpg)

选中Import Animation项后，点击Apply按钮，将会出现如下界面。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404222505.jpg)

在Charactor.fbx同目标中，打开animations文件，此文件中记录着此模型各种动画开始帧和结束帧，（通常该文件会有动画制作人员提供），接下来，我们需要根据此文件内容进行动画切割。

选中Clips中的Take 001项，会出现以下界面。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404222744.jpg)

将Take001修改为idle，并将Start设定为0，End设定为30，然后点击底部的Apply按钮，并可以通过底部的预览窗口进行动画查看（如果没有此窗口，请点击最底部的横条）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404223604.jpg)

如果希望此动画能过循环播放，可以将Warp Mode设定为Loop。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404225403.jpg)

然后点击Clips下的“+”继续添加新的动画，指定开始与结束帧，点击Apply

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404223331.jpg)

通过上面的操作按Animations.txt文件内容切割动画。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404224102.jpg)

## 动画的控制

动画切割完成后，我们可以通过Animation组件提供的方法对动画进行控制。

将切割好动画的模型拖动到场景中，会发现模型上挂在的Animation组件，并且组件中的Animations数组中存放的刚刚切好的动画片段。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404225605.jpg)

## 案例1 动画切换

创建一个C#脚本MyAni，挂载到模型上，并编写以下脚本

```C#
using UnityEngine;
using System.Collections;

public class MyAni : MonoBehaviour {

	private Animation ani;
	// Use this for initialization
	void Start () {
		ani = this.gameObject.GetComponent<Animation> ();

	}

	// Update is called once per frame
	void Update () {
		if (Input.GetMouseButtonDown (0)) {
			//设定动画为循环方式
			ani.wrapMode = WrapMode.Loop;
			//将动画切换到walk
			ani.CrossFade ("walk");
		}
		if(Input.GetMouseButtonDown(1)){
			//设定动画为循环方式
			ani.wrapMode = WrapMode.Loop;
			//将动画切换到idle
			ani.CrossFade ("idle");
		}
	}
}
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/13_%E5%8A%A8%E7%94%BB%E7%B3%BB%E7%BB%9F_Animation/images/20170404230231.jpg)












