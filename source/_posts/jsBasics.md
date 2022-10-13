---
title: JS知识点
date: 2022-09-07 16:34:29
tags: 
- JS知识点
categories:
- JS
top_img: /img/cover8.jpg
cover: /img/cover8.jpg
---
## 一：初始JavaScript
### 1.什么是JavaScript？
{% note %}
JavaScript是世界上最流行的语言之一，是一种运行在客户端的脚本语言。
脚本语言：不需要编译，运行过程中由js解释器逐行解释并执行。
{% endnote %}
### 2.HTML/CSS/JS的关系
{% note %}
HTML和CSS属于 标记语言-描述类语言
HTML决定页面的结构和内容，CSS给页面添加样式。
JS脚本语言-编程类语言
JS实现业务逻辑和页面控制(决定功能)。
{% endnote %}
### 3.浏览器执行JS
{% note %}
浏览器分为：渲染引擎和JS引擎
渲染引擎：解析HTML和CSS，俗称 内核
JS引擎：也称为JS解释器，用来读取网页JavaScript代码
浏览器本身不会执行JS代码，是通过内置的JavaScript引擎来执行JS代码，JS引擎执行代码是 逐行解释的（转换成机器语言），然后由计算机去执行，所以JavaScript语言归为脚本语言。
{% endnote %}
### 4.JavaScript的组成
{% note %}
JavaScript由 ECMAScript(JavaScript语法)+DOM(页面文档对象模型)+BOM(浏览器对象模型)
ECMAScript：规定了js的编程语法和基础核心知识
DOM：是W3C推荐的处理可扩展标记语言的 标准编程接口。通过DOM提供的接口可以实现对页面元素的操作（大小、位置、颜色等）
BOM：提供了独立于内容的 、 可以与浏览器窗口进行互动的对象结构。通过BOM可以操作浏览器窗口，如弹出框、浏览器跳转、获取分辨率等
{% endnote %}
### 5.JS的书写位置
{% note %}
js分为3种书写位置：行内、内嵌、外部。
{% endnote %}

## 二：变量
### 1.什么是变量？
{% note %}
变量是用于存放数据的容器，我们通过变量名 获取元素，数据可以修改
本质：变量是程序在内存中申请的一块用来存放数据的空间
{% endnote %}
### 2.声明多个变量
{% note %}
var a =10,b=20,c=30;
注意： var a=b=c=10; 的执行顺序是
var a=10；——>b=10;——>c=10; b、c是全局变量
{% endnote %}
### 3.声明变量的特殊情况
{% note %}
  只声明,不赋值： var age; console.log(age); 结果：undefined
  不声明,不赋值，直接使用： console.log(age); 结果：报错
  不声明,只赋值： age=10; console.log(age); 结果：10
{% endnote %}
## 三：数据类型
### 1.变量数据类型
{% note %}
JavaScript的是一种弱类型的动态语言，这意味着不用提前声明变量的类型，在程序运行过程中，类型会被自动确定。在代码运行时变量数据类型由JS引擎根据 =右边变量的值的数据类型来判断，运行完毕后变量就确定了数据类型。
JS把数据类型分为两类：
{% endnote %}
#### 简单数据类型：
{% note %}
  Number(数字型)，String(字符串型)，Boolean(布尔值类型)，Undefine，Null
{% endnote %}
#### 复杂数据类型：
{% note %}
  object
{% endnote %}
#### Number数字类型
{% note %}
数型Number的个特殊值:
{% endnote %}
```
Infinity:代表无穷大，大于任何数值
-Infinity:代表无穷小，小于任何数值
NaN,Not a number,代表一个非数值
isNaN(x):x是数字——>true ； x不是数字——>false;
```
#### String 字符串类型
{% note %}
字符串的length属性可以获取字符串长度：str.length;
多字符串之间的拼接用 + ， 字符串 + 任何类型 = 拼接后的新字符串
{% endnote %}
```
    <script>
        var a1 = 1;
        var a2 = 2;
        console.log(typeof(a1)); //number
        console.log('a1+a2=' + a1 + a2); //a1+a2=12    'a1+a2=' 是字符串 有字符就是相连  
    </script>
+号口诀：数值相加 字符相连
```
#### Boolean布尔类型
```
true(1)，false(0)
```
#### Undefined和Null
```
变量声明但是未赋值：Undefined;给变量赋值null，里面存的值就是空
注意：任何类型 +(拼接) Number / Boolean = NaN
```
### 2.获取变量数据类型
{% note %}
typeof 变量名
注意：typeof null 的结果是object
{% endnote %}
### 3.数据类型转换
{% note %}
使用表单、prompt获取过来的数据默认是 字符串类型的 不能直接进行加法运算 需要转换变量数据类型
一般有三种转换方式
  转换成字符串类型
  转换成数字型
  转换成布尔型
{% endnote %} 
#### 转换成字符串类型：
```
num.toString()、String(num)强制转换、加号拼接字符串（常用！隐式转换）
（和字符串拼接的结果都是字符串）
```
#### 转换成数字型:
```
parseInt(string)、parseFloat(string)、Number()强制转换、js隐式转换（- * /）
隐式转换是我们再进行算术运算的时候,js自动转换成了数据类型
```
#### 转换成布尔类型：
```
Boolean(‘true’)代表空、否定的值会被转换false,如 ’‘，0，NaN，null，undefined
其余值都会被转换成true
```

## 三：运算符（操作符）
### 1.算术运算符
{% note %}
+加 _ -减 _ *乘 _ /除 _ %余
算数优先级：先乘除 后加减 有小括号先算小括号的
{% endnote %}
### 2.递增递减运算符
{% note %}
前置递增运算符 ++num 先自加，后返回值
后置递增运算符 num++ 先返回值，后自加
递减同上
{% endnote %}
### 3.比较运算符
{% note %}
比较运算符是两个数据进行比较时所使用的运算符，比较运算后，会返回一个布尔值（true/false）作为比较运算的结果。
{% endnote %}
| 运算符名称 | 说明 | 案例 | 结果|
|:-----|:-----|:-----|:-----|
|<         |小于号                      | 1<2       | true|
|>         |大于号                      | 1<2       | false|
|>=        |大于等于号                  | 2 >= 2    | true|
|<=        |小于等于号                  | 3 <= 2    | false|
|==        |判等号                      | 37 == 37  | true|
|!=        |不等号                      | 37 != 37  | false|
|===  !==  |全等（数值和数据类型都一致）  | 33='33'  |   false| 

js中 == 的隐式转换规则
```
      对象——>字符串——>数值<——布尔
```
比如：
#### 1.对象和布尔值进行比较
```
[] == false; //true
[]对象——>字符串——>数值0
false——>数值0
```
#### 2.对象和数字进行比较
```
[111] == 111; //true
[111]对象——>字符串——>数值111
```
#### 3.对象和字符串进行比较
```
[1,2,3]== ‘1,2,3’; //true
[1,2,3,]对象——>字符串’1,2,3,’
```
### 4.逻辑运算符
{% note %}
逻辑运算符是用来进行布尔值运算的运算符，返回值也是布尔值，开发中经常用于多个条件的判断
{% endnote %}
| 逻辑运算符 | 说明 | 案例 |
|:-----|:-----|:-----|
| &&     |  '逻辑与'，简称'与'  and |  true && false |
| {%raw%}||{%endraw%} |  '逻辑或'，简称'或'  or  |  true {%raw%}||{%endraw%} false |
| ！     |  '逻辑非'，简称'非'  not |  !true |
#### 逻辑与&&：
```
两边都是true才返回true，否则返回false
栗子1：var a = 2 > 1 && 3 >1//true
解析：
2 > 1 // true
3 > 1 //true
true && true //true
栗子2： var a = 2 > 1 && 3 < 1
解析：
2 > 1 // true
3 < 1 //false
true &&false // false
```
#### 逻辑或||：
```
两边都为false才返回false,否则都为true
栗子1：var a = 2 <1 || 3 <1//true
解析：
2 < 1 // false
3 < 1 //false
false || false // true
栗子1：var a = 2 >1 || 3 <1//true
解析：
2 > 1 // true
3 < 1 //false
true|| false // false
```
#### 逻辑非！： 
```
也叫做取反符号，用来取一个布尔值相反的值，true的相反值就是false
var isOk = !true;
console.log(isOk);// false;
```
### 5.短路运算符
{% note %}
短路运算的原理:当有多个表达式（值）时，左边的表达式可以确定结果时，就不再继续运算右边的表达式的值。
{% endnote %}
#### a.逻辑与
{% note %}
语法： 表达式1 && 表达式2
如果第一个表达式的值为真，则返回表达式2
如果第一个表达式的值为假，则返回表达式1
console.log( 123 && 456);//456
console.log( 0 && 456);//0
{% endnote %}
#### b.逻辑或
{% note %}
语法： 表达式1 || 表达式2
如果第一个表达式的值为真，则返回表达式1
如果第一个表达式的值为假，则返回表达式2
-console.log( 123 && 456);//123
console.log( 0 && 456);//456
{% endnote %}
#### 总结：
{% note %}
逻辑与短路运算是从左往右找第一个假，没有找到，就是最后一个为真
逻辑或短路运算是从左往右找第一个真，没有找到，就是最后一个为假
找到之后都是中断
{% endnote %}
## 四：流程控制分支
### 1.流程控制分支三种结构：
{% note %}
顺序结构、分支结构、循环结构
顺序结构：按代码先后顺序依次执行
分支结构：根据不同条件执行不同路径的代码
JS提供了两种分支语句
if语句
switch语句
{% endnote %}
### 2.三元表达式
{% note %}
表达式1 ？ 表达式2 : 表达式3；
表达式1为true 则返回 表达式2的值 否则 返回 表达式3的值
比如我们在写倒计时的案例时 想显示01这种0开头的 我们需要补0
num<10 ? ‘0’ + num : num;
{% endnote %}
### 3.闰年算法
{% note %}
能够被4整除，不能被100整除的为闰年 或者 能够被400整除的就是闰年
(year % 4 === 0 && year % 100 !==0 || year % 400 ===0 )
{% endnote %}
### 4.switch
{% note %}
switch case
break是退出循环，如果执行case语句，里面没有break,则会继续执行下一个case语句
continue是退出本次循环
{% endnote %}
## 五：数组
### 1.数组概念
{% note %}
数组是一组数据的集合，里面的每个元素被称为元素，数组中可以放任意类型的数据。数组是一种将一组数据存储在单个变量名下的优雅方式
{% endnote %}
### 2.数组的创建方式
{% note %}
 利用new创建数组
 利用数组字面量创建数组
 {% endnote %}
```
    <script>
        //1.new创建一个空的数组
        var arr = new Array();
        //2.利用数组字面量创建数组  创建了一个空的数组
        var arr = [];
        var arr1 = [1, 2, 3, 'pink', '456'];
        //数组中的数据用 , 分割    数组中的数据称为数组元素 数据类型无限制
        //数组的声明并赋值 称为数组的初始化
    </script>  
```
{% note %}
数组的字面量是方括号[]
{% endnote %}
### 3.获取数组元素
{% note %}
a.利用索引 arr[0]
b.遍历数组——>for循环
使用 数组名.length 可以访问数组元素的数量（长度）
{% endnote %}
### 4.数组转换成字符串
{% note %}
思路：定义一个 var str = ‘’ ; 再循环遍历数组元素并拼接到str后面
{% endnote %}
### 5.数组新增元素
{% note %}
 通过修改length长度新增数组元素（length属性是可读写的）修改之后增加的部分由于没有赋值默认值为undefined
{% endnote %}
```
<script>
    // 1.修改length 默认值是undefined
    var arr = [1, 2, 3, 4];
    console.log(arr.length);
    arr.length = 6;
    for (var i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
</script>
```
{% note %}
通过修改数组索引新增数组元素：通过修改数组索引的方式追加数组元素，但是注意不能直接给数组名赋值，会覆盖掉原来的数据。
{% endnote %}
```
 // 2.修改索引号
    var arr1 = [1, 2, 3, 4];
    arr1[1] = 5;
    console.log(arr1.length);
    console.log(arr1);
    arr1 = '别给我直接赋值'; //不要给数组直接赋值，否则里面的全部元素都没有了
    console.log(arr1);
    console.log(arr1.length); 
```
### 6.筛选数组
```
//筛选数组 把大于10的数据放入新的数组
    var arr = [11, 5, 6, 45, 7, 8, 6, 34, 45, 78, 12, 66];
    var arr1 = [];
    var j = 0;
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] >= 10) {
            arr1[j] = arr[i];
            //arr1[arr1.length]=arr[i]  arr1.length最开始是0 length可以自动检测长度的变化
            j++;
        }
    }
    console.log(arr1); 
```
### 7.数组案例
{% note %}
删除指定元素
{% endnote %}
```
 //删除指定数组元素 去掉元素中的0
         `在这里插入代码片`var arr = [0, 1, 0, 2, 0, 5, 4, 5, 7, 0];
         var newArray = []
         var i = 0;
         for (i = 0; i < arr.length; i++) {
             if (arr[i] == 0) {
                 continue;
             }
             newArray[newArray.length] = arr[i];
         }
         console.log(newArray); 
```
{% note %}
冒泡排序
{% endnote %}
```
 //冒泡排序
        var arr = [1, 5, 3, 8, 7, 2, 8, 2, 88, 42, 36, 25, 21, 17, 78];
        var newArr = [];
        var temp;
        for (var i = 0; i < arr.length - 1; i++) {//控制趟数
            for (var j = 0; j < arr.length - 1 - i; j++) {//每趟交换变量次数
                if (arr[j] > arr[j + 1]) {
                    temp = arr[j + 1];
                    arr[j + 1] = arr[j];
                    arr[j] = temp;
                }
            }
        }
        console.log(arr);
```
{% note %}
数组排序
{% endnote %}
```
        var arr1 = [1, 58, 23, 668, 17, 88];
        //升序
          arr1.sort(function(a, b) {
              return a - b;
          }); 

        //降序
        arr1.sort(function(a, b) {
            return b - a;
        });
        console.log(arr1);
```
{% note %}
数组去重
{% endnote %}
```
 <script>
        //核心思想： 遍历旧数组，拿着旧数组元素查询新数组 如果元素在新数组存在就不放入 如果不存在就放入
        //封装一个去重的函数
        function unique(arr) {
            var newArr = [];
            for (var i = 0; i < arr.length; i++) {
                if (newArr.indexOf(arr[i]) === -1) {
                    newArr.push(arr[i]); //用 追加push(数组元素) 来写
                }
            }
            return newArr;
        }
        var arr = ['a', 's', 'd', 's', 'd', 'v', 't', 's', 'a', 'v', 'g'];
        console.log(unique(arr));
    </script>
```
{% note %}
数组转换成字符串
{% endnote %}
```
 var arr = [1, 2, 3, 4];
        // 1.toString()
         console.log(arr.toString());//1,2,3,4

        //2. join(分隔符)
        var arr1 = ['red', 'blue', 'green'];
        console.log(arr1.join()); //red,blue,green
        console.log(arr1.join('-')); //red-blue-green
        console.log(arr1.join('&')); //red&blue&green   提交表单会用
```
## 六：函数
### 1.函数概念
{% note %}
函数就是封装了一段 可被重复调用执行的代码块。
{% endnote %}
### 2.函数使用
{% note %}
步骤：声明函数 和 调用函数
声明函数
{% endnote %}
```
function 函数名（参数1，参数2）{
函数体；
}
```
{% note %}
调用函数
函数名（参数1，参数2）；
注意:声明函数本身并不会执行代码，只有调用函数才会执行代码
{% endnote %}
### 3.函数形参、实参个数不同的问题
| 参数个数 | 说明 |
|:-----|:-----|
|实参 = 形参 |	输出正确结果 |
|实参 > 形参 |	只取到形参的个数 |
|实参 < 形参 |	多的形参定义为undifned,结果为NaN |
{% note %}
在JavaScript的函数中不可以通过参数个数不同来区别不同的函数，只能是通过函数名来区别
{% endnote %}
### 4.函数返回值
{% note %}
如果函数没有return ,返回值就是undefined（使用return 函数会停止执行并返回指定值）
{% endnote %}
### 5.break,continue,return 区别
{% note %}
  break:结束当前的循环体
  continue：跳出本次循环，继续执行下次循环
  return:不仅可以退出循环，还能够返回return语句中的值，同时结束当前函数体代码
{% endnote %}
### 6.arguments
{% note %}
arguments是函数的内置对象，存储了传递的所有实参
arguments 是一个伪数组，可以进行遍历，为数组特点：
  具有length属性
  可以遍历但是不具有数组的pop,push等方法
{% endnote %}
### 7.函数的两种声明方式
{% note %}
自定义函数方式（命名函数）、函数表达式方式（匿名函数）
{% endnote %}
  #### 命名函数：
  ```
  funciton fn(){
  //
  }
  ```
  {% note %}
  fn();//调用
  调用函数的代码可以放到声明函数前面，也可以放后面
  {% endnote %}
  #### 匿名函数：
  ```
  varf fn = function(){//此处的fn是变量名 不是函数名 fn里面存储的是一个函数
  //
  }
  fn();
  ```
  {% note %}
  函数调用必须写到函数体后面
  {% endnote %}
## 七：作用域
### 1.作用域概念
{% note %}
限定这个名字的可用性的代码范围就是这个名字的作用域
ES6之前，作用域有两种：全局作用域和局部作用域（函数作用域） ES6之后新增块级作用域
{% endnote %}
### 2.变量的作用域
{% note %}
根据作用域的不同，变量可分为两种：全局变量、局部变量
全局变量：在代码任何位置都可以使用；全局作用域下用var声明的变量
局部变量：函数内部声明的变量，形参也是局部变量
{% endnote %}
### 3.全局变量和局部变量的区别
{% note %}
全局变量在任何一个地方都可以使用，只有在浏览器关闭的时候才会被销毁，因此比较占内存
局部变量只能在函数内部使用，当其所在的代码块被执行时，会被初始化；当代码块运行结束后，就会被销毁，比较节约内存
{% endnote %}
### 4.作用域链
{% note %}
只要是代码就至少有一个作用域，写在函数内部的是局部作用域，函数中还有函数，那么这个作用域中又可以诞生一个作用域
柑橘在内部函数可以访问外部函数变量的这种机制，用链式查找决定哪些数据能够被内部函数访问，就成为 作用域链
作用域链采取就近原则查找变量最终值
{% endnote %}
## 八：预解析
### 1.JavaScript解析器在运行代码的时候的步骤：预解析和代码执行
{% note %}
预解析:（也叫做变量、函数提升）在当前作用域下，JS执行代码之前，浏览器默认把带有var和function声明的变量在内存中进行提前的声明或者定义。 注意：并不赋值
代码执行：从上到下
{% endnote %}
### 2.变量预解析
{% note %}
变量提升：变量的声明提升到作用域最上面，但是变量的赋值不会提升
函数提升：函数的声明会被提升到作用域最上面，但是不会调用函数
{% endnote %}
## 九：对象
### 1.什么是对象？
{% note %}
对象是一个具体的事物，对象由属性和方法组成。
属性：事物的特征，在对象中用属性来表示 （名词）
方法：食物的行为，在对象中用方法来表示 （动词）
{% endnote %}
### 2.创建对象的三种方式
{% note %}
  利用字面量创建对象
  利用new Object创建对象
  利用构造函数创建对象(函数名的首字母要大写并且要和new一起使用才有意义 里面的属性和方法要加this哟表示当前对象的属性和方法)
{% endnote %}
```
  		// 字面量创建对象
        var dog = {
             name: '可可',
             type: '阿拉斯加犬',
             age: 5,
             color: '棕红色',
             bark: function() {
                 alert('汪汪汪');
             },
             showFilm: function() {
                 alert('演电影');
             }
         }
         console.log(dog.name);
         dog.bark() 

        //利用new Object创建对象
        var people = new Object;
        people.name = '鸣人';
        people.sex = '男';
        people.age = '19';
        people.skill = function() {
            alert('影分身术');
        }
        console.log(people.name); 

        // 构造函数创建对象
        	function 构造函数名（）{
            this.属性=值;
            this.方法=function(){

            }
        }
        new 构造函数名() 
```
### 3.对象的调用
{% note %}
对象属性的调用:
  对象.属性名
  对象[ ’ 属性名 ’ ],方括号里面的属性必须加引号 如 star[‘name’]
对象里面的方法调用：对象.方法名()
{% endnote %}
### 4.遍历对象属性
```
for … in
for ( 变量 in 对象名字 ){
//执行代码
}
for ( var k in obj){
console.log( k ); // k 是属性名
console.log( obj[k] ); // obj[k] 是属性值
}
```

## 十：内置对象
{% note %}
JavaScript中的对象分为三种：自定义对象、内置对象、浏览器对象
内置对象是指JS语言自带的一些对象，比如Math、Data、Array、String
{% endnote %}
### 1.Math对象
{% note %}
Math对象不是构造函数
Math.floor() 向下取整（往小了取）
Math.ceil() 向上取整（往大了取）
Math.round() 四舍五入（就近取值） 注意！-3.5 是 -3 ， .5的时候是取大的
Math.abs() 绝对值
Math.max() / Math.min() 最大值 / 最小值
Math.random() 随即返回小数。[0，1） 左闭右开
求两个数之间的随机整数包括这两个数：
Math.floor(Math.random() * (max - min + 1)) + min;
{% endnote %}
### 2.Date对象
{% note %}
Date日期对象是一个构造函数 所以需要实例化后才能使用
new Date();
  如果 Date() 不写参数，就返回当前时间
  如果 Date() 写参数，就返回括号里的时间
日期格式化
{% endnote %}
| 方法名 | 说明 | 代码 |
|:-----|:-----|:-----|
| getFullYear() | 获取当年               |         dObj.getFullYear() |
| getMonth()    | 获取当月（0-11  用的时候+1） |    dObj.getMonth()   | 
| getDate()     | 获取当天日期             |       dObj.getDate()     |
| getDay()      | 获取星期几（周日0 周六6）     |   dObj.getDay()     | 
| getHours()    | 获取当前小时             |       dObj.getHours()    |
| getMinutes()  | 获取当前分钟             |       dObj.getMinutes()  |  
| getSeconds()  | 获取当前秒钟             |       dObj.getSeconds()  | 
{% note %}
获取日期总毫秒
Date对象是基于1970年1月1日（世界标准时间）起的毫秒数
我们进场利用毫秒数来计算时间，因为更加精确
{% endnote %}
```
//获取Date总的毫秒数（时间戳） 不是当前时间的 而是现在时间距离1970年1月1日 过了多少毫秒
        //1.通过 valueOf() getTime()
        var date = new Date();
        console.log(date.valueOf());
        console.log(date.getTime());
        //2.简单写法  开发中常用的
        var date1 = +new Date(); // +new Date() 返回就是距离现在过了多少毫秒   现实开发中常用的
        console.log(date1);
        //3. H5 新增的  低版本浏览器不兼容
        console.log(Date.now());
```
{% note %}
倒计时案例：https://blog.csdn.net/qq_42156918/article/details/108745113
{% endnote %}
### 3.数组对象
#### 数组对象创建的两种方式：
{% note %}
    字面量方式
    new Array()
{% endnote %}
```
    //1.new创建一个空的数组
    var arr = new Array();

    //2.利用数组字面量创建数组  创建了一个空的数组
    var arr = [];
    var arr1 = [1, 2, 3, 'pink', '456'];
```
#### 检测是否为数组？
{% note %}
instanceof运算符，可以判断一个对象是否属于某种类型
Array.isArray(arr)用于判断一个对象是否为数组，（HTML5中提供的方法）
{% endnote %}
#### 添加删除数组元素的方法
| 方法名 | 说明 | 返回值 |
|:-----|:-----|:-----|
| push(参数1...)       | 末尾添加一个或多个元素，注意修改原数组                 |   并返回新的长度
| pop()                | 删除数组最后一个元素，把数组长度减1无参数，修改原数组  |    返回删除的元素的值
| unshift(参数1...)    | 向数组的开头添加一个或多个元素，注意修改原数组         |    并返回新的长度
| shift()              | 删除数组的第一个元素，数组长度减1无参数，修改原数组    |    并返回第一个元素的值
#### 数组排序
| 方法名 | 说明 | 是否修改原数组 |
|:-----|:-----|:-----|
| reverse() |    颠倒数组中元素的顺序，无参数  |    该方法会改变原来的数组，返回新数组 |
| sort()    |    对数组的元素进行排序      |       该方法会改变原来的数组，返回新数组 |
```
  var arr = [1, 64, 9, 6];
  arr.sort(function(a,b){
     return b - a;  // 降a序
     // return a - b; //升序
  })
  console.log(arr);
```
#### 数组索引方法
{% note %}
indexOf() 数组中查找指定元素的一个索引 存在返回索引号，不存在返回-1
lastIndexOf() 在数组中的最后一个索引， 存在返回索引号， 不存在返回-1
{% endnote %}
#### 数组转换成字符串
{% note %}
toString()
join(‘分隔符’)
{% endnote %}
### 4.字符串对象
{% note %}
为了方便操作基本数据类型，JavaScript提供了三个特殊的引用类型：String、Number、Boolean
基本包装类型就是把简单数据类型包装成复杂数据类型，这样基本数据类型就有了属性和方法
{% endnote %}
```
// 1. 把简单数据类型包装成复杂数据类型   给临时变量
    var temp = new String('hello');
    // 2.把临时变量给 str
    str = temp;
    // 3.销毁临时变量
    temp = null;
```
{% note %}
字符串是不可变的，指的是里面的值是不变的，当我们重新给字符串赋值时，其实地址已经变了，在内存中开辟了新的空间。
{% endnote %}
#### 根据字符串返回位置
```
indexOf（‘要查找的字符’，[开始的位置]）返回指定字符在字符串中出现的位置，没有就返回-1，开始位置是索引号
lastIndexOf() 从后往前找，只找第一个匹配的
```
#### 根据位置返回字符
```
charAt(index) 返回指定位置的字符，index是字符串的索引号 str.charAt(0)
charCodeAt(index) 获取指定位置处字符的ASCII码（index是索引号） str.charCodeAt(0)
str[index] 获取指定位置处的字符
```
#### 求字符串中出现字符次数最多的字符和次数
```
//思路 ：把每一次遍历的字符都放到一个对象的属性中，并且看有无该属性 有则创建 无则属性值+1 属性名就是字符名
        var str = 'andsbckcsivbisezcadedsc';
        var obj = {}; // 创建一个空对象
        //属性赋值
        for (var i = 0; i < str.length; i++) {
            if (obj[str[i]]) {
                //如果已经有这个属性了  值 +1
                obj[str[i]]++;

            } else {
                //没有这个属性 赋值 1
                obj[str[i]] = 1;
            }
        }
        //遍历对象 for in
        var max = 0;
        var ch = '';
        for (var k in obj) {
            // k 得到的是属性名
            // obj[k] 得到的是属性值
            if (max < obj[k]) {
                max = obj[k];
            }

        }
        for (var k in obj) {
            if (obj[k] === max) {
                ch += k;
            }
        }
```
#### 字符串操作方法
```
contact(str1,str2…) 连接字符串
substr(start,length）截取字符串，start开始位置（索引号）length取得个数，如果省略代表取start开始后面所有的字符
replace(‘被替换的字符串’,‘要替换的字符串’)
split()切分字符串，可以将字符串切分成数组，切分完毕后返回的是一个新数组
var str = ‘a,b,c,d’;
console.log(str.split(’,’));//[a,b,c,d];
```
## 十一：简单类型和复杂类型
#### 简单类型又叫做基本数据类型或者值类型，复杂数据类型又叫做引用类型
{% note %}
  值类型：简单数据类型/基本数据类型，在存储变量中是存储的是值本身
  如：string,number,boolean,undefined,null
  引用类型：复杂数据类型，在存储时变量中存储的仅仅是地址（引用），因此叫做引用数据类型，通过new关键字创建的对象，如Object，Array,Date等
{% endnote %}