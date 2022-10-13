---
title: VUE修饰符
date: 2022-09-06 10:59:30
tags:
- VUE修饰符
categories: 
- VUE
top_img: /img/cover2.jpg
cover: /img/cover2.jpg
---
## 一、表单修饰符
{% note %}
用在input标签上的v-model指令后，如v-model.lazy="value"
lazy（当光标离开标签时，才会将值赋值给value）
trim（过滤掉两边的空格）
number（自动将用户的输入值转为数值类型，但如果这个值无法被parseFloat解析，则会返回原来的值）
{% endnote %}
## 二、事件修饰符
{% note %}
对事件捕获以及目标进行处理：
stop
prevent
self
once
capture
passive
native
{% endnote %}
### stop
{% note %}
阻止事件的冒泡，相当于调用了event.preventPropagation方法
{% endnote %}
```
<div @click="shout(2)">
  <button @click.stop="shout(1)">ok</button>
</div>
//只输出1
```
### prevent
{% note %}
阻止了事件的默认行为，相当于调用了event.preventDefault方法
{% endnote %}
```
<form v-on:submit.prevent="onSubmit"></form>
```
### self
{% note %}
只当在 event.target 是当前元素自身时触发处理函数
{% endnote %}
```
<div v-on:click.self="doThat">...</div>
```
{% note %}
使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click. prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击
{% endnote %}
### once
{% note %}
绑定了事件以后只能触发一次，第二次就不会触发
{% endnote %}
```
<button @click.once="shout(1)">ok</button>
```
### capture
{% note %}
事件捕获，从顶层往下触发
{% endnote %}

```
<div @click.capture="shout(1)">
    obj1
<div @click.capture="shout(2)">
    obj2
<div @click="shout(3)">
    obj3
<div @click="shout(4)">
    obj4
</div>
</div>
</div>
</div>
// 输出结构: 1 2 4 3 
```
### passive
{% note %}
用于提升移动端scroll事件的性能。在移动端，当我们在监听元素滚动事件的时候，会一直触发onscroll事件会让我们的网页变卡，因此我们使用这个修饰符的时候，相当于给onscroll事件整了一个.lazy修饰符。
{% endnote %}
```
<!-- 滚动事件的默认行为 (即滚动行为) 将会立即触发 -->
<!-- 而不会等待 `onScroll` 完成  -->
<!-- 这其中包含 `event.preventDefault()` 的情况 -->
<div v-on:scroll.passive="onScroll">...</div>
```
### native
{% note %}
如果在自定义组件标签上绑定原生事件，则需要加上.native。
{% endnote %}
```
<button @click="add(this)">普通的html标签，不包含native的按钮</button><br/>
<button @click.native="add(this)">普通的html标签，包含native的按钮</button><br/>
<myself-button @click="add(this)"/></myself-button><br/>
<myself-button @click.native="add(this.id)"/></myself-button>
只有第一行和第四行的事件会生效。
```
## 三、鼠标按钮修饰符
```
<button @click.left="shout(1)">ok</button> //左键
<button @click.right="shout(1)">ok</button> //右键
<button @click.middle="shout(1)">ok</button> //中键
```
## 四、键盘修饰符
### 键盘修饰符是用来修饰键盘事件（onkeyup，onkeydown）的，有如下：
{% note %}
普通键（enter、tab、delete、space、esc、up...）
系统修饰键（ctrl、alt、meta、shift...）
{% endnote %}
```
// 只有按键为enter的时候才触发
<input type="text" @keyup.enter="shout()">
```
## 五、v-bind修饰符
### sync
{% note %}
实现子组件props的双向绑定
{% endnote %}
```
//父组件
<comp :myMessage.sync="bar"></comp> 
//子组件
this.$emit('update:myMessage',params);
```
相当于
```
//父亲组件
<comp :myMessage="bar" @update:myMessage="func"></comp>
func(e){
 this.bar = e;
}
//子组件js
func2(){
  this.$emit('update:myMessage',params);
}
```
{% note %}
使用sync的时候，子组件传递的事件名格式必须为update:value，其中value必须与子组件中props中声明的名称完全一致
注意带有 .sync 修饰符的 v-bind 不能和表达式一起使用
将 v-bind.sync 用在一个字面量的对象上，例如 v-bind.sync=”{ title: doc.title }”，是无法正常工作的
{% endnote %}
### props
{% note %}
设置自定义标签属性，避免暴露数据，防止污染HTML结构
{% endnote %}
```
<input id="uid" title="title1" value="1" :index.prop="index">
```
### camel
{% note %}
将命名变为驼峰命名法，如将 view-Box属性名转换为 viewBox
{% endnote %}