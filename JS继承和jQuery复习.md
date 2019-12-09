## 跟前端相关的兼容问题

  html,css,javaScript

一、web兼容
  一）html:几乎没有，可能涉及H5相关标签在低版本的IE兼容问题

   面试官：说一下H5如果在IE低版本兼容?

     通常要引入html5shiv.js来解决低版本IE不兼容H5标签的问题，原理：通过createElement动态创建h5标签来实现的

  二）css兼容：主要针对IE

     1. 媒体查询hack @media 
     2. 属性和值hack
        
        *width:200px;  //只支持IE7及以下
        _width:200px;  //只支持IE6及以下
        _width:200px\0;

     3. 选择器hack

      *html .box {  }  //只支持IE6

      *+html .box {  }  //只支持IE7

     4. 条件注释 是由microsoft公司推出解决IE兼容的方案

       （1）判断等于IE某个版本：
       
           <!--[if ie 版本号]>  要解析的内容  <![endif]-->

       （2)判断大于等于某个版本

         <!--[if gte ie 版本号]>  要解析的内容  <![endif]-->

           gte: greater than equal 三个单词的首字母

        （3)判断小于等于某个版本

         <!--[if lte ie 版本号]>  要解析的内容  <![endif]-->

          lte: less than equal 三个单词的首字母 

        (4)非IE

     
      <![if !IE]>要解析的内容<![endif]>

      微软官方文档：https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537512(v=vs.85)?redirectedfrom=MSDN


  三）JavaScript兼容：

    检测html,css,js兼容浏览器情况：https://caniuse.com/

    主要利用是特性检测的方法
      if(document.querySelector) { ｝

      if(window.API方法) {  
        //如果支持就处理
      }
      else {

      }

//封装一个事件绑定的方法


function bindEvent(target,type,func) {
   //特性检测
    
    if (window.addEventListener) {
        //检测W3c标准
        target.addEventListener(type,func,false)
    } else if (window.attachEvent) {
        //检测IE的DOM2级
        target.attachEvent('on'+type,func)
    } else {
        //DOM0绑定
       //target['on'+type]=func
    }


}


//封装的一个解绑事件的方法
function removeEvent(target,type,func) {
    //特性检测
     
     if (window.removeEventListener) {
         //检测W3c标准
         target.removeEventListener(type,func,false)
     } else if (window.detachEvent) {
         //检测IE的DOM2级
         target.detachEvent('on'+type,func)
     } else {
         //DOM0绑定
         target['on' + type] = null;
     }
 
 
 }


＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝

一、节流和防抖实现

  onscroll
  mousemove
  keyup


  1.封装防抖代码：


function debounce(func, wait = 1000,immediate) {
    
    var timeout;

    return function () {
        //console.log(this)
        var _this = this;
        var _arg = arguments;
        clearTimeout(timeout);
        if (immediate) {
            
            var canNow = !timeout;

            timeout = setTimeout(function () {
                
                timeout = null;

            },wait)


            if (canNow) { func.apply(_this, _arg) }


        } else {
            timeout = setTimeout(function () {
            
                func.apply(_this,_arg)
    
            },wait)
        }
        
    }

}

 可以通过第三方工具库（lodash）处理节流和防抖

 官方地址：https://www.lodashjs.com/docs/latest

  underscore ->lodash

  2.节流实现

    
一、JS继承：

   1.JS是用函数来模拟一个类

    手机模型                  具体的手机
     类----------------->      对象

    function Person() {}    var p1=new Person()

    继承：

    function ChinaPerson() {} var c1=new ChinaPerson()

Person     父类，基类
ChinaPerson子类，派生类

  2.如何用JS实现继承，继承方法有哪些呢

    第一种：原生链继承:

     子类.prototype=new 父类()

    第二种：借用构造函数继承（类式继承）

    格式：
    //子类
    function 子类名(参数列表) {
        //类式继承，也称借用构造函数继承 主要利用call,apply
        父类.call(this,参数列表) 
        this.子类属性="值"
    }
    
     例如：
       //子类
    function ChinaPerson(name) {
        //类式继承，也称借用构造函数继承 主要利用call,apply
        Person.call(this,name) 
        this.skins="黄皮肤"
    }

    第三种：组合继承
 
      即是原型链和借用构造函数继承的组合体

    第四种：ES6的继承 class extends

     定义一个类：

       class 类名 {
         //构造器
         constructor(参数) {
            this.实例属性=值
         }

         原型方法1() {}
         原型方法2() {}
         原型方法3() {}

       }

       继承：
       class 子类名  extends 父类 {
         constructor() {
            super()
         }

         子类方法1() {}
         子类方法2() {}
         子类方法3() {}

       }
     

二、jQuery串讲：

  面试官常问的问题：

    jQuery与vue的区别：
    jQuery核心特点：
      1.抹平浏览器之间的差异（兼容各大主流浏览器）
      2.提供了好多浏览器不具备的API
        (1)查找选择器
       （2）查找dom方法
        (3)处理dom方法
        (4)ajax方法  $.ajax()
        (5)动画 slideUp(),slideDown(),fadeIn,fadeOut
  
    jQuery选择器有哪些:
    jQuery查找方法
    jQuery删除方法
    jQuery与原生dom的互转

    ===================

     1. jQuery的别名$
     2. $能干什么：创建，查找，加载函数，全局方法

       作用1：加载函数

       $(document).ready(function () {
    
         //写逻辑

        });

        简写：$(function() { 


         })
        
     作用1：查找选择器

      例如：$('.btn') 

     作用3:创建DOM

       $("<要创建的标签名>")

     作用4.全局方法  $.ajax,$.each

    3.jQuery与原生dom的互转

      jQuery对象不能用原生方法
      
      原生DOM对象也不能用JQuery

      转换方法：

        //jQuery对象转换成原生  
        
          $(选择器)[索引]或 $(选择器).get(索引)

  
       //原生DOM转换成jQuery对象  $(原生DOM)

    4.jQuery选择器：

       类选择器，标签选择器，id选择器,>,+,~,属性选择器,伪类/伪对象

       a>b 只选择a下一级的b
       a b 选择a所有的后代b
       a+b 选择器a后面相邻的b
       a~b 选择器a后面的兄弟b

   jQuery查找方法：

       eq(),类似于nth-child
       find():类似于 a b
       children() 类似于a>b
       filter() 
       parent():只找上一级
       parents()：找所有父级元素的集合
       cloest()：会首先检查当前元素是否匹配，如果匹配则直接返回元素本身。如果不匹配则向上查找父元素，一层一层往上，直到找到匹配选择器的元素。如果什么都没找到则返回一个空的jQuery对象。

  jQuery处理元素：追加，克隆(clone())，删除（empty,remove,detach）

  jQuery事件绑定.on

三、代码调试（html,css,js）通常指的是JS调试

   


  

        