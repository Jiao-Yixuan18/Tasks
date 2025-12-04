# CSS学习笔记

> ——焦怡煖

## 学习背景

已学习HTML基础

## 学习内容的目录

CSS笔记补充

## 学习内容

> 这里是对菜鸟教程中没有提及的内容的补充

#### 字体大小

chorme浏览器能接收的最小字体是12px

#### 外边框

margin-简写属性：

四个值：上右下左

三个值：上 左右 下

两个值：上下 左右

一个值：全都一样

> t填充（padding）-简写属性同上

### transform 

`transform`属性用于对元素进行 2D 或 3D 变换，包括旋转、缩放、平移、倾斜等操作，通过改变元素的坐标空间实现视觉效果。

常用变换函数：

translate(x, y)：平移元素，x 为水平位移，y 为垂直位移。

translate3d(x, y, z) / translateX() / translateY() / translateZ()：在三维空间中沿指定轴平移。

rotate(angle)：2D 旋转，angle 为角度（正值顺时针，负值逆时针）。

rotate3d(x, y, z, angle) / rotateX() / rotateY() / rotateZ()：绕指定轴进行 3D 旋转。

scale(x, y)：缩放元素，x 为水平缩放倍数，y 为垂直缩放倍数。

scale3d(x, y, z) / scaleX() / scaleY() / scaleZ()：三维缩放。

skew(x-angle, y-angle)：倾斜元素，分别指定水平和垂直方向的倾斜角度。

skewX(angle) / skewY(angle)：单轴倾斜。

matrix(a, b, c, d, tx, ty)：通过 2D 矩阵实现组合变换。

matrix3d(...)：通过 4x4 矩阵实现 3D 变换。

perspective(length)：设置透视距离，用于 3D 效果。

代码示例：

```css
/* 平移 + 旋转 */
box1 {
 transform: translate(50px, 20px) rotate(30deg);
}
/* 3D 缩放 + 旋转 */
box2 {
 transform: scale3d(1.2, 1.2, 1) rotateY(45deg);
}
/* 倾斜 */
box3 {
 transform: skewX(20deg);
}
```
注意事项：

* 多个变换函数可组合使用，按从左到右的顺序书写，但实际应用顺序为从右到左。

* transform 会创建新的 层叠上下文，影响 z-index 计算。

* 对无障碍用户，应避免过度缩放或旋转动画，可结合 prefers-reduced-motion 媒体查询优化体验。

## 参考资料

1. [菜鸟教程-CSS教程](https://www.runoob.com/css/css-tutorial.html)

2. [B站视频](https://www.bilibili.com/video/BV1oz421q7BB/?spm_id_from=333.1387.favlist.content.click&vd_source=6aba70bfaeecdb8314d86a42c169cfd0)

