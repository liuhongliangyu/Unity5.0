## 射线

前面章节讲过，刚体与刚体、刚体与碰撞器之间可以发生碰撞，开发者可以通过碰撞器或触发器进行碰撞或触发检测。Unity还为广大开发者提供了一种射线的检测方式，射线是3D世界中一个点向一个方向发射的一条无终点的线，在发射轨迹中与其他物体发生碰撞时，它将停止发射 。此功能通过物理类中的raycast函数来实现。射线应用范围比较广， 多用于碰撞检测（如：子弹飞行是否击中目标）、角色移动等 等。
Unity中关于射线的有一个非常重要的函数类Physcics类，该类有Raycast和Linecast两种射线投射方式；第一种是以起点和射线方向为参数的投射，第二种是以起点和终点为参数的投射。既然是射线碰撞，那么被射物体必须有被碰撞组件（如BoxCollider等）

### 绘制射线

绘制射线长度

* Debug.DrawLine(transform.position, Vector3.forward * 10, Color.blue);

* Debug.DrawRay(transform.position, Veyor3.left * 10, Color.red);

**注：Debug是调试类，在程序运行时，只能在Scene场景中显示绘制的射线，而不会在Game场景中显示**

* 1. 第一个参数是射线绘制出来的位置

* 1. 第二个参数时绘制出来的点的向量，上式写的是方向*大小，也可以写成new Vector3(0,0,10),但是不建议这么写，每次都要new一下耗费内存

* 1. 第三个参数是颜色，可以直接写Color.red/blue/green等

* 1. 第四个参数是射线区域，如果改变了射线方向，则射线会形成一个区域，为float类型，值越大停留时间越长。

### 射线检测

射线检测的相关参数概念：

* 1. RaycastHit hit:光线投射碰撞（此变量用于存储此射线碰到了哪些物体的信息）

* 2. Camera.main.ScreenPointToRay(位置)：屏幕位置发射线，返回一条射线从摄像机通过一个屏幕点

**注：**

* 1. 产生的射线是在世界空间中，从相机的近裁剪面开始并穿过屏幕position（x，y）像素坐标（position.z被忽略）

* 2. 屏幕空间以像素定义。屏幕的左下为（0,0）；右上为（pixelWidth,pixelHeight）。

相关API：

* 1. Ray Camera.main.ScreenPointRay(Vector3 pos)返回一条射线Ray从摄像机到屏幕指定一个点

* 2. Ray 射线结构体

* 3. RaycastHit 光线投射碰撞信息

* 4. bool Physics.Raycast注意：如果一个球型体的内部到外部用光线投射，返回为假。

**【参数理解】**

```
    origin : 在世界坐标中射线的起始点
    direction: 射线的方向
    distance: 射线的长度
    hit: 使用c＃中out关键字传入一个空的碰撞信息类，然后碰撞后赋值。可以得到碰撞物体的transform,rigidbody,point等信息。
    ayerMask: 只选定Layermask层内的碰撞器，其它层内碰撞器忽略。 选择性的碰撞过滤物体。可以在TagManager中编辑tag和Layer。然后设置物体的Layer层级，在摄像机中设置camera.cullingmask,可以控制摄像机的渲染层级，用在射线上，可以控制射线碰撞什么，不碰撞什么。
返回布尔类型，当光线投射与任何碰撞器交叉时为真，否则为假。
```

**射线的五个参数：**
```
Physics.Raycast(射线ray, 光线投射碰撞到的物体out hit, 射线长度distance);
Physics.Raycast(位置position, 方向forward, 光线投射碰撞到的物体out hit, 射线长度distance);
Physics.Raycast(位置position, 方向forward, 光线投射碰撞到的物体out hit, 射线长度distance, 遮罩过滤层layerMask 1<<8);
```

**注：**

* 1. 第一个参数是射线的起点

* 2. 第二个参数是射线的方向

* 3. 第三个参数是碰撞的信息

* 4. 第四个参数是射线的长度

* 5. 第五个参数是遮罩过滤层

#### 示例1：鼠标点击Cube让其旋转

```C# 
public class test06 : MonoBehaviour {
	GameObject obj = null;
	bool isClick = false;
	void Update ()
	{
		if(Input.GetMouseButton(0))
		{
			Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
			RaycastHit hit;
			if(Physics.Raycast(ray,out hit,100.0f))				//用if语句来发出一条射线
			{
				obj = hit.collider.gameObject;			//射线碰到了哪些物体
				isClick = true;
			}
		}
		if(isClick == true)
		{
			obj.transform.Rotate(new Vector3(0,0,50));
		}
	}
}
```

#### 案例2：让物体对象发出一个射线，并使这个物体旋转，此时射线遇到的物体一个个消失

```C#
GameObject obj = null;
    void Start()
    {
        obj = GameObject.Find("Cube2");
    }
    void Update()
    {
        obj.transform.Rotate(new Vector3(0, 1, 0));//使物体绕y轴旋转
        RaycastHit hit;//声明接收射线投射碰撞传出的信息
        
        if (Physics.Raycast(obj.transform.position, obj.transform.forward, out hit,100))
        {
            //第一个参数: 是射线的起始位置坐标
            //第二个参数,射线的方向,
            //返回射到点的信息
            //射线长度
            Destroy(hit.collider.gameObject);
        }
    }
```

### 案例3：通过层对射线进行设定：

```C#
public class test06 : MonoBehaviour
{
    GameObject obj = null;
    void Start()
    {
        obj = GameObject.Find("Cube2");
    }
    void Update()
    {
        obj.transform.Rotate(new Vector3(0, 1, 0));
        RaycastHit hit;
        Vector3 fwd = transform.TransformDirection(Vector3.forward); //变换方向从局部坐标转换到世界坐标  TrandformDirection(Vector3:value)
        if (Physics.Raycast(transform.position, fwd, out hit, 100, 1 << 8))
        {						//1位移8,这个参数表示只能检测到参数中的层
//射线碰撞层级为8，其他层级忽略。
            Destroy(hit.collider.gameObject);
        }
    }
}

注 ： 1 << 10  打开第10层
     ~（1 << 10）打开除了第10层之外的层。默认层不算，要手动添加的层才可以
     (1 << 10) | (1 << 8) 打开第10层和第8层
```

#### 示例4：具体示例：子弹检测

```C#
using UnityEngine;
using System.Collections;

public class RayTest : MonoBehaviour {

	void Update()
	    {
	        #region //由于子弹运行速度太快,不可能在子弹上放Collider组件去检测碰撞:@@@@@@@@@@@@
	        Vector3 oldPos = transform.position;//在Update中,在执行第一帧的时候,子弹的位置
	        transform.Translate(Vector3.right * 500 * Time.deltaTime);
	        float length = (transform.position - oldPos).magnitude;//子弹第一帧到之后的每一帧时,经过的长度
	        RaycastHit hit;
	        if (Physics.Raycast(oldPos,this.transform.right,out hit,length))
	        {
	            if(hit.collider.gameObject.name == "目标")
	            Debug.Log(hit.point);
	        }
	        #endregion
	    }

	      void OnTriggerEnter()
	      {
	          print("Collider检测");
	      }
	    //步骤:
	    //1- 声明一个位置,记录在第一帧时,子弹的位置
	    //2- 让子弹移动
	    //3- 在下一帧时,记录下一帧的位置-第一帧的位置
	    //4- 这样可以获得这两帧之间的距离
	    //5- .magnitude方法可以获取向量的长度
	    //6- 通过射线,参数包含这个获取的向量长度,来推算子弹是否与物体发生了碰撞
	    //7- hit.point是碰撞点
```

#### 示例5：具体示例：让子弹弹痕紧贴接触面的效果

```C#
  public GameObject go;  //一个Quad预设图片
	void Start () {

	}

	void Update () {
        Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
        RaycastHit hitinfo;
        if (Input.GetMouseButtonDown(0))
        {
            if (Physics.Raycast(ray, out hitinfo))
            {
                print(hitinfo.transform.name);
                GameObject gg = Instantiate(go,hitinfo.point, Quaternion.identity) as GameObject;
                gg.transform.LookAt(hitinfo.point - hitinfo.normal);
                gg.transform.Translate(Vector3.back * 0.01f);
            }
        }

	}
```




