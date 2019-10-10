## vue-cli（即vue脚手架）

   1.vue-cli作用：统一开发标准，提高开发效率
   2.vue-cli安装：

      旧版安装：
       
        安装vue-cli npm install -g vue-cli

        检测vue-cli版本号： vue -V  2.9.x

        用vue-cli创建项目：vue init webpack 项目名（不能用中文）

          build
          config
          static
          src
          package.json

      新版安装：官方：https://cli.vuejs.org/zh/

        安装vue-cli npm install -g @vue/cli

        检测vue-cli版本号： vue -V  3.x

         用vue-cli创建项目：vue create 项目名

         UI方式创建管理项目：vue ui 回车 打开一个图形管理界面

## vue路由

 1.安装vue-router

 ```
  安装路由: npm install vue-router --save

  vue ui来安装路由：搜索vue-router，选定，点击安装即可

```

2.路由是什么：英文：router,通过路由可以分发，跳转到不同的位置

3.SPA是什么：SPA:Single Page Application,即单页面应用,通过路由技术实现在一个页面中展现对应的内容，提高打开速度

   缺点：不利于SEO

4.路由实现原理:无论是React,Vue,Angular，前端路由实现原理都是相同的，主要通过2点实现：

   1. hash+onhashchange实现
   2. H5的history的API实现：pushState(添加记录),replaceSate（替换一条记录）
    

    单页应用的  可以保存状态  

5.如何创建vue路由和使用:

   第一步：创建router并配置

      import Vue from 'vue'
      import VueRouter from 'vue-router'
      Vue.use(VueRouter) //挂载

      //引入要跳转的组件
      import Home from '../pages/home'
      import Cate from '../pages/cate'
      import Cart from '../pages/cart'
      import My from '../pages/my'


      //配置路由
      const routes = [
          {path:'/home',component:Home},
          {path:'/cate',component:Cate},
          {path:'/Cart',component:Cart},
          {path:'/my',component:My},
      ]



      //实例化路由
      const router = new VueRouter({
          routes
      })

      export default router;

      //注入到vue实例中，通过注入到main.js的vue中

        //引入路由配置
        import router from './router'

        new Vue({
          router,//注入到vue实现中
          ...
        }).$mount('#app')


  第二步：触发路由跳转

    1.标签方式： <router-link to="要跳转的路径" tag="修改默认标签">文字</router-link>

      默认标签：a
      tag:修改默认标签

    2.JS方式

  第三步：展现跳转对应的内容

    <router-view></router-view>


  如何添加高亮样式：vue-router有一个默认的高亮类： 

```
   .router-link-active { //高亮样式 }

```

   如果想修改默认的高亮类名，可以通过给vue实例配置添加高亮项目：
```
    //实例化路由
  const router = new VueRouter({
      routes,
      linkActiveClass:'active'  //配置高亮样式类名
  })
```

     


   

