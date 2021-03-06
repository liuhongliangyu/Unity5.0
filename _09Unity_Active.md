# 物体/组件激活隐藏

# Unity脚本及常用的函数方法

## 隐藏/是否激活 物体or组件 之 隐藏

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img2/20/%E5%9B%BE%E7%89%8722.png)

### enabled 小示例

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img2/20/%E5%9B%BE%E7%89%8731.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img2/20/%E5%9B%BE%E7%89%8732.png)

说明:

1- 当把Cube物体拖放到脚本中MeshRenderer属性中时,Unity会自动识别并获得Cube中的Mesh Renderer组件是控制一个物体是否在屏幕上渲染或显示，而物体实际还是存在，只是相当于隐身，而物体本身的碰撞体还依然存在的。(相当于对指定组件的勾选掉.如图把Mesh Renderer组件的隐藏)

## 隐藏/是否激活 物体or组件 之 激活

区别：

2- 是否激活游戏对象:gameObject.SetActive()//是否在场景中停用该物体 在你gameObject.SetActive =false中 则你在场景中用find找不到该物体

注: 在Unity中,设置是否激活是有层级父子关系的

gameObject.SetActive(true); //激活游戏物体

gameObject.SetActive(false); //禁用游戏物体

注：一旦物体被隐藏（gameObject.SetActive(false)）后，则无法通过gameObject.SetActive(true)再显示出来， 因为一旦被false,表示这个物体已经不在场景中了,用代码 GameObject.Find()也找不到的,且无法用this.gameObject.SetActive(true)来恢复。即：物体被设置为不活跃的了。
解决办法：

* 1) 写个脚本(不要绑定在要隐藏的游戏对象上),在脚本中持有要隐藏游戏对象的引用,通过这个游戏对象引用来显示或隐藏该物体。

* 2) 可以给此物体加一个父物体,通过父物体去FindChild(“子物体名”)或GetChild(索引值)找到这个子物体,并设置SetActive(true)。即:this.transform.GetChild(0).gameObject.SetActive(true)。

* 3) gameObject.renderer.enabled//控制一个物体是否在屏幕上渲染或显示,而物体实际还是存在的,只是想当于隐身.而物体本身的碰撞体还依然存在的.

3- 判断物体本身或其父类物体是否可见:
gameobject.activeinhierarchy;//判断组件是否可见(不能设置为true或false,只能用于判断,是只读的)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img2/20/%E5%9B%BE%E7%89%8741.png)

### 其他类型组件的隐藏介绍

鼠标光标显示与隐藏

Cursor.visible = false;

Cursor.visible = true;

## 响应事件 - OnEable，OnDisable， OnDestroy

* 1- 三个响应事件在项目运行时,是时时监控的

* 2- 当结束项目运行时,Ondisable与OnDestroy都会被运行一回

* 3- 前两个针对的是游戏对象,最后一个针对的是脚本本身
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img2/20/%E5%9B%BE%E7%89%8771.png)
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img2/20/%E5%9B%BE%E7%89%8781.png)
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img2/20/%E5%9B%BE%E7%89%8782.png)
 
 ## Time类及时间控制
 
* Time时间类成员变量介绍

* Time Manager时间管理器

* Time.time 时间

* Time.deltaTime 增量时间

* Time.timeScale 时间缩放

* Time.realtimeSinceStartup 自游戏开始实时时间 
 
 在Unity中，Time类是一个非常重要常用的类。我们可以通过Time类来获取和时间有关的信息，可以用来计算帧速率，可以调整时间流逝的速度等功能。
 
 ## Time时间类及成员变量
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/21/%E5%9B%BE%E7%89%8731.png)
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/21/%E5%9B%BE%E7%89%8741.png)
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/21/%E5%9B%BE%E7%89%8742.png)
 
 ## Time时间管理器
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/21/%E5%9B%BE%E7%89%8751.png)
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/21/%E5%9B%BE%E7%89%8752.png)
 
 说明：
 
* 1- Fixed Timestep: 物理固定帧率.即: FixedUpdate响应事件的刷新帧率

* 2- Maximum Allowed Timestep: [’mæksɪməm] 物理固定帧率更新的最大时间值

* 3-Time Scale: 时间缩放

注：如果Time Scale被缩小 -> 场景播放镜头变慢(场景中播放速率变慢) -> 播放画面出现卡顿现象

Time.time 时间

此帧开始的时间（只读）。这是以秒计算到游戏开始的时间。也就是说，从游戏开始到到现在所用的时间。

* 会受到时间缩放的影响

 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/22/%E5%9B%BE%E7%89%8721.png)
 
 ### Time.deltaTime 增量时间
 
* 以秒计算，完成最后一帧的时间/上一帧的时间（只读）。

* 放在Update()函数中的代码是以帧来执行的.如果我们需要物体的移动以秒来执行.我们需要将物体移动的值乘以Time.deltaTime

* 如果想要一个值根据每帧的变化而变化（增加或减少） ，你应该使用 Time.deltaTime来乘以这个值。这样才能使得变化的效果依赖于单位时间，而不是帧频。这不仅使得游戏的运行独立于帧频，也使得运动的效果符合现实。

* 每秒物体移动10米
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/22/%E5%9B%BE%E7%89%8732.png)
 
 ```C#
 //如下,即使程序执行每一帧的时间特别慢,那么也能保证每一秒是移动一米的距离
void Update ()
	{
    for (int i = 0; i < 100000000; i++)
    {

    }
    transform.Translate(new Vector3(0, 0, 1*Time.deltaTime));
  }
 ```
 ### 理解Time.deltaTime
 
* 1. Time.deltaTime表示上一帧执行的时间,即上一次Update()所执行的时间

* 2. 如果Time.deltaTime为1/30秒,则1秒内会执行30次Update()

* 3. 如果Time.deltaTime为1/60秒,则1秒内会执行60次Update()

* 4. 所以可以看到,在Update中,Time.deltaTime值小了,但是Update()相对于FixedUpdate在1秒内执行的次数就正比增多了

* 5. 即:在Update()中,不论Time.deltaTime值为多少,经过1秒时间后,相加值都为1 (1/30秒 * 30次Update() = 1秒),(1/60秒 * 60次Update() = 1秒)
so,

* 比如当速度值为10时,Speed * Time.deltaTime实际表示：每秒移动物体10米,而不是每帧10米
 
 ### Time.deltaTime的计时器
 
 ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E5%B8%B8%E7%94%A8API/img3/22/%E5%9B%BE%E7%89%8741.png)
 
### Time.timeScale 时间缩放

传递时间的缩放。这可以用于减慢运动效果。

* 1）当timeScale传递时间1.0时和实时时间一样快

* 2）当timeScale传递时间0.5时比实时时间慢一半

* 3）当timeScale传递时间为0时游戏暂停

* 4）当timescale设置为0时，FixedUpdate函数将不会被调用
 
 ```C#
 void Update ()
{
if (Input.GetMouseButtonDown(0))
        {
            Time.timeScale = 0f;
        }
        if (Input.GetMouseButtonDown(1))
        {
            Time.timeScale = 1f;
        }

        if (Input.GetMouseButtonDown(2))
        {
            Time.fixedDeltaTime = 1;
        }
 ```
 
 注:
scaleTime影响的是Time.time,影响的是时间,不会影响realtimeSinceStartup
 
## Time 时间类及成员变量

* 1- timeSinceLevelLoad在同一场景中与time值是一样的,当切换场景,这个时间会重新计算

* 2- 在处理逻辑时使用Update效果更好

* 3- frameCount记录的是所有的帧数量值

* 4- realtimeSinceStartup与Time.time一样记录项目运行时间的,不同的是Time.time记录项目运行的时间,而realtimeSinceStartup记录的是所有时间,包括项目暂停时,时间也同样记录


