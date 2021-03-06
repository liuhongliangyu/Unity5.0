# 流程控制

# Unity脚本及常用的函数方法

## 一步函数：调用（Invoke）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img2/36/%E5%9B%BE%E7%89%8721.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img2/36/%E5%9B%BE%E7%89%8722.png)

* 在一个方法执行时调用另一个方法。

* 而被调用的方法或者其中的某些语句不是立刻执行，而是过一段时间后才执行。

* MonoBehaviour提供了两种异步方法:
 
* 调用（Invoke）
 
* 协程（协同，协同程序，Coroutine）

## 异步函数：调用（Invoke）

Invoke() 方法是 Unity3D 的一种委托机制
如： Invoke(“SendMsg”, 5); 它的意思是：5 秒之后调用 SendMsg() 方法；

Invoke() 也支持重复调用：InvokeRepeating(“SendMsg”, 2 , 3);
这个方法的意思是指：2 秒后调用 SendMsg() 方法，并且之后每隔 3 秒调用一次 SendMsg () 方法

使用 Invoke() 方法时注意：

* 1- Invoke(); 不能接受含有 参数的方法；

* 2- Invoke受ScaleTime影响,所以,ScaleTime变慢,Invoke也会对应变慢.而在 Time.ScaleTime = 0; 时,Invoke() 无效,因为它不会被调用到.

* 3- Invoke、InvokeRepeating是用CancelInvoke停止。

* 4- IsInvoking是检测是否调用了

* 5- CancelInvoke只能停止相应脚本上的Invoke。(没有参数是清除所有的Invoke,有参数是表示清除某个指定的Invoke)

* 6- 无论Inveoke所对应的物体active=false，还是enable=false，无法停止Invoke，除非Invoke所在脚本或所依附的gameobject被destroy。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img2/36/%E5%9B%BE%E7%89%8741.png)

异步函数：协程（Corouine）

协程介绍：

* 在主程序运行的同时,开启另一段逻辑处理,来协同当前的程序一同执行,处理.(协程并不是线程)

关于Unity中的协程:

* 所需要的函数类型需要一个返回的迭代器IEnumerator,需要函数中有挂起yield return

* 一个协同程序在执行过程中,可以在任意位置使用yield语句。yield的返回值控制何时恢复协同程序向下执行。

* Yield是一种特殊类型的Return(返回)语句,它可以确保函数在下一次被执行时,不是从头开始,而是从Yield语句处开始

//使程序在等待5秒后在执行

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img2/38/%E5%9B%BE%E7%89%8721.png)

## StartCoroutine、StopCoroutine、StopAllCoroutines:

* 1. StartCoroutine有两种传参芳法，一种是字符串，一种是IEnumerator，传字符串的只能传一个方法参数，传IEnumerator没有限制。

* 1. StopCoroutine只能停止用字符串传参开启的协程，并且使用字符串关闭,而用IEnumerator传参的要使用StopAllCoroutines。 StopAllCoroutines两种开启的都能关闭

* 1. 一旦gameobject的状态是unactive,协同就失效。包括脚本依附的gameobject的父gameobject，再次active也无法唤起协同

* 1. 组件enable状态无法暂停协程。

* 1. 一旦跳转场景（其实就是协同所在的脚本所依附的gameobject被删除，包括脚本被删除，gameobject整个被删除），协同马上停止。
 
* 1. StopCoroutine、StopAllCoroutines只能停止相应脚本上的协同，不能停止别的脚本上的协程，

例如脚本A上有协同a，StopCoroutine、StopAllCoroutines要写在脚本A上，如果想在脚本B停止协程a，应该在脚本A上封装一个停止的方法让脚本B调用。

* StartCoroutine(Move()); 等价于 StartCoroutine(“Move”);

对比，

* Invoke是在开启的时候给一个时间去告诉几秒后调用,而Coroutine是直接调用,在方法中去处理等待的时间,Coroutine在处理是时间上更加灵活

* Invoke将物体激活关闭,不会停止调用,

* Coroutine 将物体激活关闭, 将不再调用

Invoke不支持传参数,Coroutine支持

## SendMassage 发送消息

GameObject.SendMessageUpwards 向上发送消息

GameObject.BroadcastMessage 广播消息

Component.SendMessage 发送消息

* SendMessage是一个非常强大的消息推送机制

目的为: 只要调用了此方法,同时持有某个类的引用.则可以向这个类本身,或者其子类,或者其父类传递消息,而达到执行指定的某个函数方法，这个过程非常方便的实现了某个引用,从而大大简化了开发过程中的复杂程度

GameObject.SendMessage(string methodName)会搜索这个GameObject上所有的Component中所有叫做methodName的方法,并调用这些个方法，三种方法使用方式完全一样,只是使用用途,或者说使用对象有所不同，使用的方法利用反射的机制来检索所有游戏对象身上是否存在发送消息的目标,所以开销相对还是是比较大的，so,方法很强大,但执行效率并不高

注:

* 1- 此函数是跨语言的，例如Javascript可以调用C#的函数。

* 2- 如果GameObject本身有两个脚本，例如“NewBehaviourScript1”和“NewBehaviourScript2”，两个脚本内有同名函数，会两个函数都会执行一次。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8731.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8732.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8733.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8734.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8735.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8736.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8737.png)

## SendMessage 官方API手册小示例

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8741.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8742.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/07_%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6/img3/40/%E5%9B%BE%E7%89%8743.png)

## Application函数

* ▲ 属性:

* Application.loadedLevel //获取加载的关卡的索引(返回int类型当前关卡的索引值)

* Application.loadedLevelName //获取加载的关卡的名字(返回string类型当前关卡的名字)

* Application.levelCount //关卡数(返回int类型所有的可用的关卡总数)(添加的场景数)

* ▲ 方法:

* Application.LoadLevel(“Scene场景名称 or Scene场景index索引”); //加载关卡

* Application.OpenURL(“www.baidu.com”) //打开网址

* Application.CaptureScreenshot(“pic.png”); //截屏,截屏的图片默认保存在根目录下(项目文件夹下)

//eg:游戏暂停，并切换Scene场景（切换关卡）

```C#
if(time.timeScale >0 && input.getkeydown(keycode.escape)){
	Time.timeScale = 0;
	Application.LoadLevel (“Scene场景名称 or Scene场景index索引”);
}
```

* **注：菜单:File->Build Settings->Add Current->(勾选Scene场景)**

## 简单数据场景储存（玩家偏好）

1- 设置:(在一个Scene中)

* PlayerPrefs.SetInt(“life”,100);

* PlayerPrefs.SetFloat(“lev”,9.8f);

* PlayerPrefs.SetString(“name”,“zhangsan”);

注: 此方法可以跨Scene调用一些比较简单的数据

2- 读取(在另一个Scene中)

* PlayerPrefs.GetInt(“life”);

* PlayerPrefs.GetFloat(“lev”);

* PlayerPrefs.GetString(“name”);

