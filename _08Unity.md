# 访问组件

## 查找游戏对象

* GgameObject.Find();

* transform.Find();

### GameObject.Find() - 返回GameObject类型

* 1. GameObject.Find()可以查找任何层级的物体，不收脚本所绑定的物体层级位置影响

* 1. GameObject.Find()可以指定层级查找，也可以不用指定层级去查找；若指定层级，则会在所对应的层级中查找；若不指定层级，则会在所有的层级中查找（名称不能重复）

* 1. GameObject.Find()如果没有指定层级，而查找的物体是多个相同名称的物体，则会在查找到Hierarchy面板列表中最后一个创建的同名物体

* 1. GameObject.Find()没有写出全路径名称情况下，不支持查找隐藏的物体

### trandform.Find() - 返回的是Transform类型

* 1. transform.Find()只能查找子集的物体

* 1. transform.Find()如果想查找其它同级（同级或父级）的物体，则需要使用完整路径进行查找

* 1. transform.Find()支持查找隐藏的物体

注意：隐藏的物体指的是物体没有被激活，并不是看不见的物体

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/11/%E5%9B%BE%E7%89%8721.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/11/%E5%9B%BE%E7%89%8722.png)

* 查找并获取游戏对象 - 查找没有被激活的游戏对象

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/11/%E5%9B%BE%E7%89%8731.png)

#### 通过子物体名称/路径查找子物体：

obj = transform.FindChild("子节点").transform.FindChld("再下一层子节点名")...

obj = transform.GetChild(0);  //查找父节点下的第一排

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/11/%E5%9B%BE%E7%89%8723.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/12/%E5%9B%BE%E7%89%8721.png)

#### 通过子物体获取其父物体:

gameObject.transform.parent

注：还可以继续往上一级获取父物体：gameObject.transform.parent.parent

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/12/%E5%9B%BE%E7%89%8731.png)

### 其它查找游戏对象的方法

* 通过Tag标签查找物体

通过Inspector中的Tag标签查找物体

```C#
GameObject obj = GameObject.FindWithTag("AI");//通过Tag标签查找一个物体
GameObject obj = GameObject.FindGameObjectWithTag("AI");//通过Tag标签查找一个物体
GameObject[] obj = GameObject.FindGameObjectsWithTag("AI");//通过Tag标签查找一批物体
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/13/%E5%9B%BE%E7%89%8721.png)

## 获取组件

* GetComponent<>()

* GetComponentInChildren<>()

* GetComponentsInChildren<>()

* GetComponentInParent<>()

* GetComponentsInParent<>()

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/14/%E5%9B%BE%E7%89%8721.png)

### 获取，得到组件-脚本

Obj.GetComponent<脚本名>();

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/14/%E5%9B%BE%E7%89%8731.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/14/%E5%9B%BE%E7%89%8732.png)

### 从物体本身或者其子物体(儿子,孙子重孙子…)中获取单个或多个组件(或脚本)

获得子物体的一个组件

* gameObject.GetComponentInChildren<脚本或组件名称>()

获取子物体组件列表

* gameObject.GetComponentsInChildren<脚本或组件名称>()

### 从物体本身或其父类物体(父亲,爷爷,祖宗)中获取单个或多个组件(或脚本)

* gameObject.GetComponentInParent<脚本或组件名称>()

获取父类中组件列表（包括物体本身以及下面的所有子物体）

* gameObject.GetComponentsInParent<脚本或组件名称>()

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/14/%E5%9B%BE%E7%89%8751.png)

### 添加组件的几种方法

* gameObject.AddComponent<>()

* [RequireComponent(typeof())]

1. 动态添加脚本

gameObject.AddComponent<脚本名>();

2. 动态加载组件（eg:添加刚体）

gameObject.AddComponent<RigidBody>();

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/15/%E5%9B%BE%E7%89%8731.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/15/%E5%9B%BE%E7%89%8732.png)

3. 添加组件（扩展编辑器）

[RequireComponent(typeof())]

注: 扩展编辑器所执行的代码一定是在编辑状态下的
只有在脚本没有挂载到物体上时候编辑再拖到物体上才有效果

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/15/%E5%9B%BE%E7%89%8741.png)

## 方法与属性的执行效率

* 比较组件

* Tags标签管理类

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/16/%E5%9B%BE%E7%89%8726.png)

### 比较组件:

1. Component.tag == “xxx”;

2. Component.CompareTag(“xxx”);

注:

1- 继承自GameObject的游戏对象和Component类的组件都有一个tag和CompareTag属性和方法

2- 执行效率ComparTag相对更高

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/16/%E5%9B%BE%E7%89%8731.png)

## 项目经验 - Tags标签管理类

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img/16/%E5%9B%BE%E7%89%8741.png)

## 游戏物体的生成和销毁

* 游戏物体的生成和销毁

* Object.Instantiate 实例

### GameObject.CreatePrimitive 创建基本物体

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8721.png)

### Object.Instantiate克隆/实例/创建一个游戏物体

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8731.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8732.png)

Object.Instantiate是重载函数,方法有两种: (两种方式不论输入和输出都为Object类型)：一种是参数需要指定为Object类型,返回一个Object类型,默认生成物体的位置和旋转都为0点(Vector3.zero,Quaternion.identity)；另一种是参数除了指定Object类型,还可以指定其位置和旋转角度,返回同样一个Object类型
Object类包含GameObject和组件两种,即: 不论指定的参数为GameObject游戏对象,还是Component组件,都将返回一个Object类型整个的克隆体，因为返回类型是Object类型,所以会在场景中生成一个对应游戏物体的克隆体(Clone)

注意 :

Object.Instantiate比较耗配置,因为每次实例化物体都需要系统进行加载

destroy方法可以定时删除游戏对象

#### Object.Instantiate 小示例1 - 最简单的克隆游戏对象

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8741.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8742.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8743.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8744.png)

注:

1- 脚本绑定在第三方

2- Hierarchy列表中产生的克隆体带“(Clone)”字样,表示为通过Instantiate克隆出来的

#### Object.Instantiate 小示例2 - 克隆对象本身

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8751.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8752.png)

注:

修改代码,脚本绑定在本身身上,同样在Hierarchy列表中产生克隆体

如果反复克隆,则会在生成的克隆体之上继续克隆出新的克隆体

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8761.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/17/%E5%9B%BE%E7%89%8762.png)

注:

通常情况下,不会克隆Hierarchy面板中场景内的游戏物体,因为场景内的物体在游戏运行时需要去加载,而在其他的场景中无法复用

此时可以规定其位置和旋转角度;如果没有规定,则生成的克隆对象,会沿用之前原物体当时的坐标

### 游戏物体的生成和销毁

* Object.Destroy 销毁

* Object.DestroyImmediate 立即销毁

* Object.DontDestroyOnLoad 加载时不销毁

* MonoBehaviour.OnDestroy 当销毁

#### Object.Destroy()

* 可以游戏当中动态删除场景中的组件,物体

* Destroy继承自Object,所以凡是基础Object类的组件,物体,资源都可以被此方法动态的删除

* 第二个参数为延迟删除销毁的时间,默认为0(立即删除)

* 删除物体之后,物体上的组件,包括脚本也会对应删除,脚本将不会再起作用

* 若删除的物体有父子层级关系,则会删除自身及连同子集,父级不会被删除

* this代表脚本本身 gameObject 等价于 this.gameObject

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/18/%E5%9B%BE%E7%89%8721.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/18/%E5%9B%BE%E7%89%8722.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/18/%E5%9B%BE%E7%89%8723.png)

注意:

* 关于帧运行的机制..

* 当销毁存在父子级关系的游戏对象时,会一并销毁子级

#### Object.DontDestroyOnLoad 加载时不销毁

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/19/%E5%9B%BE%E7%89%8721.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/19/%E5%9B%BE%E7%89%8722.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/19/%E5%9B%BE%E7%89%8724.png)

注意:

1- 当切换场景,到一个新的场景时,如果在老场景中使用了此函数,参数中被指定的对象Object将不会在新场景中销毁,在新场景中还可以继续看到指定的Object物体对象

2- 当Unity加载或读取一个新场景时,之前的场景所有的对象在内存中将都被释放,如果想保持指定的物体,就需要使用此函数方法

3- 被加载过来的物体,身上所有的组件及对应的属性信息都不会改变

4- 如果加载保存的不是游戏对象,而是对象上某个组件,其效果与整体保存游戏对象效果是一样的

##### Object.DontDestroyOnLoad 小示例

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/19/%E5%9B%BE%E7%89%8732.png)

* 菜单导航栏 -> File -> Build Settings -> 把新,老场景指定到 Scenes In Build中

##### Object.DontDestroyOnLoad 小提问

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/19/%E5%9B%BE%E7%89%8741.png)

##### 问题1: 是否可以保留组件,而不是游戏对象?

1- 如果指定的参数不是游戏对象,而是一个物体中的某个组件,但切换场景后,仍然是这个物体所有的东西都一起带到新场景中,而不是只保留了某个刚指定的组件即: 如果保留一个物体身上某一个组件,对应组件实例的物体都将会保存下来

##### 问题2: 有父子级关系时,是如何的保留情形的?

2- 如图,Cube1和Cube4中添加代码,则Cube1和Cube2都被保留,Cube3和Cube4都不会被保留.即: 要保留的对象自己必须是父级,且自己的子集将会一起被保留

必须自己就是Hierarchy面板中的根目录级别,而其子物体也会统一保存下来

#### MonoBehaviour.OnDestroy 当销毁

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/19/%E5%9B%BE%E7%89%8751.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/06_%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6/img2/19/%E5%9B%BE%E7%89%8752.png)

注意:

不要忘记添加刚体组件(关于刚体组件,将在后面的专题课程中重点详细介绍)


