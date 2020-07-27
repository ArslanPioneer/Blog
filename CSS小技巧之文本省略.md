现在我们有一句诗“春江潮水连海平，海上明月共潮生”，希望只显示前半句，后半句以省略号来显示。
这里先给出答案

     <p>春江潮水连海平，海上明月共潮生。</p>
     
      p {
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
                font-size: 16px;
                width: 130px;
         }

![](https://user-gold-cdn.xitu.io/2019/3/19/169962da25331f64?w=227&h=45&f=png&s=1164)

text-overflow这个css属性是题眼，是确定如何向用户发出未显示的溢出内容信号，ellipsis正是在容器极限处进行截断来显示省略号。这个属性并不会强制“溢出”事件的发生，所以需要white-space:nowrap,这个属性使文字不能换行，overflow:hidden使其强制溢出。这时候我们在给容器一个固定宽度，自然整行文字就能按照我们的心意实现省略。

现在我们又有一段话“ 春天的江潮水势浩荡，与大海连成一片，一轮明月从海上升起，好像与潮水一起涌出来。

月光照耀着春江，随着波浪闪耀千万里，所有地方的春江都有明亮的月光。江水曲曲折折地绕着花草丛生的原野流淌，月光照射着开遍鲜花的树林好像细密的雪珠在闪烁。 ”

     div {
                width: 200px;
                display: -webkit-box;
                /* 显示几行 */
                -webkit-line-clamp: 4;
                -webkit-box-orient: vertical;
                overflow: hidden;
       }


![](https://user-gold-cdn.xitu.io/2019/3/19/169962de2eb28d8c?w=267&h=122&f=png&s=4999)


这里使用了WebKit的CSS扩展属性，该方法适用于WebKit浏览器及移动端

1. -webkit-line-clamp用来限制在一个块元素显示的文本的行数。 在这里我们显示4行
2. display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
3. -webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。

这是笔者日常的工作总结，从细微处深入，希望能给各位同学带来一点小小的收获，如果有帮助请关注我的个人公众号.
这是一个关注成长，关注技术，关注世界的暖心公众号。

![](https://user-gold-cdn.xitu.io/2019/3/19/169962e0a77929b8?w=430&h=430&f=jpeg&s=41740)