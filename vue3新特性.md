# vue3新特性
1. 虚拟节点引入 (重写虚拟DOM (Virtual DOM Rewrite))碎片化节点fragment
   - 把静态的节点进行提升,也就是说在应用第一次的启动被创建了一次后，
  之后这些虚拟节点会在每次渲染时候被不停的复用，这样就免去了重复的创建节点，
  大型应用会受益于这个改动，免去了重复的创建操作，优化了运行时候的内存占用。
  
2. vue3.0将组件的逻辑都写在了函数内部，setup()会取代vue2.x的data()函数，
  返回一个对象，暴露给模板，而且只在初始化的时候调用一次，因为值可以被跟踪。
 
3. 目前如果我们要在组件之间共享一些代码，则有两个可用的选择：
   - mixins 和作用域插槽（ scoped slots），但是它们都存在一些缺陷：
   - mixins 的最大缺点在于我们对它实际上添加到组件中的行为一无所知。
   这不仅使代码变得难以理解，而且还可能导致名称与现有属性和函数发生冲突。 
   - 通过使用作用域插槽，我们确切地知道可以通过 v-slot 属性访问了哪些属性，
   因此代码更容易理解。这种方法的缺点是我们只能在模板中访问它，
   并且只能在组件作用域内使用。
 
 4. tree shaking，需要用的功能模块会被打入包里

5. vue2中v-for与ref一起使用，批量模板引用的时候，获取的ref为一个数组,
vue3 中ref绑定的是一个函数，二者获取ref的dom方式有变化，但是获取的结果相同
    ```js
     <div v-for="i in 3" ref="setItemRef" :key="i">{{i}}</div> //这里是数组
     
     mounted() {
          console.log(this.$refs.setItemRef)
    },
    ```
6. 在vue3中引入了一个新的方法 --->defineAsyncComponent定义异步组件，
来包裹vue2引入方式里面的内容
```js
import { defineAsyncComponent } from 'vue'
         component: defineAsyncComponent(() => import('./NextPage.vue'))
```
7. 
 ```js
        <template v-for="(item,index) in qiTianData" :key="index">
            <qi-tian-weather></qi-tian-weather>
        </template>
```