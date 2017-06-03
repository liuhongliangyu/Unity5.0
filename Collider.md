## 碰撞与触发

### 碰撞器与碰撞、触发检测

在上一节中我们了解到，游戏物体有了刚体才能具备真正的物理属性，而物体与物体之间发生碰撞的时候，则需要对其碰撞的行为进行监测。这需要我们去添加一个碰撞器组件，添加方法为：Inspector面板->Add Component->Physics->Box Collider（根据需要也可以选择为其他的Collider组件）。如图 所示。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%878.png)
![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%879.png)

### 各种碰撞组件属性介绍

1. Box Collider: 核碰撞体，核碰撞体是一个立方体外形的基本碰撞体，该碰撞体可以调整为不同大小的长方体，用作门、墙、以及平台等，也可用于布娃娃的角色躯干或者汽车等交通工具的外壳，当然最适合用在盒子或者箱子上， 属性如下图：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8710.png)

* Is Trigger:触发器，勾选该项，则该碰撞体可用于触发事件，并将被物理引擎所忽略

* Material：材质

* Center：中心，碰撞体在对象局部坐标中的位置

* Size：大小，碰撞体在X、Y、Z方向上的大小

1. Sphere Collider:球形碰撞体，球形碰撞体是一个基于球体的基本碰撞体，球体碰撞体的三维大小可以均匀地调节，但不能单独调节某个坐标轴方向的大小，该碰撞体适用于落石、乒乓球等游戏对象

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8711.png)

* Radius:半径，球形碰撞体的半径

1. Capsule Collider:胶囊碰撞体，胶囊碰撞体有一个圆柱体和预期相连的两个半球体组成，是一个胶囊形状的基本碰撞体，胶囊碰撞体的半径和高度都可以单独调节，可用在角色控制器或者与其他不规则形状的碰撞结合来使用

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8712.png)

* Height :高度，该项用于控制碰撞体中圆柱的高度

* Direction：方向，在对象的局部坐标中胶囊的纵向方向所对应的坐标轴，默认是Y轴

1. Mesh Collider:网格碰撞体，网格碰撞体通过获取网格对象并在其基础上构建碰撞，在与复杂网格模型上使用基本碰撞相比，网格碰撞体要更加精细，但会占用更多的系统资源

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8713.png)

* Smooth Sphere Collisions:平滑碰撞，在勾选该项后碰撞会变得平滑

* Mesh：网格，获取游戏对象的网格并将其作为碰撞体

* Convex：唾弃，勾选该项，则网格碰撞体将会与其他的网格碰撞体发生碰撞

1. Wheel Collider:车轮碰撞体，车轮碰撞体是一种针对地面车辆的特殊碰撞体，他有内置的碰撞检测、车轮物理系统以及滑胎摩擦的参考体

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8714.png)

* Suspension Distance:悬挂距离，该项用于设置车轮碰撞体悬挂的最大延伸距离，按照局部坐标来计算，悬挂总是通过其局部坐标的Y轴延伸向下 

* Center：中心，该项用于设置车轮碰撞体在对象局部坐标的中心

* Suspension Spring：悬挂弹簧，该项用于设置车轮碰撞体通过添加弹簧和阻尼外力使得悬挂达到目标位置

* Forward Friction：向前摩擦力，当轮胎向前滚动时的摩擦力属性

* Sideways Friction：侧向摩擦力，当轮胎侧向滚动时的摩擦力属性

1. Terrain Collider:组件属性如下图

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8715.png)

* Character Controller，角色控制器，角色控制器主要用于对第三人称或第一人称游戏主角的控制，并不使用刚体物理效果

* Slope Limit：坡度限制，该项用于设置所控制的角色对象只能爬上小于或等于该参数值的斜坡

* Step Offset：台阶高度，该项用于设置所控制的角色对象可以迈上的最高台阶的高度

* Skin Width：皮肤厚度，该参数决定了两个碰撞体可以相互渗入的深度，较大的参数值会产生抖动的现象，较少的参数值会导致所控制的游戏对象被卡住，较为合理地设定上是：该参数值为Radius值的10%

* Min Move Distance：最小移动距离，如果所控制的角色对象的移动距离小于该值，则游戏对象将不会移动

* Center：中心，该参数决定了胶囊碰撞体再世界坐标中得位置，

* Radius:半径，胶囊碰撞体的长度半径，

* Height：高度，该项用于设置所控制的角色对象的胶囊碰撞体的高度

### 碰撞与触发分别对应的三种函数方法

系统默认会给每个对象(GameObject)添加一个碰撞组件。而在Unity中，能检测碰撞发生的方式有两种，一种是利用碰撞器，另一种则是利用触发器。这两种方式的应用非常广泛，为了完整的了解这两种方式，我们必须理解以下概念：

* 1. 碰撞器是一群组件，它包含了很多种类，比如：Box Collider，Capsule Collider等，这些碰撞器应用的场合不同，但都必须加到GameObjecet身上。

* 2. 所谓触发器，只需要在Inspector检视面板中的碰撞器组件中勾选IsTrigger属性选择框。

* 3. 在Unity中，主要有以下接口函数来处理这两种碰撞检测：

#### 触发信息检测

* 1. MonoBehaviour.OnTriggerEnter( Collider other )当进入触发器

* 2. MonoBehaviour.OnTriggerExit( Collider other )当退出触发器

* 3. MonoBehaviour.OnTriggerStay( Collider other )当逗留触发器

#### 碰撞信息检测

* 1. MonoBehaviour.OnCollisionEnter( Collision collisionInfo ) 当进入碰撞器

* 2. MonoBehaviour.OnCollisionExit( Collision collisionInfo ) 当退出碰撞器

* 3. MonoBehaviour.OnCollisionStay( Collision collisionInfo )  当逗留碰撞器

注： 

* 1. 以上这六个接口都是MonoBehaviour的函数，由于我们新建的脚本都继承这个MonoBehaviour这个类。所以我们的脚本里面可以覆写这六个函数。

* 2. 参数不同,Collision是类,Collider不是,Collision类包含接触点，碰撞速度等信息

* 3. 参数为被碰撞的对象

* 4. 要做判断,否则,物体添加刚体后,掉到地面,与地面接触也是一种碰撞行为

* 5. if(obj.gameObject.name == “Cube”){}

示例：在两个Cube标准 立方体中的其中一个加入下脚本
```C#
using UnityEngine;
using System.Collections;

public class ColliderTest : MonoBehaviour {

	void OnCollisionEnter( Collision collisionInfo )
    {
        if (collisionInfo.collider.name == "CubeB")
        {
            Debug.Log("Enter");
        }
    }
    void OnCollisionStay(Collision collisionInfo)
    {
        if (collisionInfo.collider.name == "CubeB")
        {
            Debug.Log("Stay");
        }
    }
    void OnCollisionExit( Collision collisionInfo )
    {
        if (collisionInfo.collider.name == "CubeB")
        {
            Debug.Log("Exit");
        }
    }
}
```

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8716.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%A2%B0%E6%92%9E/img/%E5%9B%BE%E7%89%8717.png)

通过后台的输出，我们可以看到物体在进入碰撞状态、停留在碰撞状态、退出碰撞状态中的过程细节。而触发的机制与碰撞是一样的，具体示例在此省略。

#### 碰撞检测条件

* 1. 都有Collider

* 2. 必须要在挂脚本的物体上有Rigidbody

* 3. Collider上都不勾选Is Trigger

#### 触发检测条件

* 1. 都有Collider

* 2. 必须要在挂脚本的物体上有Rigidbody

* 3. 所挂脚本物体勾选Is Trigger

综上，总结如下：

共性：

* 1. 必须都有Collider。

* 2. 且至少在挂脚本的物体上加Rigidbody

区别：

* 3. 碰撞都不勾选Is Trigger。

* 4. 而触发则需要勾选Is Trigger属性。（ 只需在任意一个物体上勾选即可）。










