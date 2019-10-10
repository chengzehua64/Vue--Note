# vue过滤器
  
  1、vue过滤器是什么：即用于进行数据格式转换的方法

  2、使用场景：例如：性别的处理，货币的处理，字母大小写，日期的处理处理等

  3、具体实现：

    创建过滤器：
     （1）全局过滤器：

        //Vue.filter('过滤器名称',函数);

        Vue.filter('过滤器名称',function(v1,v2,...vn) {
            //过滤器的逻辑处理
            .....

        });

        例如：

        //定义一个性别过滤器
        Vue.filter('sexy',function(v1) {

        return v1==0 ? '有货':'无货'

        })
        
    （2）局部过滤器：通过在Vue的实例对象中添加filters属性来实现局部过滤器的

     格式：
        new Vue({
           ....
           filters:{
               过滤器名1() {},
               过滤器名2() {},

           }
           .....

        })


     例如：
      new Vue({
           ....
            filters:{
                currency(v1,type) {
                    //将小数部分保留2位
                    v1=v1.toFixed(2);
                    
                    //处理千分分隔；
                    result=("" + v1).replace(/(\d{1,3})(?=(\d{3})+(?:$|\.))/g, "$1,");
                    //result=(result*1).toFixed(2)

                    //最后返回带货币的千分分隔数据；
                    return type+result;
                },
                sexy(v1) {
                return v1==0 ? '有货':'无货'

                }
            }
        ....

        })



    如何使用？？ {{ 要处理的数据 | 过滤器(参数1，参数2，...，参数n) }}

    例如：   <p>{{ item.sex | sexy }}</p>


# vue自定义指令：

  vue内置指令：v-for,v-if,v-on,v-show,v-bind,v-model......,v-html,v-text...

    1、vue自定义指令是什么：提供了除内置指令外，封装dom操作所需要的指令

    2、使用场景：自动获取焦点，拖拽等。。。

    3、具体实现：

       创建：
         全局自定义指令：

            Vue.directive('指令名',{

                inserted() {

                }

            });
           
         局部自定义指令：通过在Vue的实例对象中添加directives属性来实现局部自定义指令的

         new Vue({
           ....
            directives:{
                 focus:{
                    inserted(el) {
                        console.log('el::::',el);
                        el.focus();

                    }
                }
            }
        ....

        })


       调用：v-指令名

# vue-cli(即vue脚手架)