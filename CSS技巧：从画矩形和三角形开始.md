```css
<div class="box"></div>
<style>
      .box {
        width: 0;
        height: 0;
        border: 100px solid #ccc;
      }
</style>
```

![1595773096591](C:\Users\Arslan\AppData\Roaming\Typora\typora-user-images\1595773096591.png)

我们会得到一个width:200px height:200px 的矩形

而border:100px solid #ccc;这句代码其实相当于

```
border-top: 100px solid red;
border-left: 100px solid green;
border-bottom: 100px solid yellow;
border-right: 100px solid pink;
```

![1595773505260](C:\Users\Arslan\AppData\Roaming\Typora\typora-user-images\1595773505260.png)

接下来我们实现下三角形就很容易了，border-bottom不设置，border-left,border-right背景色设置为transparent.

![1595774438652](C:\Users\Arslan\AppData\Roaming\Typora\typora-user-images\1595774438652.png)

```
 .bottomTriangle {
        width: 0;
        height: 0;
        border-top: 100px solid red;
        border-left: 100px solid transparent;
        border-right: 100px solid transparent;
 }
```

照葫芦画瓢我们可以依次实现左三角形、右三角形、上三角形

接下来我们要升级了，实现一个实心\空心三角指示箭头。

实心三角形视觉上没有边框，空心三角形视觉上有边框。

> 空心三角形的原理是一个边框颜色的三角形绝对定位到主体元素边界处并连接起来，然后另一个主体元素背景色的三角形绝对定位并覆盖到第一个三角形上面，关键的一点是第二个三角形相较于第一个三角形定位上偏移的距离应等于边框宽度。

