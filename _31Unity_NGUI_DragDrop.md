# 拖动的实现

如果实现一个UI的可以拖动，只要在需要拖动的UI元素上添加上BoxCollider和UIDragAndDopItem便可以实现拖动。

# 如果处理拖动和释放

如果对拖动过程进行操作，那我们就需要新建类，并集成UIDragDropItem类，在新类中通过重写相应的方法来实现。

在我们拖动过程中到底发生了什么事情，有哪些方法被调用了呢？

下面是拖动过程中调用的方法，按实际顺序排列(标红项重要)

* OnPress(bool isPressed) 拖动对象是否被按下，按下为true,松开为false

* OnDragDropStart 拖动释放开始

* StartDraging 拖动开始

* OnDragStart() 开始拖动

* OnDragDropMove(Vector2 delta) 拖动释放操作移动

* OnDrag(Vector2 delta) 拖动中

* OnDragDropEnd() 拖动释放结束

* OnDragDropRelease(GameObject surface) 拖动物体被释放 

* OnDragEnd() 拖动结束

* OnPress(bool isPress)

OnDragDropRelease(GameObject surface)
使用此方法可以对鼠标松开那一刻进行处理

## 拖动案例一

松开鼠标时，如果松开是，与影子重合，及设置花与影子在同一位置，此时shadow和flower都有BoxCollider,flower有MyDragItem（代码如下)

```C#
using UnityEngine;
using System.Collections;
public class MyDragItem : UIDragDropItem {
    protected override void OnDragDropRelease(GameObject surface)
    {
        base.OnDragDropRelease(surface);
        //如果释放拖拽物体下面UI有碰撞体，并且名称为shadow,则将拖动的物体与shadow位置设为一样
        if (surface!=null && surface.name=="shadow")
        {
            this.transform.localPosition = surface.transform.localPosition;
        }
    }
}
```

## 拖动案例二

在上一个案例的基础上，为shadow添加DragDropContainer组件，花添加DragDropItem组件，花会自动进入到Shadow游戏对象中去（可以不用编写任何代码）

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/18_NGUI%E5%A4%8D%E5%90%88%E7%BB%84%E4%BB%B6_%E6%8B%96%E5%8A%A8DragDrop/images/2016092006345.bmp)
