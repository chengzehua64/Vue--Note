# 回顾一下昨天内容：
```
1.vue是什么：
2.vue怎么用：实例化

new Vue({
    el:xxx,  //挂载点
    data:xxx,  //初始化的数据
    methods:xxx  //方法，要处理的逻辑
})

```

3.常用指令：v-for,v-if,v-show,v-bind,v-on,v-model,v-cloak

v-cloak:为了防止网速慢，导致vue未加载完，页面上出现{{ }},用户体验不好，所以添加v-cloak

  具体加法：在标签上添加v-cloak，然后再样式中设置display:none;

  例如：

  ```
  标签上加v-cloak
     <ul v-cloak>
        <li v-for="(item,index) in chinainfo">
            {{ item }}---{{ index }}
        </li>
      </ul>


  在样式中添加:

    <style>
       [v-cloak] {
         display:none;
       }
    </style>
```

通常v-for要和key配合使用，key的作用：提高遍历性能

v-on修饰符：stop,prevent,native,once

stop：阻止事件冒泡
prevent:阻止事件默认行为

[面试会问]Vue响应式原理和$set

Vue响应式原理：主要利用ES5的Object.defineProperty()中的getter和setter来实现的

如果要让数据响应，必须放在将数据放在data对象中提前定义好，但如果后面新添加的属性，而不会响应，如果让后来添加的数据也响应呢？？？这回要请出$set来实现

$set:

```
格式：this.$set(要添加的对象，属性，值)
例如：this.$set(item,'num',1) 

```


#  计算属性和watch

  computed和methods区别：

    methods:每次触发方法都会执行中的代码
    computed:只要依赖项数据不发生改变，则不会执行其中代码（即有缓存数据的作用），直接返回，除非依赖项发生变化才执行其中代码

  computed适用场景：需要通过计算得到的值，这时才用计算属性比如：总价，评价总数

  watch:即监听,可以监听data和computed中数据的新旧的变化

  例如：

  ```

   watch:{
        title(newvalue,oldvalue) {
            console.log('oldvalue:',oldvalue)
            console.log('newvalue:',newvalue)
            if(newvalue>20) {
                alert('库存不足')
            }
        },
        total(newvalue,oldvalue) {
             if(newvalue>200) {
                alert('库存不足')
            }
        }

```


## 样式处理

  vue处理样式：class样式，行内样式

  1.class样式：
  
     （1）对象写法：例如：

     格式：<li  :class="{ hot:布尔值}">

     ```
        <li :class="{ hot:item.num>5}">
     ```
     （2）数组写法:适合添加多个类

     格式：<li  :class="[ 类1,类2,.... ]">


     总结：$set，计算属性，动态样式




