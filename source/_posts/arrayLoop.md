---
title: 数组循环
date: 2022-09-06 15:19:45
tags:
- 数组循环
categories:
- 数组
top_img: /img/cover6.png
cover: /img/cover6.png
---
### 1.forEach()
```
let array = [1,2,3,4];
array.forEach((item, index, array) => {
　　console.log(item);
});
```
{% note %}
forEach会遍历数组, 没有返回值, 不允许在循环体内写return, 不会改变原来数组的内容.forEach()也可以循环对象。
{% endnote %}
### 2.map()
```
let array = [1, 2, 3, 4];
let temp = array.map((item, index, array) => {
　　return item * 10;
});
console.log(temp);　　//  [10, 20, 30, 40];
console.log(array);　　// [1, 2, 3, 4]
```
{% note %}
map 遍历数组, 会返回一个新数组, 不会改变原来数组里的内容
{% endnote %}
```
let temp2 = array.map(String);　　// 把数组里的元素都转成字符串
console.log(temp2);
```
### 3.filter()
```
let array = [1, 2, 3, 4];
let temp = array.filter((item, index, array) => {
　　return item >  3;
});
console.log(temp);　　// [4]
console.log(array);　　// [1, 2, 3, 4]
```
{% note %}
filter 会过滤掉数组中不满足条件的元素, 把满足条件的元素放到一个新数组中, 不改变原数组
{% endnote %}
### 4.reduce()
```
let array = [1, 2, 3, 4];
let temp = array.reduce((x, y) => {
	console.log("x,"+x);
	console.log("y,"+y);
	console.log("x+y,",Number(x)+Number(y));
	return x + y;
});
console.log(temp);　　// 10
console.log(array);　　// [1, 2, 3, 4]
```
{% note %}
x 是上一次计算过的值, 第一次循环的时候是数组中的第1个元素
y 是数组中的每个元素, 第一次循环的时候是数组的第2个元素
{% endnote %}
### 5.every()
```
let array = [1, 2, 3, 4];
let bo = array.every((item, index, array) => {
　　return item > 2;
});
console.log(bo);　　　　// false;
```
{% note %}
every遍历数组, 每一项都是true, 则返回true, 只要有一个是false, 就返回false
{% endnote %}
### 6.some()
```
let array = [1, 2, 3, 4];
let temp = array.some((item, index, array) => {
　　return item > 5;
});
console.log(temp);　　// false
```
{% note %}
遍历数组的每一项, 有一个返回true, 就停止循环

以上6个方法IE9及以上才支持。不过可以通过babel转义支持IE低版本。
以上均不改变原数组。
some、every返回true、false。
map、filter返回一个新数组。
reduce让数组的前后两项进行某种计算，返回最终操作的结果。
forEach 无返回值。
{% endnote %}