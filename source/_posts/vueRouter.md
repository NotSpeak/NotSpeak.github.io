---
title: VUE路由
date: 2022-09-06 13:02:30
tags:
- VUE路由
categories: 
- VUE
top_img: /img/cover5.jpg
cover: /img/cover5.jpg
---
## 一、vue-router的理解
{% note %}
首先，需要理解一下vue-router：
vue-router是vue的一个插件，专门用来实现SPA应用。SPA也就是单页Web应用，特点是：整个应
用只有一个完整的页面，点击页面中的导航链接不会刷新页面，只会做页面的局部更新，数据需要
通过ajax请求获取。
{% endnote %}
## 二、路由的理解
### 什么是路由：
{% note %}
1、一个路由就是一组映射关系（key-value）
2、key为路径，value可能是function或component
{% endnote %}
### 路由的分类：
{% note %}
1、后端路由
（1）理解：value是function，用于处理客户端提交的请求。
（2）工作过程：服务器接收到一个请求时，根据请求路径找到匹配的函数来处理请求，返回响应数据。
2、前端路由
（1）理解：value是component，用于展示页面内容。
（2）工作过程：当浏览器的路径改变时，对应的组件就会显示。
{% endnote %}
## 三、路由基本使用
{% note %}
首先需要在main.js中配置路由：
{% endnote %}
```
import Vue from 'vue'

import App from './App.vue'

import VueRouter from 'vue-router'

import router from './router'

Vue.config.productionTip = false

Vue.use(VueRouter)

new Vue({

el:'#app',

render: h => h(App),

router:router

}).$mount('#app')
```
### 实现切换（active-class可配置高亮样式）：
```
 <router-link to="/about"  active-class="active">About</router-link>

（<router-link>的replace属性：
```
{% note %}
1、作用：控制路由跳转时操作浏览器历史记录的模式；

2、浏览器的历史记录有两种写入模式：分别为push和replace，push是追加历史记录，replace是替换当前记录，路由跳转时候默认为push；

3、直接在<router-link>添加replace即可。）
{% endnote %}
### 指定显示位置：
<!-- 指定组件的呈现位置 -->
```
<router-view></router-view>
```
### 几个注意点：
{% note %}
1、路由组件通常存放在pages文件夹，一般组件通常存放在components文件夹；

2、通过切换，“隐藏”了的路由组件，默认是被销毁掉的，需要的时候再去挂载；

3、每个组件都有自己的$route属性，里面存储着自己的路由信息；

4、整个应用只有一个router，可以通过组件的$router属性获取到。
{% endnote %}
## 四、多级（嵌套）路由 
{% note %}
1、配置路由规则，使用children配置项：
{% endnote %}
```
 routes:[

        {

            path:'/about',

            component:About

        },

        {

            path:'/home',

            component:Home,

            children:[

                {

                    path:'news',

                    component:News

                },

                {

                    path:'message',

                    component:Message

                }

            ]

        }

    ]
```
{% note %}
2、跳转的时候要写完整路径：
{% endnote %}
```
<router-link class="list-group-item" to="/home/news" active-class="active">News</router-link>
```
## 五、路由的query参数
{% note %}
1、传递参数
{% endnote %}
```
<router-link :to="{

    path:'/home/message/details',

    query:{

        id:m.id,

        title:m.title

    }

  }">

    {{m.title}}

</router-link>
```
{% note %}
2、接收参数
{% endnote %}
```
<li>消息编号：{{$route.query.id}}</li>

<li>消息标题：{{$route.query.title}}</li>
```
## 六、路由的params参数
{% note %}
1、配置路由，声明接收params参数
{% endnote %}
```
routes:[

        {

            path:'/about',

            component:About

        },

        {

            path:'/home',

            component:Home,

            children:[

                {

                    path:'news',

                    component:News

                },

                {

                    path:'message',

                    component:Message,

                    children:[

                        {

                            name:'xiangqing',//必须通过name的方式找到details

                            path:'details',//使用占位符声明接收params参数

                            component:Details

                        }

                    ]

                }

            ]

        }

    ]
```
{% note %}
2、传递参数
{% endnote %}
```
<li v-for="m in messageList" :key="m.id">

    <!-- 跳转字符并携带params参数 to的字符串写法 -->

    <!-- <router-link :to="/home/message/details/666/hello">{{m.title}}</router-link> -->

    <!-- 跳转字符并携带params参数 to的对象写法 -->

    <router-link :to="{

        name:'xiangqing',//必须用name配置

        params:{

            id:m.id,

            title:m.title

        }

      }">

        {{m.title}}</router-link>

</li>
```
{% note %}
3、接收参数
{% endnote %}
```
<li>消息编号：{{$route.params.id}}</li>

<li>消息标题：{{$route.params.title}}</li>
```
## 七、编程式路由
{% note %}
1、作用：不借助<router-link>实现路由模块，让路由跳转更灵活
2、编码：
{% endnote %}
```
<button @click="pushShow(m)">push查看</button>

<button @click="replaceShow(m)">replace查看</button>

methods:{

    pushShow(m){

        this.$router.push({

            name:'xiangqing',

            query:{

                id:m.id,

                title:m.title

            }

        })

    },

    replaceShow(m){

        this.$router.replace({

            name:'xiangqing',

            query:{

                id:m.id,

                title:m.title

            }

        })

    }

    }
```
## 八、缓存路由组件
{% note %}
1、作用：让不展示的路由组件保持挂载，不被销毁。
2、具体代码：
{% endnote %}
```
<keep-alive include="News">
    <router-view></router-view>
</keep-alive>
```
## 九、两个新的生命周期钩子
{% note %}
1、作用：路由组件所独有的两个钩子，用于捕获路由组件的激活状态。
2、具体名字：
actived：路由组件被激活时触发；
deactived：路由组件失活时触发。
{% endnote %}
## 十、路由守卫
{% note %}
1、作用：对路由进行权限控制；
2、分类：全局守卫、独享守卫、组件内守卫；
3、全局守卫：
全局前置守卫，初始化时执行，每次路由切换前执行
{% endnote %}
```
router.beforeEach((to,from,next)=>{

    if(to.meta.isAuth){//判断是否需要鉴权

        if(localStorage.getItem('school')==='hkd'){

            next()
        }
    }
    else{
        next()
    } 
})
```
{% note %}
全局后置路由守卫，初始化时执行，每次路由切换之后被调用
{% endnote %}
```
router.afterEach(()=>{

    if(to.meta.isAuth){//判断是否需要鉴权

        document.title=to.meta.title

    }

    else{

        document.title='vue_test'

    }

})
```
{% note %}
4、独享路由守卫：某一个路由所独享的；
{% endnote %}
```
beforeEnter:(to,from,next)=>{

    if(to.meta.isAuth){//判断是否需要鉴权

        if(localStorage.getItem('school')==='hkd'){

            next()

        }

    }

    else{

        next()

    }

}
```
{% note %}
5、组件内路由守卫
//通过路由规则进入该组件时调用
{% endnote %}
```
    beforeRouteEnter(to,from,next){

      console.log('beforeRouteEnter');

      if(to.meta.isAuth){//判断是否需要鉴权

        if(localStorage.getItem('school')==='hkd'){

                next()
            }
        }
        else{
            next()
        }
    },
```
{% note %}
//通过路由规则离开该组件时调用
{% endnote %}
```
    beforeRouteLeave(to,from,next){

      next()

    }
```