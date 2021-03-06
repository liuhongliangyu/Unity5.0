# UnityAPI核心类

## 前言

在Unity中，游戏项目的控制与交互等功能是通过脚本编程来实现。脚本也是Unity一种组件，可以理解为是附加在游戏对象上，用于定义游戏对象行为的指令代码。通过脚本命令，开发者可以控制每一个游戏对象的创建、销毁，以及在不同情况下发生的一定的逻辑关系,在不同的游戏物体上创建不同的脚本,能够让每个游戏物体都产生不同的行为,进而按照项目需求实现一个预期的交互效果。脚本开发是项目的核心部分.是贯穿整个项目开发中最大,最重要的内容.在Unity引擎项目开发中,脚本好比人的大脑和神经网络,贯穿和控制着人的四肢,五脏六腑,意识形态.我们经常用到的已经存在的功能组件实际上也都是由脚本语言封装而成的.

## 介绍C#脚本: 脚本也是一种组件

脚本的分类. 为何选择C#脚本.

在Unity中，目前可以使用三种类型的脚本，分别为：JavaScript、C#，一般讲，在国内的商业开发中，使用C#语言的比例最大。C#本身有很多强大的语言特性，相对更适合深入开发，并且很多优秀的Unity第三方插件也都是用C#开发的。

## 如何学习Unity的API

在.NET运行环境中,我们也会经常使用一些提供好的API方法,例如Console类中的WriteLine(),ReadLine(),Math类中的,Sin(),Cos()等等方法,从而帮助我们编写程序时不必自己去写这些功能或者算法,那在Unity中,我们继承了MonoBehavior类之后,Unity也给我们提供了各种各样强大的方法,这些方法存在于MonoBehavior类中或者它的父类中,使用这些方法,能让我们在开发的过程中省去了很多代码,这也是除去引擎自带的各种组件,资源等使用这个引擎的重要原因之一.

（通过C#渐渐引入UnityAPI的含义);

* 1- Unity软件安装目录中预制的手册,可从Unity引擎中打开

* 2- Unity官方在线手册: [http://docs.unity3d.com/ScriptReference/index.html](http://docs.unity3d.com/ScriptReference/index.html)

* 3- Unity圣典在线手册: [http://game.ceeger.com/search/](http://game.ceeger.com/search/)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%871.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%873.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%872.png)

## Unity3D核心类

看脑图,看API,了解继承关系：

* Object -> Component -> Behavior -> MonoBehavior

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%876.png)

### MonoBehaviour概述:

MonoBehaviour 表示一个单一的行为。Unity中用户对游戏对象的操作被分割成若干个单一行为。每个单一行为都作为一个MonoBehaviour类来封装。再生成每个MonoBehaviour类的实例，并作为组件嵌入游戏对象。然后按照一定的顺序（从下到上）调用每个对象的重载方法来实现游戏对象的全部行为。

### 创建:

在菜单Assets->create中选择C# script创建一个脚本类。Unity规定：这些类都必须继承自MonoBehaviour。javascript 的脚本类自动继承MonoBehaviour，c#脚本类必须显式继承这个类。(如果没有继承MonoBehaviour,则不能挂在到项目中游戏对象之上)

#### 特别之处:

继承自MonoBehaviour的类，不需要自己创建它的实例，也不能自己创建（如 new 类名）。
因为所有从MonoBehaviour继承过来的类，unity都会自动创建实例，并且调用被重载的方法，如我们经常用到的Awake,Start, Update等。
而普通类，就可以用new来创建实例了。

### 创建脚本

* 1- 默认名称为“NewBehaviourScript”

* 2- 选中脚本后,则可以在Inspector面板中预览

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%8731.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%8732.png)

### 脚本默认内容

默认有Start和Update方法,是Unity内置的event事件响应函数,分别代表:

* Start: Unity创建时运行初始化的函数，理解为构造函数的性质,但是我们不可以用构造函数,因为无法识别所处生命周期的位置

* Update: 以及项目运行之中,每一帧都会在反复调用的函数，理解为放电影的每一个帧动画

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%8741.png)

### 请课下查阅百度百科FPS 深入理解Update方法

http://baike.baidu.com/link?url=WBwz-Fd-1CG90EJyfax30UB6WvsAhgJLowPIE9C0ByLr-o3iwQnDvvL_cVuJDIi0g1Zg9U5GPB2hM65SXRQf_K

### 修改脚本模板

* 1- 默认有Start和Update方法

* 2- 若修改默认方法的模板:

安装Unity引擎目录下 -> Editor -> Data -> Resources -> ScriptTemplates.文件夹内有一个“81-C# Script-NewBehaviourScript.cs.txt”文件,可以用第三方工具“Notepad/Atom..”打开,以便更美观的格式观看模板代码或修改

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%8751.png)

#### 第一个Unity C#脚本 - Hello Unity

* 注意：在Console控制台双击日志内容可以跳转到脚本对应的代码行上面

```C#
void Start ()
  {
      print("Hello Unity!");
      Debug.Log("Hello Unity!")
  }
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%8762.png)

#### 脚本创建与调试 - Console控制台

* 菜单导航栏 -> Window -> Console (Ctrl+Shift+C)

解释:

* Clear: 清除.点击此按钮清除所有日志显示内容

* Collapse: [kə’læps] 收缩,折叠.将所有重复的日志内容折叠起来

* Clear on Play: 运行时清除.即: 每次项目重新运行时,将会重置显示内容

* Error Pause: [pɔːz] 错误暂停.当脚本中出现错误的时候,游戏暂停

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%8781.png)

#### Debug日志函数

Debug与print方法的不同,就是它还可以打印在控制台提示信息

注意：

* 1- 不同级别的日志对应的图标不一样

* 2- 在Unity引擎左下方也会显示最后一条日志内容

* 3- Console控制台窗口右上角的3个按钮可以过滤掉不同种类的日志信息

* 4- 如果代码语法错误等,也会报错,且项目不会正常运行,直到语法修改通过为止

```C#
void Start ()
  {
      Debug.Log("Log");           //普通输出
      Debug.LogWarning("Warning"); //报警告的方法
      Debug.LogError("Error");   //报错的方式
}
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/%E5%9B%BE%E7%89%8792.png)

#### C#脚本几个规则

在使用C#脚本编写时需要注意以下几个规则：

* 1- 任何脚本都必须依托于场景内的物体,即:必须绑定到Hierarchy面板中的物体列表身上才能够被执行

* 2- 凡是添加到游戏对象上的脚本都要继承MonoBehaviour类，否则脚本无法添加到物体上。我们添加脚本的时候，Unity也会自动帮助开发者完成继承的代码。

* 3- 而创建的C#脚本名称要和脚本中的类名一致。!!!!!!!!!!

* 4- Unity脚本中用Start或Awake函数来初始化，避免使用构造函数，因为Unity里无法确定构造函数何时被调用。

* 5- Unity不支持C#的自定义命名空间。

* 6-在Unity运行游戏时修改代码后,要将Unity结束运行在重新运行

* 7-注意Start和Update方法大小写!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

#### Unity脚本及常用的函数方法

##### 相同的变量不同的修饰符

相同的变量不同的修饰符 与 是否可见(在Inspector面板中显示出变量名称及对应数值):

* 1- 没有修饰符代表private类型

* 2- 只有用public类型的变量,才能在Inspector面板中对数值序列化

* 3- [SerializeField]可以把本a不可以在Inspector面板中显示的变量显示出来

* 4- [HideInInspector]可以把本可以在Inspector面板中显示的,已经被序列化的变量隐藏起来

```C#
public class NewBehaviourScript : MonoBehaviour {

    int num1;
    private int num2 = 100;
    public int num4;
    public int num5 = 100;

    [SerializeField]
    private int num6;

    [HideInInspector]
    public int num7;
  }
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/3/%E5%9B%BE%E7%89%8722.png)

#### 各种变量的声明与显示效果

注意:

* 1- 根据变量的类型的不同,在Inspector面板中会对应以不同的样式显示.

* 2- 在Inspector面板中修改数值时,可自动计算该类型的取值范围.如超出了(大于)int类型的取值范围,数值会自动变为2147483647,也就是int类型的最大值

* 3- 几何变量后面专题模块会具体介绍.分别代表了二维数组-四维数组,或欧拉角度,旋转角度等.

* 4- 最后2组为引用类型,可具体指定在场景中的具体的游戏对象或脚本.

* 5- 指定脚本类型时,必须要指定的脚本在场景中存在.即: 必须在场景中有物体挂着这个要指定的脚本

* 6- 在脚本中为变量在初始化时赋值默认值,则可以在Inspector面板中显示出来

* 7- !!!如果在Inspector面板中为某个变量赋值再次赋值,则项目运行时,以在Inspector面板中赋的值为准(脚本中只是初始化时的默认值)

这点经常容易出错,如果再次修改了脚本中的默认值,则需要在Inspector面板中点击reset键!!!!!

```
public class NewBehaviourScript : MonoBehaviour {
//之前我们常用的数据类型
public int num1;
public float num2;
public byte num3;
public string name;
public bool isChecked;

//Unity中将会常用到的数据类型..
public Vector2 v2;
public Vector3 v3;
public Vector4 v4;
public Quaternion q1;
public GameObject obj; //等等…

//声明一个类类型的实例,当然,首先在Project工程中存在这个脚本
public Demo scriptDemo;
}
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/3/%E5%9B%BE%E7%89%8732.png)

### enum枚举类型的声明

注意:

* 枚举类型也是一样,如果需要在Inspector面板中显示出来,需要现创建一个枚举类型的数据,再定义一个枚举类型的变量

* 枚举是可以创建在类外的,

```C#
public enum Week
  {
      星期一, 星期二, 星期三, 星期四, 星期五, 星期六, 星期日,
  }

public class NewBehaviourScript : MonoBehaviour {
  public enum Sex
  {
      男,女
  }

  public Week week;
  public Sex sex;
}
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/3/%E6%9E%9A%E4%B8%BE.png)

## 整体类型的声明

* 1- 在Project中可以创建一个class类,这个类可以不需要继承MonoBehavior,但是也就同时不能挂载到游戏物体上也失去了使用Unity中各种生命周期方法的权限,这种类我们可以用来存储数据/处理项目框架,或者作为一个管理类,因为这些类都是不需要使用生命周期的

* 2- 如果想对整体类型中所有的变量在Inspector面板中显示出来,则需要添加[System.Serializable]

* 3- [System.Serializable]表示对后面紧跟着的class类中所有的变量在Inspector面板中序列化

* 4- 必须在最后要实例化声明的整体类型

```C#
public enum LX
{
    战士,法师,刺客,坦克,射手
}
[System.Serializable]
public class Player{
    public LX lx;
    public int lv = 0;
    public string name;
    public int damage;
}


public class zhanshi : MonoBehaviour {
    public Player p1;
	void Start ()
	{
        print(p1.lv);
		print(p1.lx);
        print(p1.name);
        print(p1.damage);
	}
}


public class fashi : MonoBehaviour {

    public Player p2;
	void Start ()
	{
        print(p2.lv);
		print(p2.lx);
        print(p2.name);
        print(p2.damage);
	}
}
```

## Unity核心类与生命周期

下图为Unity中核心生命周期的函数,也就是在一个脚本中,这些函数都会被执行,只不过执行的顺序以及被被执行的方式有一些区别,有些是会自动调用的,有些则需要在达成一些条件下才会被调用

先参看截图

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/5/%E5%9B%BE%E7%89%8721.png)

### 执行先后顺序是如何的呢？内部是如何进行管理的呢？

我们编写代码的类都继承于MonoBehaviour的类，根据项目需求我们会写有很多个方法，于是乎必然要问出一个问题：这么多个方法，执行先后顺序是如何控制的呢？

* 1- In Editor Mode: 在运行项目之前,在编辑状态下,当第一次将Component组件添加到物体之上时将自动被调用的函数

* 2- 在运行项目后,只要绑定脚本的物体存在于场景中,Awake就会被执行一次的,且不论脚本是否被Disable隐藏掉.

* 3- Update是在系统每一帧都会被调用,只是每一次循环调用时都是Update先于LateUpdate.而FixedUpdate是基于物理时间的运算,即有一个自己固定的频率

* 4- Rendering是关于渲染的

* 5- GUI是关于UI界面绘制相关的

* 6- Teardown[’tɛr,down]是卸下,拆毁的意思.即当物体不可见或者脚本被销毁时所要最后执行调用的部分

### 下边列举了一些经常在开发过程中经常会用到的核心生命周期函数

* Reset：在用户点击检视面板的Reset按钮或者首次添加该组件时被调用。此函数只在编辑模式下被调用。Reset最常用于在检视面板中给定一个默认值。 

* Awake：用于在游戏开始之前初始化变量或游戏状态。在脚本整个生命周期内它仅被调用一次,并且即使脚本被禁用,它也会执行.Awake在所有对象被初始化之后调用，所以你可以安全的与其他对象对话或用诸如GameObject.FindWithTag()这样的函数搜索它们。每个游戏物体上的Awake以随机的顺序被调用。因此，你应该用Awake来设置脚本间的引用，并用Start来传递信息,Awake总是在Start之前被调用。它不能用来执行协同程序。 

* Start：仅在Update函数第一次被调用前调用。Start在behaviour的生命周期中只被调用一次。Start总是在Awake之后执行。

* FixedUpdate：固定帧更新，在Unity导航菜单栏中，点击“Edit”–>“Project Setting”–>“Time”菜单项后，右侧的Inspector视图将弹出时间管理器，其中“Fixed Timestep”选项用于设置FixedUpdate()的更新频率，更新频率默认为0.02s。 

* Update：帧更新，用于更新逻辑。每一帧都执行，处理Rigidbody时，需要用FixedUpdate代替Update。例如:给刚体加一个作用力时，你必须应用作用力在FixedUpdate里的固定帧，而不是Update中的帧。(两者帧长不同)FixedUpdate，每固定帧绘制时执行一次，和update不同的是FixedUpdate是渲染帧执行，如果你的渲染效率低下的时候FixedUpdate调用次数就会跟着下降。FixedUpdate比较适用于物理引擎的计算，因为是跟每帧渲染有关。Update就比较适合做控制。 

* LateUpdate: 在所有Update函数调用后被调用，和Fixedupdate一样都是每一帧都被调用执行，这可用于控制脚本逻辑的执行顺序。例如:当物体在Update里移动时，跟随物体的相机可以在LateUpdate里实现。不然如果物体移动和相机跟随都写在Update就有可能出现获取不到已经更新好的角色位置.

#### Awake() VS Start() - 小示例

```C#
void Awake()
{
    print("Awake");
}

void Start()
{
    print("Start");
}
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/6/%E5%9B%BE%E7%89%8732.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/6/%E5%9B%BE%E7%89%8733.png)

#### 生命周期函数执行顺序如下：

Reset -> Awake -> OnEable -> Start -> FixedUpdate -> Update-> LateUpdate -> OnGUI -> OnDisable -> OnDestroy(面试会问的类型)

#### Awake() VS Start()总结

##### Awake()：

* 1- Awake在脚本整个生命周期内像构造函数一样仅被调用一次

* 2- 初始化函数,在项目运行时,系统自动调用

* 3- Awake在所有对象被初始化之后调用,所以可以安全的与其他对象对话或使用诸如GameObject.FindWithTag()这样的函数搜索它们

* 4- 不论脚本是否激活状态,Awake都会被调用(但如果绑定的物体没有激活,将不会调用Awake函数)

* 5- Awake总是在Start之前被调用

* 6- 它不能用来执行协同程序

##### Start()：

* 1- Start在脚本整个生命周期内仅被调用一次

* 2- Start总是在Awake之后被调用

* 3- Start总是在Update等等函数运行之前被调用

* 4- 必须在脚本被激活时才能被调用

注:
建议一般在Awake方法中创建游戏对象/初始化字段数值。在Start方法中去获取游戏对象/数值，这样就可以确保万无一失了。

### 修改C#脚本执行顺序

小提问：如果两个脚本中在Awake方法里都做了事情，但是这两件事也有前后顺序怎么办？例如在一个脚本中的Awake方法引用另外一个脚本中Awake方法中初始化字段的变量(不一定会引用的到,因为执行顺序不确定,有可能是初始化的脚本先执行,就会引用得到,有可能不是先执行)

```C#
public class Test01 : MonoBehaviour {

    public int sum = 0;
	void Awake () {
        sum = 100;
	}
}
```

```C#
public class Test02 : MonoBehaviour {

    public Test01 t1;
    void Awake()
    {
        print(t1.sum);
    }
}
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/6/%E8%84%9A%E6%9C%AC%E6%8E%92%E5%BA%8F.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/6/0.png)
          
菜单导航栏 -> Edit -> Project Settings -> Script Execution Order

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/7/%E5%9B%BE%E7%89%8741.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/6/1.png)

#### Update() VS FixedUpdate() 总结

##### Update()：

* Update是正常帧更新.会在每一帧调用一次

* 2- 帧长时时在改变

* 3- 一般用于非物理的运动(比如使一个物体匀速运动)

##### FixedUpdate()：

* FixedUpdate是固定帧更新,会在每个固定的时间频率调用一次函数

* 帧长是固定的(默认为0.02秒),不是时时改变的

* 一般用于物理的运动(比如控制一些诸如Rigidbody,Collier等物理相关组件)
(物理引擎中关于物理的行为运动都是根据固定的时间来计算的)

注:

* 1- 两者帧长不同

* 2- FixedUpdate 固定帧长,可以手动设置

* 3- Update就比较适合做控制

* 4- LateUpdate与Update方式一样,唯一不同的是

LateUpdate,在每帧Update执行完毕调用，他是在所有update结束后才调用

##### Update() VS FixedUpdate() - 小示例

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/7/%E5%9B%BE%E7%89%8731.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/7/%E5%9B%BE%E7%89%8732.png)

#### 调整FixedUpdate调用时间

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/7/%E5%9B%BE%E7%89%8723.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/04_%E6%A0%B8%E5%BF%83%E7%B1%BB%E4%B8%8E%E7%BB%84%E4%BB%B6%E4%BD%9C%E7%94%A8/img/7/%E5%9B%BE%E7%89%8722.png)

### 补充: Unity3d之MonoBehaviour的响应事件

下边列举了一些在开发过程中经常会用到的响应函数,这些函数会在达到某些条件时自动被调用,并且这些函数不属于生命周期的函数,即使脚本被禁用,在脚本中写的这些方法依然会在达到条件时执行,并且,脚本能否被禁用(是否在组件上显示打钩选项,取决于你当前的脚本中是否有一个生命周期的函数),那么很显然,这个意思就是说如果你的脚本中不存在生命周期的函数,你禁用脚本也没有什么意义.因为响应函数是不会被脚本是否禁用所影响.Awake是特例.即使脚本禁用,它也会被执行.现在可以进行一下简单的了解,后期会在碰撞/触发器,物体/组件的激活隐藏中详细的讲解

* OnMouseEnter：当鼠标进入到Collider(碰撞体)中时调用OnMouseEnter。

* OnMouseOver：当鼠标悬浮在Collider(碰撞体)上时调用OnMouseOver .

* OnMouseExit：当鼠标移出Collider(碰撞体)上时调用OnMouseExit。

* OnMouseDown：当鼠标在Collider(碰撞体)上点击时调用OnMouseDown。

* OnMouseUp：当用户释放鼠标按钮时调用OnMouseUp。

* OnMouseUpAsButton：OnMouseUpAsButton只有当鼠标在同一个或Collider按下，在释放时调用。

* OnMouseDrag：当用户鼠标拖拽Collider(碰撞体)时调用

* OnTriggerEnter：当Collider(碰撞体)进入trigger(触发器)时调用

* OnTriggerExit：当Collider(碰撞体)停止触发trigger(触发器)时调用OnTriggerExit。

* OnTriggerStay：当碰撞体接触触发器时，OnTriggerStay将在每一帧被调用。

* OnCollisionEnter：当此collider/rigidbody触发另一个rigidbody/collider时，OnCollisionEnter将被调用。

* OnCollisionExit：当此collider/rigidbody停止触发另一个rigidbody/collider时，OnCollisionExit将被调用。

* OnCollisionStay：当此collider/rigidbody触发另一个rigidbody/collider时，OnCollisionStay将会在每一帧被调用。

* OnEnable：当对象变为可用或激活状态时此函数被调用。

* OnDisable：当对象变为不可用或非激活状态时此函数被调用。

* OnDestroy：当MonoBehaviour将被销毁时，这个函数被调用。

## 总结

C#脚本在Unity中的作用.在继承Monobehavior之后和在.net中的一些区别(在继承Monobehavior之后,这个类就最好不要使用new来创建它的实例了,因为无法确定何时调用它的构造函数)
Unity圣典的使用方式(以后解决问题的好帮手)
访问修饰符在修饰字段时面板的不同表现(public 可以在面板指定,private不会再面板显示)
脚本/语句执行顺序的更改方式, 使用脚本排序或者 在响应函数中有所体现 (Awake总是会比Start先执行)
