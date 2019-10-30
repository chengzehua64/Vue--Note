## vuex:
  
  vue的全家桶包括什么：vue.js,vue-router,ES6,vuex,less/sass,
  你上家公司用的vue技术栈包括什么？vue.js,vue-router,ES6,vuex,less/sass,element ui,mint ui....

  你说一下你对vuex的理解:

     1.是一个管理数据的工具，集中管理数据状态
     2.适用场景：用于大中型项目，解决复杂组件之间传值混乱问题
     3.vuex有5个核心要素：

        （1）state
         (2) actions
         (3) mutations
         (4) getters
         (5) modules

    官方文档：https://vuex.vuejs.org/zh/

    建议安装vuex调试工具：但需要翻墙
    
    翻墙工具：https://github.com/getlantern/lantern

    安装好后打开https://chrome.google.com/webstore/search/vue?hl=zh-CN链接，将vue tools添加到chrome浏览器

    具体使用：

      安装vuex: npm insall vuex --save
    



      1.state:
         各组件如何获取vuex的公共数据：

        （1）this.$store.state.属性名

        （2）通过mapState来获取 【推荐】

      2.actions:是一种事件消息机制，不改变数据状态，是异步操作的方法

        例如：下课就是一个事件

        组件如何触发action事件消息，有两种：

        （1）this.$store.dispatch('action方法名')

        （2）通过mapActions辅助函数实现



      3.mutations:是最终改变数据状态的，是同步操作

      4.getters:相当于store的计算属性


          有两种实现方法：

        （1）this.$store.getters.属性

        （2）通过mapGetters辅助函数实现
    
      5.modules:可以实现对state状态树进行分类管理，让数据维护更加清晰

        例如：

            //引入需要的模块
            import Users from './modules/users'
            import Goods from './modules/goods'

            const store = new Vuex.Store({
            ....
                },
                modules: {
                    Users,
                    Goods,
                }
            });

            export default store;


            modules的state访问方式：

             (1) 通过this.$store.state.Users.属性名
            （2）通过mapGetters转换一下，来获取



   vuex组件触发流程：

     vue组件--dispatch-->actions---commit-->mutations---通过逻辑操作最终改变了state值-->从而更新了组件的状态


     vuex的模块化:5大核心以独立模块文件的形式存在，用时引入

     数据持久化：
     
      1.安装：npm install vuex-persistedstate
      2.使用：

        import createPersistedState from 'vuex-persistedstate'
 
        const store = new Vuex.Store({
        // ...
        plugins: [createPersistedState()]
        })
       
     
## Mock数据

  mock.js官方示例：http://mockjs.com/examples.html
  mock.js文档：https://github.com/nuysoft/Mock/wiki


 例如：

 Mock.mock({

   "success|1-2":true,
   "data|10":[{
         "id":"@id",  //模拟id
        "author_id":"@id",
        "tab|1":['ask','job','share','good'],  //数组中取1个
        "content":"@cparagraph",  //模拟段落
        "title":"@ctitle", //模拟标题
        "name":"@cname", //模拟中文名称
        "last_reply_at":"@datetime('yyyy-MM-dd A HH:mm:ss')",  //模拟日期时间
        "good|1":false,
        "toip|1":false,
        "reply_count|+1": 3,
        "visit_count|1": 555,
        "create_at": "@datetime('yyyy-MM-dd A HH:mm:ss')",
        "author":{
            "loginname":"@cname",
            "avatar_url":"@url"  //模拟网址,url


        },
       "imgurl":"@image('200x100','#f00','#000','vuejs')",  //模拟图片
        "imgurl|1":[
               'https://img11.360buyimg.com/n2/jfs/t1/1632/20/3511/140589/5b99c0adE686075a8/a0828e25d49e2eaf.jpg!q70.jpg.webp',
               'https://img14.360buyimg.com/n2/jfs/t1/84443/14/12846/189736/5d9df66fEebc0b47b/360c7f8d978f879a.jpg!q70.jpg.webp',
               'https://img10.360buyimg.com/n2/jfs/t1/58112/20/13690/259913/5da5a37bEf269000f/ffba9efc8c7904fc.jpg!q70.jpg.webp',
               'https://img10.360buyimg.com/n2/jfs/t1/60188/33/672/162527/5cee38d6E9e0181bc/f676a0b6eadeefec.jpg!q70.jpg.webp'
      ],
       "city":"@city(true)"  //模拟省市



   }]

})


  如何与vue集成，利用axios请求mock数据

  第一步：在项目上安装mockjs

     npm install mockjs --save

  第二步：在src目录下创建mock目录，分别创建如下文件并写入代码：

    index.js：

      import Mock from 'mockjs'

      //引入商品mock数据
      import goodsjson from './goods'
      import userjson from './user'
      import listjson from './list'


      //Mock.mock('请求接口地址','提交方式','请求的数据')

      Mock.mock('http://www.1902A.com/api/goods','get',goodsjson)
      Mock.mock('http://www.1902A.com/api/list','get',listjson)
      Mock.mock('http://www.1902A.com/api/user','get',userjson)

  第三步：在main.js中引入mock/index.js
  
    //引入store
    import store from './store'
    
