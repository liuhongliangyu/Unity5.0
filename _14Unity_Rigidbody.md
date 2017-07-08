## 刚体（Rigidbody）
### 刚体的概念：
	在任何力的作用下，体积和形状都不会发生改变的物体叫做刚体（Rigidbody）。它是力学中的一个科学抽象概念，即理想模型。事实上，任何物体受到外力，不可能不改变形状。实际物体都不是刚体。若物体本身的变换不影响整个运动过程，为使被研究的问题简化，可将该物体当做刚体来处理而忽略物体的体积和形状，这样所得结果仍与实际情况符合。例如，物理天平的横梁处于平衡状态，横梁在力的作用下产生的形变很小，各力矩的大小都几乎不变。对于形变，实际是存在的，但可不予考虑。为此在研究天平横梁平衡的问题时，可将横梁当作刚体。
	
  在Unity物理引擎中，使用刚体（Rigidbody）类模拟这种物理效果，当一个游戏对象被赋予刚体组件后，游戏引擎就会对其进行物理效果的计算和模拟。同时我们也可以给这个对象施加各种作用力，让它运转起来。另外如果要实现重力效果，那么相应的游戏物体都必须附上刚体组件。
### 刚体的使用方法：
  既然前面已经说过，物理引擎用于模拟物体碰撞，力影响等效果，那么，刚体是在处理物体碰撞和想用力去控制物体移动的首选组件。
#### 1. 组件的添加
* 在Inspector面板中->Add Component->Physics->Rigidbody.

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E5%88%9A%E4%BD%93/img/%E5%9B%BE%E7%89%871.png)
![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E5%88%9A%E4%BD%93/img/%E5%9B%BE%E7%89%872.png)

* 再选中 要添加刚体的游戏对象后，通过Unity编辑器菜单栏添加

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E5%88%9A%E4%BD%93/img/20170318191547.jpg)

#### 2. 详细参数介绍

添加好组件后，可以看到Rigidbody组件面板上的参数。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E5%88%9A%E4%BD%93/img/%E5%9B%BE%E7%89%873.png)

* Mass:质量

质量越大，惯性越大。建议场景中的物体质量最好不要相差100倍率以上。防止两个质量相差太大的物体碰撞后会产生过大的速度，从而影响游戏性能及呈现的效果。

* Drag：阻力（摩擦力）

这里指的是空气阻力，属性数值影响阻碍此物体对象的直线运动的速度效果。当游戏物体受到某个作用力的时候，这个值越大越难移动。如果设置成无限的话，物体会立即停止移动。

* Angular Drag:角阻力（旋转摩擦力）

同样指的是空气阻力，只不过是用来阻碍物体旋转的。如果设置成无限的话，物体会立即停止旋转。

* __Use Gravity:使用重力__

不勾选，则不会受到重力影响。

* Is Kinematic：是否符合运动学的（是否受到物理引擎的驱动）。

这个属性有点难理解，它是忽略力对该物体的作用。即不论是外力,还是重力,都无法作用于此物体上，即不受物理引擎驱动。仅仅拥有物理碰撞模型，可以与其他物理碰撞，但是本身不表现出物理特性。比如碰撞后的反弹，或受重力影响，这些在勾选后都是不起作用的。但是如果想改变这些物体的位置的话可以直接改变transform属性，而不需要用物理的方式。
总结：Rigidbody->Is Kinematic->勾选后，变成不再受物理引擎的影响，改为受Transform的影响。即不再有重力，不再被碰撞等，只会呆在Transform规定的位置上不动，物体撞击时候像一堵墙一样不会倒，位置不会因碰撞而发生改变。

* Interpolate[ɪn’tɜːpəleɪt]：差值类型。

如果看到刚体移动的时候运动的不是很平滑，可以选择一种平滑方式。即：平滑物体运动的曲线。

    * None（无差值）：不使用差值平滑。

    * Interpolate（差值）：根据上一帧来平滑移动。

     * Extrapolate（推算）：根据推算下一帧物体的位置来平滑移动。

* Collision Detection 碰撞侦测。

用来改变物体碰撞检测的精度。

    * Discrete（离散）：默认的碰撞检测方式。但若当物体A运动很快的时候，有可能前一帧还在B物体的前面，后一帧就在B物体后面了，这种情况下不会触发碰撞事件，所以如果需要检测这种情况，那就必须使用后两种检测方式。
    
    * Continuous（连续）：这种方式可以与有静态网格碰撞器的游戏对象进行碰撞检测。 可以避免因物体移动速度过快而穿过另一个物体的情况。
    
    * Continuous Dynamic（动态连续）：这种方式可以与所有设置了2或3方式的游戏对象进行碰撞检测。

* Constraints：约束。
约束位置或旋转时的x/y/z坐标,使其Freeze(冻结)。比如想控制游戏对象人物上台阶不会摔倒，或者高速碰到一个墙壁物体时不会胡乱转动的话,则要冻结x，y和z轴的旋转。

* [重要] centerOfMass:相对于变换原点的质心。

* [重要] angularVelocity 刚体的角速度向量,修改它可以使刚体进行旋转

### 【案例】
创建两个Cube,都添加上刚体，其中一个调整为长方体，并取消useGravity，通过centerOfMass调整物体的重心。在Inspector面板中，修改重心观察效果。

```C#
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour {
    public Vector3 com;
    public Rigidbody rb;
    void Start() {
        rb = GetComponent<Rigidbody>();
        rb.centerOfMass = com;
    }
}
```

效果1(centerOfMass值为(0,0,0))

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E5%88%9A%E4%BD%93/img/centermass01.gif)

效果2(centerOfMass值为(0,1,1))

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E5%88%9A%E4%BD%93/img/centermass02.gif)
### 1. 控制刚体移动的方法

**注意:处理Rigidbody时，一般情况物理仿真需要用FixedUpdate代替Update。**

#### 恒定力组件

给刚体添加恒定力Constant Force组件

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E5%88%9A%E4%BD%93/img/%E5%9B%BE%E7%89%876.png)

Constant Force组件属性介绍

**注：Constant [’kɒnst(ə)nt] 常数,恒量,恒定的,不变的。**
    
    * Force：绝对力 世界坐标力。
    
    * Relative Force：相对力 自身坐标力。
    
    * Torque[tɔ:k] ：绝对扭距 世界坐标扭距。
    
    * Relative Torque：相对扭距 自身坐标扭距。

#### 2. 刚体睡眠（Sleep）和唤醒（Wake Up）函数

* Sleep 使物体睡眠，不进行移动

* WakeUp是刚体从睡眠中醒过来，能做一些操作

下面通过一个示例，来讲解刚体的休眠与唤醒等相关的函数方法。如图 所示。创建一个Plane地板和2个标准立方体Cube。为2个Cube分别添加上刚体组件Rigidbody。在其中一个Cube上添加脚本如下：

##### 【案例】
```C#
oid Start () {

        GetComponent<Rigidbody>().useGravity = true;
	}

	void Update () {

        if (Input.GetMouseButtonDown(0))
        {
            GetComponent<Rigidbody>().Sleep();
        }
        if (Input.GetMouseButtonDown(1))
        {
            GetComponent<Rigidbody>().WakeUp();
        }
	}
```

#### 3. 通过刚体的速度向量（velocity）控制移动
之前章节中讲过，开发者可以利用物体的Transform.Translate函数来使物体达到一个位移的效果。刚体有一个重要的属性velocity，通常情况下，我们会利用这个属性来实现运动效果。

##### 【案例】
创建一个Cube，添加刚体组件，编写脚本，利用Rigidbody.velocity刚体的速度向量驱动物体运动，通过按空格键按下使物体向上运动。

```C#
using UnityEngine;
using System.Collections;

public class example : MonoBehaviour {
	private Rigidbody rigidbody;
	void Start(){
		 //获取RigidBody组件
		 this.rigidbody=this.GetComponent<RigidBody>();
	}
	void FixedUpdate() {
		if (Input.GetButtonDown("Jump"))
		  //对刚体设置速度向量
			this.rigidbody.velocity = new Vector3(0, 10, 0);
			//等价于rigidbody.velocity = transform.up * 10;
	}
}
```

#### 4. 通过施力进行移动

对刚体施加力有以下几种方法：

* AddExplosionForcer 应用一个力到刚体上来模仿爆炸效果。

```C#
using UnityEngine;
using System.Collections;

// Applies an explosion force to all nearby rigidbodies
public class ExampleClass : MonoBehaviour {
    public float radius = 5.0F;
    public float power = 10.0F;

    void Start() {
        Vector3 explosionPos = transform.position;
        Collider[] colliders = Physics.OverlapSphere(explosionPos, radius);
        foreach (Collider hit in colliders) {
            Rigidbody rb = hit.GetComponent<Rigidbody>();

            if (rb != null)
                rb.AddExplosionForce(power, explosionPos, radius, 3.0F);

        }
    }
}
```

* AddForce 添加到刚体的力

```C#
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour {
    public float speed;
    public Rigidbody rb;
    void Start() {
        rb = GetComponent<Rigidbody>();
    }
    void FixedUpdate() {
        rb.AddForce(transform.forward * speed);
    }
}
```

* AddForceAtPosition 在position位置应用force力。作为结果这个将在这个物体上应用一个扭矩和力。

* AddRelativeForce 添加力到刚体。相对于它的系统坐标。










