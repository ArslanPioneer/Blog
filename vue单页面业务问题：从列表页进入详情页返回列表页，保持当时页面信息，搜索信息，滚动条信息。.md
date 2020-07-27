vue单页面业务问题：从列表页进入详情页返回列表页，保持当时页面信息，搜索信息，滚动条信息。

刚开始是用vuex存储页面信息，后来发现太麻烦，不通用，后来经过掘金和CSDN博客的苦苦挖掘寻找，终于得到了以下两种解决方案。

关键在于keep-alive这个抽象组件，实际上不会被渲染在DOM树中。它的作用是在内存中缓存组件（不让组件销毁），等到下次渲染的时候，还会保持其中的状态，并且会触发钩子函数，常与router-view一起出现。

现在将业务问题抽象，A->B->C,A到B或者B到A都不需要页面缓存，而B是列表页查看详情到了C页，C页后退到B页则需要B页保持原来的页面信息。

1.在父页面进行路由渲染处如下设置

```vue
<!-- 需要页面缓存 -->
<keep-alive>
 	  <router-view v-if="$route.meta.keepAlive"></router-view>
 </keep-alive>
 <!-- 不需要页面缓存 -->
 <router-view v-if="!$route.meta.keepAlive"></router-view>
```

2.在vue-router下根文件处设置meta属性，keepAlive=true表示该页面需要缓存

```
  {
        path: '/mini',
        component: orderMini,
        name:'allMiniOrders',
        //添加meta
        meta: {
          keepAlive: true
        }
   },
```

3.在列表页组件中采用beforeRouterLeave这个路由守卫

```
 beforeRouteLeave(to, from, next) {
 	  //to: Route: 即将要进入的目标 路由对象
      //from: Route: 当前导航正要离开的路由
      //next: Function: 一定要调用该方法来 resolve 这个钩子。执行效果依赖 next 方法的调用参数。
 	  //当我们要去的页面不是详情页时
      if(to.name!=='orderMiniDetails'){
      //将当前页面的keepAlive设为false,表示现在这个页面不需要缓存了
        from.meta.keepAlive=false;
      }
      next();
  },
```

