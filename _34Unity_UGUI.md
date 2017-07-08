# 引语

在UGUI系统中，如果想显示一幅图片，可以使用Image和RawImage组件来实现。
Image:需要将图片类型指定为Sprite 2D And UI类型.
RawImage:直接使用Texture类型。

## Image

UGUI的Image等价于NGUI的Sprite组件，用于显示图片。
如果要使用Image显示图片，需要选中图片后，在Inspector面板中，将Texture Type的类型设定为
Sprite(2D and UI)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E5%9B%BE%E5%BD%A2%E7%BB%84%E4%BB%B6/images/20170422081550.jpg)

经过此次操作的，可以图图片拖动到Image组件的Source Image属性上去。

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/19_UI%E7%B3%BB%E7%BB%9F_UGUI%E5%9B%BE%E5%BD%A2%E7%BB%84%E4%BB%B6/images/20170422081812.jpg)

* Source Image（图像源）：纹理格式为Sprite（2D and UI）的图片资源（导入图片后选择Texture Type为Sprite（2D and UI））。

* Color（颜色）：图片叠加色。

* Material（材质）：图片叠加材质。

* Raycast Target（射线投射目标）：是否作为射线投射目标。

* Image Type（图片显示类型）：Simple（基本的），图片整张全显示，不裁切，不叠加，根据边框大小会有拉伸。

* Preserve Aspect（锁定比例）：针对Simple模式，勾选之后，无论图片的外形放大还是缩小，都会一直保持初始的长宽比例。

## RawImage

RawImage需要显示的图片必须为Texure类型。

