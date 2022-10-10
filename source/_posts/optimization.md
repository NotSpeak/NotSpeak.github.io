---
title: 前端性能优化
date: 2022-10-10 14:01:25
tags:
- 前端性能优化
categories:
- 前端
top_img: /img/cover2.jpg
cover: /img/cover2.jpg
---
## 前端性能优化
### 如何优化请求
#### 图片方面
#### ① 精灵图
通过 background-position 来取每个图标位置，最后每个图标
===>
优势 :
一次请求，多次利用 （ 减少请求频率 ）
👇
![精灵图](/img/jingling.png)
#### ② 小图标 Base64
虽然 内存没有减小 ，存储为超长的字符串码
但是不用请求各种小图标 （ 减少请求频率）
应用 （webpack 打包配置）
下载插件：👇
npm i -D url-loader
配置打包： 👇
```
module: {
  rules: [
       {
        test: /\.(jpeg|jpg|png|svg|gif)$/,
        use: {
          loader: 'url-loader', // 默认使用的是es6模块
          options: { // 配置 
            esModule: false, // 使用common.js规范
            outputPath: 'images', // 输出的文件目录
            name: 'images/[contenthash:4].[ext]',
            limit: 10*1024 // 小于10k转为base64
          }
        }
      }
  ]
}
```
#### ③ 图片懒加载
电商系统，最为常用；
原理： 👇
滚动到图片位置，再去请求图片
这样浏览多少，加载多少 （ 按需请求 ）
简单实现： 👇
```
<body>
    <img data-a="./img/1.jpg" alt="">
    <img data-a="./img/2.jpg" alt="">
    <img data-a="./img/3.jpg" alt="">
    <img data-a="./img/4.jpg" alt="">
    <img data-a="./img/5.jpg" alt="">
 </body>
<script>
        const imgs = document.getElementsByTagName('img');
	  	window.onload = window.onscroll = function () { 
            gundong(imgs);
        }
		function gundong(imgs) {
            let height = document.documentElement.clientHeight;
          	let s = document.documentElement.scrollTop || document.body.scrollTop;	
            for (let i = 0; i < imgs.length; i++) {
                if (hight + s > getTop(imgs[i])) {
                    imgs[i].src = imgs[i].getAttribute('data-a');
                }
            }
        }
        function getTop(e) {  //计算到浏览器顶部的距离
            let ss = e.offsetTop;
            while(e = e.offsetParent) {
               ss += e.offsetTop;
            }
            return ss;
        }
 </script>
```
#### ④ 图标库 采用 svg
svg 是 HTML5 新增的 矢量图 （ 减少请求 ）
svg 图标占用内存非常小
将图标库，选择svg类型图标库
推荐： 👇
Iconify 图标库 ( 包含 Antd、Element ui …的图标 )
安装：👇
npm i -D @iconify/json
地址：👇
点击跳转（开源免费） https://icon-sets.iconify.design/
请求内容方面
##### ① 减少请求内容大小
每次请求的数据不要太大
表格和列表 类型 后端分页 👇
— 分页尽量后端处理
— 前端传参 ，每次请求每页数据 （ 加快请求响应速度 ）
…
##### ②更改请求方式
对于获取 表格、或列表内容 ，尽量 get 请求
获取表格， 一般只会传 页码和大小、类型 （ 不会涉及重要参数）
get 请求的 速度 > post 请求 速度
##### ③ 防抖节流
防抖：👇例子
表单 点击按钮提交时，然后 几秒内，按钮 不能被点击或点击无效，避免过快重复点击
、、、
节流：👇 例子
搜索框匹配内容时，用户 停止输入到 几秒时去搜索，而不是输入一个 触发一次
##### ④ 利用存储
本地存储 ：
cookie、localStorage、sessionStorage
场景：👇
1、第一次请求后，存储到本地，下次发送请求，后端判断数据是否更新，如果不更新不返回数据；
2、用户登录 将token 存储 cookie ，再访问改网页token未过期，则不需要重新登录；
### 代码优化
#### ① 事件委托
给 父标签 绑定点击事件
点击 子标签 同样会执行该函数
举个简单的例子： 👇
```
<body>
	<ul onclick="fun(event)">
    	<li>111</li>
    	<li>222</li>
    	<li>333</li>
	</ul>
</body>
<script>
function fun(e){
    console.log(e.target.innerHTML);
}
</script>
```
#### ② 减少dom操作
少 通过 document 来获取对象 如：👇
document.getElementsByClassName( ‘content’ ).innerHTML = 123
因为同时操作多个标签 => 大量的 重绘 或 重排
可以使用流行的框架 👇
如： vue 、react 都采用 虚拟dom ，多次操作一次渲染
#### ③ 页面结构优化
将script标签放到最后面可以提前解析DNS资源。
#### ④ css 优化
选择器准确可以减少匹配的时间。
如 ： .box>.header_box>.content{ … }
less 和 sass 可以层级嵌套 会 加快匹配时间
如 👇
```
<style lang="less">
.box{
	...
	.header_box{
		...
		.content{
			...
		}
	}
}
</style>
```
### 框架和打包
#### ① SSR 服务端渲染
页面在服务端直接渲染成 HTML 字符串，作为服务端响应返回给浏览器，最后在浏览器端将生成静态的 HTML
优势：
 · 首次加载速度快 ，利于SEO
劣势：
 · 不支持路由懒加载 ，
 · 适合页面较少 ，
 · 服务端压力过大
nuxt 是一个SSR 最为流行的框架之一 基于vue 👇
点击了解 nuxt https://v3.nuxtjs.org/

#### ② CDN 加速
CDN 加速就是将 依赖部署在其他站点上，而不是把资源打包到项目中 。
不需要 npm 或 yarn 下载 ，只需要html 文件的 头部去导入 👇
```
<body>
    <div id="app"></div>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/3.1.5/vue.global.min.js"></script>
</body>
```
```
// webpack.config .js
module.exports = {
    chainWebpack: config => {
       config.externals({
           'vue': 'Vue',
       })
     },
}
```
优势：
 · 这种 非常适合带宽比较小的服务器
 · 打包会更加小
劣势：
 · 如果 服务器不差，CDN 加速反而会变慢
 · 请求的依赖包是全量的，没有按需加载
#### ③ tree-shaking (摇树优化)
摇树优化 ：顾名思义就是要掉，身上多余的东西
就是打包的时候 ，依赖中没用到的功能，就不打进去
让生产环境的包足够小 👇
向vue 、react 都自带这种功能
#### ④ js 最小拆包
进入每个子页面加载每次用到的 js 逻辑
可以通过 webpack 和 vite 的配置实现
#### ⑤ 路由懒加载
在进入那个路由，加在对应的逻辑
在 vue 和 react 中 应用 👇
```
vue 采用 () => import('/...') 来导入
---
react 采用 React.lazy(() => import('/...'))
```
#### ⑥ 异步组件，异步Js
如果有的组件，是通过点击 和 操作之后出现的
这时就可以通过 异步组件和异步Js
实现 功能按需加载 已vue 为例：👇
```
import { defineAsyncComponent } from 'vue'
const Foo = defineAsyncComponent(() => import('./Foo.vue'))
```
```
function loadLazy() {
  return import('./lazy.js')
}
```
