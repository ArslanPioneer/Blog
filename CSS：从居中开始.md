CSS：从居中开始

## 一、水平居中

#### 1.行内元素水平居中。

可以通过text-align:center,实现块级元素包裹的行内元素居中. 

```css
.parent {
            text-align: center;
        }
```

如果块级元素包裹着块级元素，可以通过display:inline-block，使块级元素转换成行内块元素，再使其居中。

```
  <div class="parent">
            <div class="child">
                demo
            </div>
   </div>

 .parent {
            text-align: center;
        }
  .child {
            display: inline-block;
         }
```

#### 2.块级元素水平居中

（1）

```
 .parent {
             /* 定宽 */
             width: 100px;
             margin: 0 auto;
         }
```

（2）table+margin

​	先将子元素设置为块级表格来显示，再将其设置为水平居中

```
<div class="parent">
            <div class="child">
                demo
            </div>
 </div>
 
  <style>
         .child {
             display: table;
             margin: 0 auto;
         }
 </style>
```

（3）absolute+margin

先将父元素设置为相对定位，再将子元素设置为绝对定位，向右移动子元素，移动的距离为父元素的一半，最后通过向左移动子元素的一半宽度，使其水平居中。

```
 .parent {
            position: relative;
        }
  .child {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
   }
```

（4）flex+justify-content

```css
 .parent {
            display: flex;
            /* 主轴元素对齐方式 */
            justify-content: center;
  }
         
```

(5) flex+margin

```
.parent {
        display: flex;
         }

.child {
         margin: 0 auto;
}
```

#### 3.多块级元素水平居中

父级元素采用flex布局，主轴上采用center,水平居中的方式排列

```
 <div class="container">
            <div>1</div>
            <div>2</div>
            <div>3</div>
 </div>
 <style>
        .container {
            display: flex;
            justify-content: center;
        }
         
  </style>
```

子级元素采用display:inline-block,父级元素使用text-align:center居中，实现水平居中

```
 <style>
        .container {
            text-align: center;
        }
        
        .child {
            display: inline-block;
        }
    </style>
```

4.浮动元素水平居中

```css
<style>
      .parent {
        display: flex;
        justify-content: center;
      }
      .chlid {
        float: left;
        width: 200px; 
      }
</style>

<div class="parent">
      <span class="chlid">我是要居中的浮动元素</span>
</div>
```



## 二、垂直居中

#### 1.单行内联元素垂直居中

```
 <div class="parent">
        <span class="child">单行内联元素垂直居中</span>
 </div>
 
 <style>
        .child {
            height: 120px;
            line-height: 120px;
            border:1px solid #ccc;
        }
    </style>
```

#### 2.多行内联元素垂直居中

flex布局

```
<div class="parent">
        <span class="child">春天的江潮水势浩荡，与大海连成一片，一轮明月从海上升起，好像与潮水一起涌出来。
                月光照耀着春江，随着波浪闪耀千万里，所有地方的春江都有明亮的月光。
                江水曲曲折折地绕着花草丛生的原野流淌，月光照射着开遍鲜花的树林好像细密的雪珠在闪烁。</span>
</div>
<style>
        .parent {
            height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            border: 1px solid #ccc;
        }
</style>

```

利用表布局

```
 <style>
        .parent {
            display: table;
            height: 140px;
            border: 1px solid #ccc;
        }
        .child {
            display: table-cell;
            vertical-align: middle;
        }
 </style>
```

#### 3.块级元素垂直居中

  （1）flex+align-items

```
<style>
        .parent {
            height: 200px;
            display: flex;
            align-items: center;
            border: 1px solid #ccc;
        }
</style>
 <div class="parent">
        <div class="child">未知高度的块级元素垂直居中。</div>
 </div>
```

(2) 使用absolute+transform

```
 <style>
      .parent {
        position: relative;
        height: 200px;
        border: 1px solid #333;
      }
      .chlid {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
      }
    </style>
<div class="parent">
    <div class="child">未知高度的块级元素垂直居中。</div>
</div>

```

(3)display:table-cell vertical-align:center

MDN:[CSS](https://developer.mozilla.org/en-US/docs/CSS) 的属性 **vertical-align** 用来指定行内元素（inline）或表格单元格（table-cell）元素的垂直对齐方式。

```
<style>
       .parent {
         height: 100px;
         border: 1px solid #333;
         display: table-cell;
         vertical-align: middle;
       }
 </style>
 <div class="parent">
      <div class="chlid">未知高度的垂直居中块级元素</div>
 </div>
```



## 三、水平垂直居中

#### （1）绝对定位与负边距

```
 <style>
        .parent {
            height: 800px;
            position: relative;
            border: 1px solid #ccc;
        }

        .child {
            position: absolute;
            width: 400px;
            height: 400px;
            left: 50%;
            top:50%;
            margin-left: -200px;
            margin-top: -200px;
            background-color: #ccc;
        }
    </style>
    
     <div class="parent">
        <div class="child">已知高度宽度的块级元素水平垂直居中。			</div>
    </div>
```

#### （2）margin auto

​	这种方法不需要知道块级元素的高宽，但在IE浏览器会有兼容问题

```
<div id="parent">
      <div id="child" style="width: 100px;height: 100px;background-color: #666">
        未知高宽的块级元素水平垂直居中
      </div>
</div>
 #parent {
        position: relative;
        height: 400px;
        border: 1px solid #ccc;
      }

      #child {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto;
      }
```

####   (3) transform

```
 <style>
      #parent {
        position: relative;
        height: 400px;
        border: 1px solid #ccc;
      }

      #child {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%,-50%);
      }
    </style>
    
   <div id="parent">
      <div id="child" style="width: 100px;height: 100px;background-color: #666">
        未知高宽的块级元素水平垂直居中
      </div>
    </div>
```

#### （4）flex布局

```
<style>
        .parent {
            height: 200px;
            width: 400px;
            display: flex;
            justify-content: center;
            align-items: center;
            border: 1px solid #ccc;
        }
 </style>
 
<div class="parent">
        <div class="child">未知高度的块级元素水平垂直居中。</div>
</div>
```

#### (5)grid布局

```
  <style>
        .parent {
            height: 400px;
            display: grid;
            border: 1px solid #ccc;
        }

        .child {
            margin: auto;
        }
    </style>
    
    
    <div class="parent">
        <div class="child">未知高度宽度的块级元素水平垂直居中。			</div>
    </div>
```

参考文章

- [【基础】这15种CSS居中的方式，你都用过哪几种？](https://segmentfault.com/a/1190000013966650)

- [最全面的水平垂直居中方案与flexbox布局](https://segmentfault.com/a/1190000011791428)

- [CSS3 Flexbox轻巧实现元素的水平居中和垂直居中](http://www.myexception.org/flex/2025243.html)

- [如何居中一个元素（正常、绝对定位、浮动元素)](https://blog.csdn.net/lxcao/article/details/52670724)

- [CSS布局解决方案（终结版）](https://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651553836&idx=1&sn=1f9e378e61908fd8c6c0fd81810b77fd&chksm=802557edb752defba9f1c2e462f7f09be0d1abbcbbdeb90007b80a6c4a78c855abbb5f291e39&mpshare=1&scene=1&srcid=0320rhs9ftYpIVK7WHOW2BoV#rd)

- [水平居中、垂直居中、水平垂直居中、浮动居中、绝对定位居中.......帮你搞定](https://segmentfault.com/a/1190000015095402)

  

   