## 引语

以前Unity的内置UI系统，无法适用于商业项目开发，所以便有人或组织开发UI插件来提升开发效率，NGUI便是很典型的UI插件，除此之外，还有TK2D，EZGUI，但流行比较高的便是NGUI。

## 课程内容

* NGUI适用流程

* NGUI常用的基本组件

## NGUI适用流程

对于NGUI插件，从很高程度上回对我们的UI进行优化，其主要的实现方式便是将零散的小UI图片，通过操作将其合并成一张图，这张图便可以称之为图集（Atlas），制作图集的工作可以使用内置工作Atlas Maker，也可以使用Texture Packer组件

Atlas制作->创建UISprite->选取Sprite->添加功能组件。

## 常用基本组件讲解

### 1. 文本标签（UILabel）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%9F%BA%E6%9C%AC%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8/images/20160918200239.png)

BBCode是很早以前的富文本标记语言

```
[ff0000]你好[-]
我是[b]粗体[/b]
我是[i]斜体[/i]
我是[u]下划线[/u]
我是[s]删除线[/s]
我是Mircorsoft[sup]TM[/sup]
我是H[sub]2[/sub]O
超链接[url=http://www.baidu.com/]百度[/url]
```
当我们在Label的Text中写入以上文字时，将呈现线面结果

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%9F%BA%E6%9C%AC%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8/images/20160918203117.png)

## Label中的超链接处理

通过[url =链接地址]显示内容[/url]对超链接进行设置，为Label添加Box Collider组件用于检测碰撞，然后通过编写程序处理超链接

```C#
 using UnityEngine;
  using System.Collections;

  public class Label : MonoBehaviour {
      void OnClick()
      {
          UILabel lbl = this.GetComponent<UILabel>();
          //获取鼠标点击位置出的超链接
          string url=lbl.GetUrlAtPosition(UICamera.lastHit.point);
          if(!string.IsNullOrEmpty(url))
              //打开超链接
              Application.OpenURL(url);
      }
  }
```

### 2. 按钮（UIButton）

按钮是制作UI过程中最核心的、最重要的空间之一。在游戏中，按钮是用户操作最依赖的控件，无处不在。

广泛地说，按钮的核心在于接收事件，任何可以接收事件的，都可以称作按钮。
对于按钮的交互处理，有很多种方式，下面给大家一一说明

#### 第一种方式

通过Inspector面板的On Click组件进行制定

在脚本中定义Public方法，然后将脚本挂载到某个游戏对象上，并将此对象拖拽到OnClick面板中，从Method选项中选择相应的方法。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%9F%BA%E6%9C%AC%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8/images/20160918161427.png)

#### 第二种方式

此方法与第一种方法类似，为按钮添加EventTrigger组件，每组事件都和第一种方法中的ONClick一样，然后采用第一种方法，为相应的事件添加方法调用。

* OnHoverOver

* OnHoverOut

* OnPress 鼠标左键按下

* OnRelease 鼠标左键松开

* OnSelect

* OnDeselect

* OnClick/Tap 鼠标点击或触屏点击

* ONDouble-Click/Tag 鼠标双击或触屏双击

* OnDragOver 按下鼠标拖动到按钮上

* OnDragOut 按下鼠标拖动到按钮外

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%9F%BA%E6%9C%AC%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8/images/20160918162404.png)

#### 第三种方式

这种方式是在脚本中编写固定的方法签名，然后将脚本挂载到按钮对象上。

```C#
using UnityEngine;
using System.Collections;

public class ButtonDemo : MonoBehaviour {

    void OnDrag(Vector2 delta){
        print("拖动"+delta);
    }
    void OnHover()
    {
        print("鼠标移上");
    }
    void OnClick(){
        print("点击");
    }

    void OnDoubleClick ()	{
        print("鼠标双击");
    }

}
```

#### 第四种方法

通过定义添加VoidDelegate的形式添加交互操作（仅限处理OnClick事件）

```C#
using UnityEngine;
using System.Collections;

public class ButtonDemo : MonoBehaviour {

    void Start () {
        //获取按钮组件
        UIButton btn = this.GetComponent<UIButton>();
        //创建委托
        EventDelegate dele1 = new EventDelegate(onBtnClickA);
        //将委托添加给按钮的Click
        btn.onClick.Add(dele1);
    }

    private void onBtnClickA()
    {
        print("按钮被点击了");
    }
}
```

#### 第五种方法

通过交互对象添加UIEventListener组件方式处理按钮多种相关事件。

```C#
using UnityEngine;
using System.Collections;

public class ButtonDemo : MonoBehaviour {
      void Start () {
          //为按钮添加UIEventListener组件,并处理点击事件
          UIEventListener ue = this.gameObject.AddComponent<UIEventListener>();
          //处理点击事件
          ue.onClick = onBtnClickA;
          
          //直接使用简写方式处理
        UIEventListener.Get(this.gameObject).onClick = onBtnClickB;
      }

      private void onBtnClickA(GameObject go)
      {
          print("按钮被点击了  onBtnClickA");
      }
    
}
```

对于Start的方法中，可以采用下面的简写方式

```C#
UIEventListener.Get(this.gameObject).onClick = onBtnClickB;
```

### 3. 输入文本（Input）

输入框是在Label的基础上扩展出来的一种组件，主要的用途是接收用户的输入文本，可以输入单行或者多行文本，常用于注册界面的数据检验。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%9F%BA%E6%9C%AC%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8/images/20160920172847.png)

### 4.滚动条，进度条(ScrollBar,Slider,Progress)

### 5. 单选框组件(Toggle)

制作Toggle按钮，通常需要用两个精灵来呈现，分别是背景图，选中时显示的图。方块图既为背景，对勾为选中是要显示的图。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%9F%BA%E6%9C%AC%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8/images/20160919171857.jpg)

### 6. 下拉表(Poplist)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%9F%BA%E6%9C%AC%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8/images/20160921100700.jpg)

```C#
public class PopListDemo : MonoBehaviour {

    private UIPopupList list;
	// Use this for initialization
	void Start () {
        list = this.GetComponent<UIPopupList>();
        //动态向options中添加项
        for (int i = 0; i < 3; i++)
        {
            //通过AddItem添加项
            list.AddItem("Item "+i);
            //通过RemoveItem删除项
            //list.RemoveItem("Item1");
        }
	}
}
```














