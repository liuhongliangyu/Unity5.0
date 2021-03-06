## 引语

寻路是游戏中常用的一项技术，3D游戏世界用于实现物体能够自动寻找一条路径到达目的地的一项技术。他将游戏场景中复杂的结构组织关系简化为带有一定信息的网格，在这些网格的基础上通过一系列相应的计算来实现自动寻路

自动寻路就是AI中的一个十分重要的分支，其算法异常复杂。Unity中提供的这套非常成熟的组件来为我们解决这一难题。

在Unity中，可以根据用户所编辑的场景内容，自动的生成用于导航的网格。导航时，只需要给要进行寻路的物体挂载导航组件，导航物体便会自行根据网格信息来寻找做直接的路线，并沿着路线行进到目标点。
自动训练路属于AI（人工智能）的范畴，使用Unity来开发手游，除了导航网络寻路外，比较传统的是用**A星寻路**，它是一种比较传统的人工智能算法，在游戏开发中比较常用到。大部分的页游和端游都用到这种技术。在Unity游戏也可以用这种技术，Asset Store上面已经有相关的组件了，感兴趣的同学可以自己去了解。

## 寻路系统操作步骤

1. 对场景中物体进行标记，然后进行路径烘焙，产生网格数据。

1. 为要进行寻路的物体添加寻路组件（NavMeshAgent）。

1. 通过NavMeshAgent组件的属性或方法进行移动。

## 【案例】

使用NavMesh组件来实现最基本的角色自动寻路。点击场景中某个位置，角色绕过各种复杂的障碍物自动寻路过去。

### 场景创建及烘焙

1. 使用Plane，Cube游戏对象搭建如下图所示的场景，并将创建的所有对象放置到一个空物体中，并命名inv。并创建新标签Tag为inv，为环境中的物体及其场地都添加上inv标签。（其中Plane作为地面，Capsule胶囊体作为主角）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%871.png)

2. 通过菜单栏->Window->Navigation打开Navigation操作窗体。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%872.png)

3. 选中inv地形在Navigation窗口中，勾选Navigation Static。如图所示

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%873.png)

或者选中地形，在Inspector面板中->Static->勾选Navigation Static。如图所示。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%874.png)

在弹出的窗体中选择Yes，将所有的子对象也设置为静态中对象。或者依次选中场景对象（不包含Capsule）,在Navigation窗口中的Object标签中，勾选NavigationStatic属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%875.png)

4. Navigation窗口中，选择Bake（烘焙）界面，点击Bake按钮，进行场景烘焙，就可以烘焙出寻路网格了。效果如图

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%876.png)

### Bake烘焙参数面板

* Radius：半径。半径数值越小，生成网格面积越大，越容易靠近被烘焙的静态物体。

* Height：高度。整体网格可以烘焙到的高度。1和2可以理解为寻路者的半径和高度。

* Max Slope：最大斜坡角度。角度越大，代理越能爬坡，超过这个坡度寻路者则无法通过。

* Step Height：台阶步高。步高越大，导航代理迈过台阶的能力越强（可达到或代替跳跃效果）

* Drop Height：代理跳落高度。（只能往下跳，不可往上跳）。表示寻路者可以跳落的高度。

* Jump Distance：代理跳跃距离。（往远处跳跃的距离）表示寻路者的跳跃距离极限。

* Advanced高级模式（最好别动）

  * Manual Voxel Size：导航烘焙的像素效果
  
  * Min Regon Area：网格面积小于该值的地方，将不生成导航网格
  
  * Height Mesh：勾选后，将会保存高度信息
  
  ###　寻路对象设置
  
  为胶囊体角色对象添加NavMeshAgent组件，即：为其添加一个导航代理。Component->Navigation->Nav Mesh Agent.如图所示
  
  ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%878.png)
  
  NavMeshAgent组件常用属性
  
  ![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/15_%E5%AF%BC%E8%88%AA%E7%BD%91%E7%BB%9C%E5%AF%BB%E8%B7%AF_%E5%9F%BA%E7%A1%80%E5%AF%BB%E8%B7%AF/images/%E5%9B%BE%E7%89%879.png)
  
* Radius 半径： 代理的半径（仅用于寻路目的，可以跟实际对象的半径大小不一样，一般比实际对象的半径大）。

* Speed 速度： 代理的最大移动速度。

* Acceleration 加速度： 最大加速度。

* Angular Speed 角速度： 最高转速（度/秒）。

* Stopping distance 制动距离：到目的地的距离小于此属性值时，代理则此时开始减速。

* Auto Traverse OffMesh Link 自动遍历OffMesh链接：自动移动并关闭OffMeshLinks。即：是否采用默认方式度过连接路径。

* Auto Repath 自动重新寻路：在进行因为某些原因中断寻路的情况下，是否重新计算，获得新的路径，重新开始寻路。

* Height 高度：代理的高度（用于调试图形）。

* Base offset 基本偏移：碰撞几何体相对于实际几何体垂直的偏移。

* Obstacle Avoidance Type 障碍躲避表现等级，即：躲避的质量水平。

* None：不躲避障碍。等级越高，躲避效果越好，消耗相应越多。

* Avoidance Priority：躲避优先级。

* NavMesh Walkable：代理可以进行的网隔层掩码。导航网格行走：指定代理可以遍历的导航网格层类型。可以为地形指定不同的层，指定代理可以通过或者不可以通过哪些层。

* 注：要说明的是，障碍物一定要有Mesh Render，用于烘焙寻路网格。
  
### 寻路功能实现  

```C#
using UnityEngine;
using System.Collections;

public class PlayerController : MonoBehaviour {

  private NavMeshAgent agent;

  void Start()
  {
      //获取组件  
      agent = GetComponent<NavMeshAgent>();
      agent.destination =hit.point;//等价于：agent.SetDestination(hit.point);
  }
}
```

```C#
using UnityEngine;
using System.Collections;

public class PlayerController : MonoBehaviour {

private NavMeshAgent agent;

void Start()
{
    //获取组件  
    agent = GetComponent<NavMeshAgent>();
}

void Update()
{
    //鼠标左键点击  
    if (Input.GetMouseButtonDown(0))
    {
        //摄像机到点击位置的的射线  
        Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
        RaycastHit hit;
        if (Physics.Raycast(ray, out hit))
        {
            //判断点击的是否地形  
            if (hit.collider.tag == "inv")
            {
                //设置寻路的目标点  
                agent.destination =hit.point;//等价于：agent.SetDestination(hit.point);
            }
        }
    }

    //播放动画，判断是否到达了目的地，播放空闲或者跑步动画  
    if (agent.remainingDistance == 0)
    {
        Debug.Log("已到达");
    }
    else
    {
        Debug.Log("寻路中..");
    }  
  }  
}
```
  
  
  
  
  
  
  
  
  
  
  
  
  
  
