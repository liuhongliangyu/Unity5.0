### Physic material物理材质

物理材质用来调节碰撞物体的摩擦力和弹力效果。要创建物理材质从Project面板中->Great->Physic Material.然后从Project面板中拖拽物理材质到场景上物体的碰撞器Material属性上。如图所示

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%89%A9%E7%90%86%E6%9D%90%E8%B4%A8/img/%E5%9B%BE%E7%89%8718.png)

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%89%A9%E7%90%86%E6%9D%90%E8%B4%A8/img/%E5%9B%BE%E7%89%8719.png)

### Physic Material属性

* 1. Dynamic Friction：动态摩擦力，通常值在0到1之间。值为0的效果像冰，而设为1时，物体运动将很快停止，除非有很大的外力或重力来推动它。

* 2. Static Friction:静态摩擦力，通常值在0到1之间。当物体在表面静止的摩擦力。当值为0时，效果像冰，当值为1时，使物体移动十分困难。

* 3. Bouncyness：表面的弹力（反弹系数）。0值将不反弹，1值反弹将没有任何能量损失。

* 4. Friction Combine Mode：摩擦力结合模式。定义两个碰撞物体的摩擦力是如何结合起来的，相互作用。

* 5. Average：平均值。使用两个摩擦力的均值

* 6. Min：最小值

* 7. Max：最大值

* 8、Multiply：相乘。使用两个摩擦力的乘积。

* 9. Friction Direction 2：摩擦力方向。给摩擦力加一个方向。如果该方向不为0，各向异性摩擦力被启用。 Dynamic Friction 2和Static Friction 2将被沿着Friction Direction 2应用。

* 10. Dynamic Friction 2：动态摩擦力 如果各向异性摩擦力被启用，DynamicFriction2将沿着Friction Direction 2应用。

* 11. Static Friction 2：静态摩擦力 如果各向异性摩擦力被启用，StaticFriction2将沿着Friction Direction 2应用。

常见的物理材质参数参考值：（可做一个斜坡，通过不同的立方体配置下面不同的物理材质，比较其下滑的摩擦顺畅效果）。

* 1. 反弹球：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%89%A9%E7%90%86%E6%9D%90%E8%B4%A8/img/%E5%9B%BE%E7%89%8720.png)

* 2. 冰面：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%89%A9%E7%90%86%E6%9D%90%E8%B4%A8/img/%E5%9B%BE%E7%89%8721.png)

* 3. 铁质：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%89%A9%E7%90%86%E6%9D%90%E8%B4%A8/img/%E5%9B%BE%E7%89%8722.png)

* 4. 木质：

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%89%A9%E7%90%86%E6%9D%90%E8%B4%A8/img/%E5%9B%BE%E7%89%8723.png)

要注意的是，添加物理材质，不论是使用反弹还是摩擦特性，都需要在两个接触的物体上都要添加Physic Material组件，要知道，力的作用是相互的。开发者往往在物体上添加了物理材质后，忘记在相接触的地板上也需要同样去添加物理组件，从而无法达到一个期望的效果。

#### 案例1-物理材质效果

利用一个Plane创建一个斜坡，然后再创建一个Sphere,并为Cube添加RigidBody.

1. 未添加物理材质效果

![](https://nts.newbieol.com/static/k25/02_%E6%B8%B8%E6%88%8F%E5%BC%95%E6%93%8E%E6%A0%B8%E5%BF%83/11_%E7%89%A9%E7%90%86%E7%B3%BB%E7%BB%9F_%E7%89%A9%E7%90%86%E6%9D%90%E8%B4%A8/img/20170404_01.gif)

为Plane和Sphere添加物理材质

