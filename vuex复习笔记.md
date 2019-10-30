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
       
     

