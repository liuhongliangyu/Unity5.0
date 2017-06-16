## 文本列表的简介

文本列表经常用于聊天内容的显示，访问记录的显示等，并按行的形式进行显示，如图所示

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8_%E6%96%87%E6%9C%AC%E5%88%97%E8%A1%A8TextList/images/20160919_01.bmp)

## 文本列表制作

由于文本主要是用来显示文本内容，所有需要借助一个Label组件，添加TextList组件。

1. 添加Label组件

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8_%E6%96%87%E6%9C%AC%E5%88%97%E8%A1%A8TextList/images/20160919163710.jpg)

2. 添加BoxCollider

3. 添加TextList组件，并把之前创建好的Label赋值给TextList属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8_%E6%96%87%E6%9C%AC%E5%88%97%E8%A1%A8TextList/images/20160919163909.jpg)

## 文本列表的常用属性

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8_%E6%96%87%E6%9C%AC%E5%88%97%E8%A1%A8TextList/images/20160919161436.jpg)

* TextLabel  用来显示文本内容的Label组件

* ScrollBar 指定滚动条

* Style 显示风格（分为Text文本和Chat聊天模式，默认为Text文本模式）

* Paragraph History 最多可以显示的行数（默认50行）

* scrollValue 文本滚动的值（0-1之间）0表示最久，1表示最新

通过鼠标左键点击，将文本滚动到可移动内容的一半位置

参考效果

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8_%E6%96%87%E6%9C%AC%E5%88%97%E8%A1%A8TextList/images/20160919164733.jpg)

```C#
void Update () {
      //鼠标点击时，将文本滚动到可滚动范围的一半位置
      if (Input.GetMouseButtonDown(0))
      {
          list.scrollValue = 0.5f;
      }
}

```

* Add ()向TextList中添加文本内容

下面通过Add方法，向TextList进行内容添加

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/17_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6%E5%BA%94%E7%94%A8_%E6%96%87%E6%9C%AC%E5%88%97%E8%A1%A8TextList/images/20160919164628.jpg)

```C#
using UnityEngine;
using System.Collections;

public class TextListDemo : MonoBehaviour {

    private UITextList list;
    // Use this for initialization
    void Start () {
          list = this.GetComponent<UITextList>();
          //动态为文本列表添加内容
          for (int i = 0; i < 20; i++)
          {
              list.Add("[ff0000]"+i+"[-]  line  "+i);
          }
    }
}
```

参考案例：

创建TextList并在开始时，将Chat字符添加到TextList中

```C#
using UnityEngine;				
using System.Collections;				

public class GetLabelValue: MonoBehaviour {				
    public UITextList TextList; //持有一个TextList的引用
    public string  Chat;//需要添加到TextList的字符内容
    void Update(){
       TextList.Add(Chat);//添加内容   	
    }			
}
```

