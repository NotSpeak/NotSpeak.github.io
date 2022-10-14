---
title: VUE生命周期
date: 2022-09-06 14:42:47
tags: 
- VUE生命周期
categories: 
- VUE
top_img: /img/cover4.jpg
cover: /img/cover4.jpg
---
## Vue生命周期详解
### 什么是生命周期?
{% note info no-icon%}
1.Vue实例从创建到销毁的这一过程叫做vue的生命周期.
2.过程:开始创建—>初始化数据—>编辑模板—>挂载DOM($el)---->UI渲染—>数据更新---->卸载
{% endnote %}
Vue的生命周期分为四个阶段
大家看这张图：
![vue生命周期图](/img/cycel.png)

### 生命周期四大阶段：
{% note info no-icon%}
1.初始化阶段:
beforeCreate：实例刚创建完成,此时还没有data和methods属性
created：vue实例data和method属性已经初始化完成,此时还没有编译模板

2.实例挂载阶段
beforeMount：挂载前 模板编译完成,此时e l 还 没 有 挂 载 , el还没有挂载，data目前可见
mounted：挂载完成后 模板编译完成,$el挂载完成

3.数据更新阶段
beforeUpdate： 数据更新时执行,data数据此时已经是最新的数据,UI界面还是旧的
updated：数据更新完成后,界面和data里的数据此时都是最新的,完成的界面的更新渲染render

4.销毁阶段
销毁前: beforeDestroy： 实例准备销毁,此时data和methods方法都能用
销毁后:destroyed： 实例销毁完成,此时原先创建的实例方法和属性都不可以属性
{% endnote %}
