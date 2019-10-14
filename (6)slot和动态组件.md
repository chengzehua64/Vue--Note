## 复习一下组件：

   组件基本构成：template,script,style

## 组件slot:

 封装一个组件通常包括三个要素：
    1.props
    2.事件
    3.slot：vue官方文档：https://cn.vuejs.org/v2/guide/components-slots.html

     slot作用：提供一个组件占位符的作用，封装一个有共性，也带有差异性的的组件时比较常用

旧版本的slot:使用<slot></slot>提供占位符

       如果插件多个slot，通常给每个slot用name命名，以示区分
        例如：<slot name="back"></slot>

       嵌套数据：（vue官方也称内容分发）添加要分发的标签或组件

         <标签名或组件名 slot="上面定义的name名"></标签名或组件名>

         例如： <button slot="back">返回</button>

新版本的slot:使用<slot></slot>提供占位符,并通过name指定名称，这点和旧版本是一样的

       嵌套数据：通过template标签添加v-slot来调用上面的name名称 
       
         <template v-slot:name的名称></template>

         例如：
            <template v-slot:back>
                 <button>返回</button>
            </template>

## 动态组件（黄皮22页 ）
    
    1.动态组件：用于在交互过程中，动态引入的组件，主要通过component标签和is属性配合完成

    格式：<component :is="要加载的组件名"></component>

    例如：<component :is="currentTab"></component>


   注：keep-alive:主要用于缓存组件，保留组件内部数据状态

     格式： <keep-alive include="tabA,tabB">
               要缓存的组件
              </keep-alive>

     例如： <keep-alive include="tabA,tabB">
                <component :is="currentTab"></component>
              </keep-alive>

    注意：给keep-alive添加include和exclude设置包含或排除指定组件
     
## vue生命周期