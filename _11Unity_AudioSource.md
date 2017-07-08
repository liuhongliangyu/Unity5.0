# 引语

声音作为游戏中必不缺少的元素，能够通过不同的声音效果提升游戏的用户体验，接下来学习如何在Unity中播放声音

# Unity能够支持的音频文件格式。

Unity支持压缩的和原生的音频。任何类型的文件（MP3/Ogg Vorbis的除外），最初都以原生音频导入可以通过选择加载类型（Load Type）选择运行时Unity加载音频的方法。

Unity能够支持的声音格式

* AIFF 最适合短音效果。可以在编辑器中按需求压缩。

* WAV 最适合短音效果。可以在编辑器中按需求压缩。

* MP3 最适合较长的音乐曲目。

* OGG 压缩音频格式（与iPhone设备和某些Android设备不兼容），最适合较长的音乐曲目。

# 如何在Unity中播放声音?

在Unity中能够播放声音的前提是需要场景中同时具有以下三个组件:

* AudioListener

* AudioClip

* AudioSource

三者关系如下

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403174643.jpg)

说明:

* AudioClip 指需要播放的各种格式的声音文件。

* AudioSource 用于进行声音播放的组件，可以控制播放，暂停，音量调整等功能。

* AudioListener 用于接收AudioSource组件播放的声音，然后通过声卡进行输出。此组件通常会在创建场景时自动地被添加到Main Camera上。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403180007.jpg)

# [案例1]

利用Unity引擎播放声音文件。

1. 导入Unity一个支持的声音文件，会看到Project面板中的声音文件显示为波形。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403180452.jpg)

在右侧的Inspector面板可以对声音进行设置。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403180655.jpg)

如果应该声音不用于模块立体音效可以选择 Force To Mono 复选框，设定为单声道声音。

2. 创建一个空游戏对象，并命名为MyAudio，添加AudioSource组件，并将准备好的声音文件，拖动到AudioSource组件在面板上的属性AudioClip上。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403181021.jpg)

3. 点击编辑器上的测试按钮，运行，将会听到声音的播放。

在AudioSource组件的编辑器界面有些常用属性:

* AudioClip 需要播放的组件，需要播放哪个声音文件，拖动到此属性即可。

* Mute 静音开关,选择则无声音输出

* Play On Awake 此对象在生命周期中的Awake时便开始播放声音。

* Loop 控制声音是否循环播放，选中为循环播放。

* Volume 音量大小调节

* Pitch 用于调节音调，有点类似于调整声音播放的速度快慢，可以用于赛车游戏中，汽车引擎声音随车速有高低变化。

* Stereo Pan 立体声道调整，小于0偏左声道，大于0偏右声道。

这些属性在AudioSource组件的API中，都会有明确的属性与其对应。

# [案例2]通过鼠标控制音乐的播放。

1. 案例一的基础上，我们取消AudioSource组件的Play On Awake复选框。

1. 新建C#脚本MyPlayer.cs，并添加到MyAudio游戏对象上，在脚本中获取AudioSource组件，然后通过API查阅用于控制声音播放与停止的函数。

```C#
using UnityEngine;
using System.Collections;

public class MyPlayer : MonoBehaviour {

	/// <summary>
	/// 获取AudioSource组件
	/// </summary>
	private AudioSource au;
	// Use this for initialization
	void Start () {
		au = this.GetComponent<AudioSource> ();
	}

	// Update is called once per frame
	void Update () {
		//鼠标左健按下时，开始播放声音
		if (Input.GetMouseButtonDown (0)) {
			au.Play ();
		}
		//鼠标右健按下时，停止播放声音
		if (Input.GetMouseButtonDown (1)) {
			au.Stop ();
		}
	}
}
```

# [案例3]鼠标点击后，更换正在播放的声音文件

1. 新建场景，并创建一个空对象，命名为Music2。

1. 为Music2添加AudioSource组件，并将前面案例中的bgMusic音乐拖动到AudioClip属性上。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403181021.jpg)

3. 新建C#脚本 MyPlayer.cs并拖动到Music2游戏对象上.

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403190512.jpg)

4. 编写以下内容

```C#
using UnityEngine;
using System.Collections;

public class MyPlayer : MonoBehaviour {

	/// <summary>
	/// 获取AudioSource组件
	/// </summary>
	private AudioSource au;

	/// <summary>
	/// 拖动另一声音文件到此属性上
	/// </summary>
	public AudioClip Music2;
	// Use this for initialization
	void Start () {
		au = this.GetComponent<AudioSource> ();
	}

	void Update(){
		if (Input.GetMouseButtonDown (0)) {
			//将得到的Music2赋值给AudioSource使其播放
			au.clip = Music2;

			//播放声音
			au.Play();
		}
	}
}
```

# [案例4] 同时播放背景音乐及音效。

1. 参照案例1中的方式，播放一个背景音乐。

1. 编写脚本，声明另一个AudioClip类型变量 FxSound用于存储特效声音。

```C#
   //背景音乐播放时需要播放的声音
   pubilc AudioClip FxSound;
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/08_%E9%9F%B3%E9%A2%91%E7%B3%BB%E7%BB%9F/images/20170403191254.jpg)

3. 编写特效控制程序

```C#
 using UnityEngine;
  using System.Collections;

  public class MyPlayer : MonoBehaviour {

  	/// <summary>
  	/// 获取AudioSource组件
  	/// </summary>
  	private AudioSource au;

  	/// <summary>
  	/// 拖动另一声音文件到此属性上
  	/// </summary>
  	public AudioClip FxSound;
  	// Use this for initialization
  	void Start () {
  		au = this.GetComponent<AudioSource> ();
  	}

  	void Update(){
  		if (Input.GetMouseButtonDown (0)) {
  			//播放特效声音，并设定特效音量大小
  			au.PlayOneShot(FxSound);
  		}
  	}
  }
```


















