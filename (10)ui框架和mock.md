## UI框架

 1.UI框架简介：
 适合PC端：element UI等

 适合移动端：mint ui,muse ui等

 参考：

 Element UI框架官网：https://element.eleme.io/#/zh-CN
 第三方：https://www.cnblogs.com/sunsets/p/10093157.html

 2.Element UI框架的基本使用：

   第一步：安装element UI:

    npm install element-ui -S

   第二步：在main.js中引入element ui和css

     ...

        import ElementUI from 'element-ui';
        import 'element-ui/lib/theme-chalk/index.css';

        Vue.use(ElementUI);

        ...

        实现按需加载组件：

          新版vue-cli@3.x加载：
          
            第一步：vue add element
            第二步：在main.js中引入需要的组件

            例 如：

            import { Switch } from 'element-ui'

            Vue.use(Switch);

  2.vue路由懒加载

    vue路由懒加载：

       目的：主要为了解决打包文件过大的问题，从而提高首屏加载的速度，提高加载性能

       写法：const 组件名=()=>import('要引入的组件路径')


  3.vuex持久化：

     vuex数据持久化的原理：主要用的是本地存储:localStorage

     可以通过第三方vuex存储插件来解决：

       第一步：npm install vuex-persistedstate;

       第二步：在vuex的store中的inddex.js文件中引入：

        import createPersistedState from 'vuex-persistedstate'

       第三步：在vuex实例化中通过plugins来调用此插件

       例如：

        export default new Vuex.Store({
                ....
                plugins: [createPersistedState()]
        })
        

    基于vue封装的swiper插件：https://github.com/surmon-china/vue-awesome-swiper


  ## Mock数据

   1.返回数据板式：json,xml 

   2.mock.js基本使用: 官方： http://mockjs.com/examples.html#Date

     数据模板中的每个属性由 3 部分构成：属性名、生成规则、属性值：

    // 属性名   name
    // 生成规则 rule
    // 属性值   value

    'name|rule': value


    占位符 只是在属性值字符串中占个位置，并不出现在最终的属性值中。

      占位符 的格式为：

      @占位符   例如：@date(),@url,@email,@ctitle,@cparagraph @city ...

      @占位符(参数 [, 参数])


    let jsondata=Mock.mock({
  "success|2":true,
  "data|5":[
      {
         "id|+1":100,
         "tab|1":['ask','job','good'],
         "content":"@cparagraph",
         "title":"@ctitle(5)",
         "last_reply_at":"@date('yyyy年MM月dd日') @time('HH:mm:ss')",
         "author":{
             "loginname":"@cname",
             "avatar_url":"@url"

         },
        "city":"@city(true)",
        "email":"@email",
        "imgurl":"@image('200x100','#ccc','hello,vuejs')"
     }

   ]
})


 3.vue如何集成mockjs

   第一步：安装mockjs

     npm install mockjs

  第二步：在src下创建一个mock目录，在其中创建需要mock的数据，最终通过index.js文件引入

      例如：goods.js

import Mock from 'mockjs';

let jsondata=Mock.mock({
  "success|2":true,
  "data|5":[
      {
         "id|+1":100,
         "tab|1":['ask','job','good'],
          .....
     }

   ]
})

export default jsondata;


  打开mock/index.js

   import Mock from 'mockjs';

   import goods from './goods'  //引入模板数据


   Mock.mock('http://www.1902A.com/goods','get',goods);

   export default Mock;
 

  第三步：在main.js注入mock/index.js

    //引入mock数据
    import './mock'

  

    

  