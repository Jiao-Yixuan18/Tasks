# JS学习笔记

> ——焦怡煖

## 学习背景

已学习HTML CSS基础

## 学习内容的目录

- JS介绍[JavaScript 介绍](#JavaScript 介绍)
- 为什么要学JS[为什么要学JS](#为什么要学JS)
- JS和ES的关系[JavaScript与ECAMScript的关系](#JavaScript与ECAMScript的关系)
- 语句[语句](#语句)
- 标识符[标识符](#标识符)
- 变量[变量](#变量)
- 变量提升[变量提升](#变量提升)
- 常量[常量](#常量)
- JS引入到HTML文件中[JS引入到HTML文件中](#JS引入到HTML文件中)
- 数据类型（6种）[数据类型（6种）](#数据类型（6种）)
- typeof运算符[typeof运算符](#typeof运算符)
- 算术运算符[算术运算符](#算术运算符)
- 赋值运算符[赋值运算符](#赋值运算符)
- 比较运算符[比较运算符](#比较运算符)
- 布尔运算符[布尔运算符](#布尔运算符)
- 类型转换[类型转换](#类型转换)
- 条件语句[条件语句](#条件语句)
- 三元运算符[三元运算符](#三元运算符)
- 循环语句for[循环语句for](#循环语句for)
- 循环语句while[循环语句while](#循环语句while)
- break[break](#break)
- continue[continue](#continue)
- 字符串[字符串](#字符串)
- 字符串的方法[字符串的方法](#字符串的方法)
- 
## 学习内容

#### JavaScript 介绍
JS是一种轻量级的脚本语言。所谓“脚本语言”，指的是它不具备开发操作系统的能力，而是只用来编写控制其他大型应用程序的“脚本”。
JS是一种嵌入式语言，它本身提供的核心语法并不多，只能用来做一些数学和逻辑运算。

#### 为什么要学JS
1. 操作浏览器的能力
2. 广泛的适用领域
3. 易学性
#### JavaScript与ECAMScript的关系
ES和JS的关系是，前者是后者的规格，后者是前者的一种实现。在日常场合中，这两个词可以互换。
#### 语句
JS程序的单位是行，也就是一行一行地执行，一般情况下，每一行就是一个语句。
在开发者工具（vs code即可）创建一个js文件（index.js），写入一个语句
var num = 10；
> 注释：在HTML中：<!-- --!>
> 在CSS中：/* */
> 在JavaScript://单行注释
 /* */多行注释

语句以分号结尾，一个分号就表示一个语句结束
注意：在JS中，分号是可选的，不加，语法上也不错，但是总是建议添加分号，以免出现错误

#### 标识符
标识符指的是用来识别各种值的合法名称。最常见的标识符就是变量名
标识符是由：字母、美元符号(&)、下划线（_）和数字组成，其中数字不能开头
中文是合法的标识符可以用作变量名（不推荐）
以上例子中 num 就是一个标识符
JS保留关键字，这些关键字不能用作标识符

#### 变量
用var声明
var num= 10;
 变量可以看作一个停车位，num相当于车位编号，10相当于车（可更换）
 num = 20;变量的重新赋值


#### 变量的提升
JS引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行。这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升。

* 打印，会在浏览器的控制台中显示出来
 console.log(100);
  打印出100
  例：
  1。
  var num = 10;
  console.log(num);
  打印出10
   2.
  console.log(hello);
  会报错，因为hello未定义
   3.
  console.log(num);
  var num = 10;
  打印出undefined
  实则被解释成：
  var num;(没有值undefined)
  console.log(num);
  num = 10;
  所以要先声明后打印（在JS中不会报错）

#### 常量
const定义常量，常量无法改变
例：
const URL = "http://www.itbaizhan.com"
URL = "http://iwenwiki.com"
会报错
常量一旦声明，是不可改变，所以不会改变的量用常量定义

#### JS引入到HTML文件中
1. 内部标签

可以在head和body标签里添加script标签（一般放在body最后，浏览器先渲染内容，效率高）

例：<script src="路径"><script/>

2. 外部引入

将js文件（页面上的行为）与html（页面内容）分离出来，将关注点分离，实现每个代码的职责单一

1）在VScode里新建一个js文件
2）将html里script标签里的内容剪切放进js文件
3）在html里script标签里添加属性src=“js文件名”，这会告诉浏览器Javascript代码在该文件中

3. 引入网络来源文件
一般引入的是jquery cdn
与1中一样，用src引入，但引入的不是一个路径的，而是一个网络地址

如何看这个JS文件是否有加载？
右击运行浏览器当中，点检查，点NNetwork,刷新一下等待加载，点All,看有无文件

什么是CDN？
网络加速资源

#### 数据类型（6种）

1. 原始类型（基础类型）：数值、字符串、布尔值

   ```javascript
   var  age =20; *数值*

   var name = "尚学堂"；*字符串*

   var learn = true;*布尔值*
	```
   注：

   （1）数值

   js不区分小数和整数

   123 整数

   123.1浮点数

   1.123e3 科学计数法

   -99负数

   NAN not a number

   Infinity 表示无限大

   （2）布尔值

   只有true（真）,false（假）两个值

2. 合成类型（复合类型）：对象，一个对象往往是多个原始类型复合而成

      例：

      ```javascript
      var obj={
             name:"itbaizhan",
             age:10;
             flag:false
      }
      ```
      对象分为狭义对象（键值对的对象）和广义对象（在JS中，一切皆对象）

3. null、undefined（特殊）
    一般把它们看成两个特殊值
    区别：
    都是基本的数据类型，这两个数据类型分别都只有一个值，就是undefined和null.
    undefined代表的含义是未定义，null代表的含义是空对象。一般变量声明了但还没有定义的时候会返回undefined,null主要用于赋值给一些可能会返回对象的变量，作为初始化。
    例：

    ```javascript
    var hello; *undefined*
    var timer = null;*定时器  初始化操作*
    ```

  undefined和null区别

  * （1）类型不同
    * undefined是一个类型（undefined类型），表示变量未定义.
    * null是一个对象（object类型），表示空对象指针。
     (2)使用场景不同
    * undefined通常用于变量声明但未赋值的情况。
    * null通常用于显式地表示“空”或“无值”的情况。
     (3)赋值方式不同
    * undefined是JS引擎自动赋予未初始化变量的值。
    * null是开发者可以显式赋予变量的值。
     (4)比较不同
    * `undefined==null`返回`true`，因为他们都表示“空值”。
    * `undefined===null`返回`false`，因为他们类型不同。

  #### typeof运算符

作用:确定数据类型

数值返回number、字符串返回string、布尔值返回boolean、对象返回object
例：

```javascript
   console.log(typeof 123);*number*
   console.log(typeof "123");*string*
   console.log(typeof true);*boolean*
   console.log(typeof {})*object*
```
当对null和undefined这两种数据类型使用typeof进行判断时，Null类型会返回“object”
例：

```javascript
console.log(typeof undefined);*undefined*
console.log(typeof null);*object*
```


在JS中，确定数据类型的几种方式：
`typeof操作符`
`instanceof操作符`
`Object.prototype.toString.call`方法
`Array.isArray`判断是否为数组

#### 算数运算符
1.加法运算符

> 数值相加

```javascript
var num1 =10；

var num2 = 29；

console.log(num1+num2);//39
```

> 非数值相加

*//true:1 false:0*

```javascript
var f1 = true;

var f2 =true;

var f3 = false;

var num3 = 10;

console.log(f1+f2);//2

console.log(f1+f3);//1

console.log(f1+num3);//11

console.log(f1+num3);//10
```

> 与字符串相加
>
> 如果是与字符串相加，这是加法运算符会变成连接运算符，返回一个新的字符串，将两个原字符串串连接在一起
>
> 如果一个运算子是字符串，另一个运算子是非字符串，这时非字符串会转成字符串，再连接在一起

```javaScript

var s1 = "hello"

var s2 = "world"

var num4 = 10;

var f4 = false;

console.log(s1+s2);//helloworld

console.log(s1+num4);//hello10

console.log(s1+f4);//hellofalse
```

字符串与任何类型相加都会转化成字符串

2.加减乘除运算符

基本的数学运算符效果，加法比较特殊

3.余数运算符

例：

```javascript
var num7 = 15;

var num8 = 4;

console.log(num7 % num8);//3 
```

4.自增自减运算符

* 放在变量之后，会先返回变量操作前的值，再进行自增自减操作；

* 放在变量之后，会先进行自增自减操作，再返回变量操作后的值

  > ++在前先加后运算
  > ++在后先运算后加
  
  例：
  
  ```javascript
  var x = 1;
  var y = 1;
  x++ //1
  ++x //2
  var x = 10;
  var y = 20;
  console.log(x++ + y);//30
  ```
  
  #### 赋值运算符
  
|    运算符  | 表达式  | 
| :--------:   | :-----:  | 
| =    | 赋值运算符|  
| +=      |   x+=y等同于x=x+y   |  
| -=       |    x-=y等同于x=x-y  |  
|   *=          |      x*=y等同于x=x*y    |
|     /=        |   x/=y等同于x=x/y         |
|	  %=        | x%=y等同于x=x%y            |

#### 比较运算符
> "=="是比较，不是赋值

比较运算符用于比较两个值的大小，然后`返回一个布尔值`，表示是否满足指定的条件。
2>1//true

|    比较运算符  | 描述  | 
| :--------:   | :-----:  | 
| <   | 小于运算符|  
| >      |  大于运算符  |  
| <=       |    小于或等于运算符  |  
|   >=          |   大于或等于运算符      |
|     ==        |      相等运算符      |
|	  ===        |       严格相等运算符     |
|     !=         |            不相等运算符        |
|       !==          |        严格不相等运算符       |

* “==”和“===”的区别

双等比较值，三等比较值和类型

100=="100"//true
100==="100"//false

#### 布尔运算符
> 返回布尔值
* 取反运算符：！
  布尔值取反、非布尔值取反
  对于非布尔值，取反运算符会将其转为布尔值
  以下六个值取反后为true，其他都为false：undefined、null、false、0、NAN、空字符串（""）
* 且运算符：&&
  多个条件都要满足
* 或运算符：||
  满足一个条件即可
  
#### 类型转换
* 自动转换
  1. 不同类型的数据互相运算
  
  2. 对非布尔值类型的数据求布尔值
      例：
  
    ```javascript
    var num = 100;
    var str = "hello"
    ```
  
  *//num先进行自动类型转换，转成字符串，再与str进行拼接*
  
  ```javascript
  console.log(num+str);//100hello
  ```
  
  *//hello自动类型转换成boolean类型，true*
  
  ```javascript
  var hello = "hello";
  console.log(!hello);//false
  ```
  
* 强制转换
  使用Number、String和Boolean三个函数，手动将各种类型的值，分布转换成数字、字符串或者布尔值
  1. Number:
  使用Number函数，可以将任意类型的值转化为数值
   * 数值：转换后还是原来的值
     Number(324)//324
   * 字符串：如果可以被解析为数值，则转换为相应的数值
     Number('324')//324
   * 字符串：如果不可以被解析为数值，返回NaN
     Number('324abc')//NaN
   * 空字符串转为0
     Number('')//0
   * 布尔值：true转为1，false转为0
     Number(true)*//1*
     Number(false)*//0*
     
     var num1 = 100;
     console.log(typeof Number(num1))；*//number*
     console.log(typeof Number("123ABC"));*//number*
  2. String:
  string函数可以将任意类型的值转化为字符串
  String(123)//"123"
  String('abc')//"abc"
  String(true)//"true"
  String(undefined)//"undefined"
  String(null)//"null"
  3. Boolean:
  Boolean可以将任意类型的值转化为布尔值
  除了以下5个值的转换结果为false，其他的值全部为true：
  undefined、null、-0或+0、NaN、""(空字符串)
  例：Boolean(undefined)//false
  
#### 条件语句
* if

if结构先判断一个表达式的布尔值，然后根据布尔值的真伪，执行不同的语句。所谓布尔值，指的是JS的两个特殊值，true表示真，false表示伪。

```javascript
if (布尔值){

语句；

}

if（布尔值）{

语句；

}else{

语句；

}
```

注：布尔值往往由一个表达式产生的，必须放在圆括号里中

对同一个变量进行多次判断时，多个if...else语句可以连写在一起

* switch

  ```javascript
  switch（）{
  
  case “banana”:
  
  //...
  
  break;
  
  case “apple”:
  
  //...
  
  break;
  
  default:
  
  //...
  
  }
  
  
  ```



#### 三元运算符

```javascript
（条件）？表达式1：表达式2
```

#### 循环语句for

```javascript
for（初始化语句；条件；迭代因子）{
    语句;
}
```

1. 初始化表达式：确定循环变量的初始值，只在循环开始时执行一次。
2. 布尔值表达式：每轮循环开始时，都要执行这个条件的表达式，只有直委真，才继续进行循环。
3. 迭代因子：每轮循环的最后一个操作，通常用来递增循环变量
4. 三个表达式可以省略任何一个，也可以全部省略，如果全部省略，就进入死循环



#### 循环语句while

```javascript
while (条件){

语句；

}
```

#### break

用于跳出代码块或循环

#### continue

用于立即终止本轮循环，返回循环结构的头部，开始下一轮循环

#### 字符串

0个或多个排在一起的字符，放在单引号或双引号之中

```javascript
"balabala"   'balabala'
```

单引号字符串的内部，可以使用双引号，双引号字符串内部，可以使用单引号

```javascript
'key="value"'     "It's a long balabala"
```

如果要在单引号字符串的内部，使用单引号，就必须在内部的单引号前面加上反斜杠，用来转义。

双引号字符串内部使用双引号，也是如此

```javascript
'Did she say \’Hello\‘？'     "Did she say \"Hello\"?"    
```

注：字符串默认只能写在一行内，分成多行将会报错

* 如果长字符串必须分成多行，可以在每一行的尾部使用反斜杠

  ```javascript
  var longString = 'Long \
  
  long \
  
  string’;
  ```

* 转义
|    转义字符  | 含义  | 
| :--------:   | :-----:  | 
| \0 | null|  
| \b  |   后退键   |  
|   \f     |   换页符  |  
|     \n        |   换行符    |
|  \r    |   回车键   |
|  \t    |     制表符     |
|   \v     |  垂直制表符   |  
|     '        |     单引号  |
|   "   |   双引号   |
|   \   |    反斜杠      |


* length属性
  返回字符的长度，该属性无法改变

  ```javascript
  var s = 'balabala';
  s.length //9
  ```

#### 字符串的方法
* concat:连接两个或多个字符串，返回连接后的字符串
  
  ```javascript
  var str1 = "hello"
  var str2 = "world"
  console.log(str1.concat(str2));
  console.log(str1+str2);
  ```
  
* slice：提取字符串的一部分，并返回一个新的字符串，注意从0开始计算
  用于从原字符串取出子字符串并返回，不改变原字符串

  它的第一个参数是子字符串的开始位置，第二个参数是子字符串的结束位置（不含该位置）
  
  ```javascript
  console.log(str3.slice(0,2));//"it"
  ```
  
  如果省略第二个参数，则表示子字符串一直到原字符串结束
  

   ```javascript
  console.log(str3.slice(2));//"baizhan"
   ```


* substring:提取字符串的一部分，并返回一个新的字符串
  用于从原字符串取出子字符串并返回，不改变原字符串，跟slice方法很像
  
  
  ```javascript
  var str4 = "itbaizhan";
  console.log(str4.substring(0,2));//"it"  0是开始的位置，2是结束的位置（返回结果不含该位置）
  console.log(str4.substring(2));
  ```

* indexOf：检索字符串，返回字符串中首次出现的位置
  用于确定一个字符串在另一个字符串中第一次出现的位置，返回结果是匹配开始的位置，如果返回-1，就表示不匹配
  
  ```javascript
  var str5 = "itbaizhan";
  console.log(str5.indexOf("a"));
  if(str5.indexOf("j")!= -1){
  console.log("存在")；
  }else{
  console.log("不存在")；
  }
  ```

* trim：去除字符串两端的空格
  
  ```javascript
  var str6 = " iwenwiki "
  console.log(str6.trim());//iwenwiki
  ```
  
* replace：替换字符串

  ```javascript
  var str7 = "sxtbaizhan"
  console.log(str7.replace("sxt","it"));//itbaizhan
  ```

* split：把字符串分割成字符串数组

  ```javascript
   var str8 = "sxt|it|baizhan"
   console.log(str8.split("|"));//["sxt","it","baizhan"]
  ```

#### 数组

数组是按次序排列的一组值，每个值都有编号（从0开始），整个数组用方括号表示

两端的方括号是数组的标志。sxt是0号位置，baizhan是1号位置，it是2号位置。

```j
var arr = ['sxt','baizhan','it'];
```

除了在定义时赋值，数组也可以先定义后赋值。

```'
var arr1 = [];

arr[0] = 'sxt';
arr[1] = 'baizhan';
arr[2] = 'it';

console.log(arr,arr1);
```

任何类型的数据，都可以放入数组

```javascript
var arr = [100,[1,2,3],false ];
```

length属性：返回数组的成员数量

```javascript
console.log(arr1.length);//3
```

读取数组中的某一个元素，通过下标

```javascript
console.log(arr1[0]);//sxt
```

#### 数组常用方法

* 数组的遍历

  ```javascript
  var a = ['sxt','baizhan','it'];
  
  //for循环
  for(var i = 0;i<a.length;i++){
      console.log(a[i]);
  }
  
  //while循环
  var i = 0;
  while(i<a.length){
      console.log(a[i]);
      i++;
  }
  ```

  

* 数组的静态方法Array.isArray()

  判断是否为数组

  ```javascript
  var arr = ['sxt',100,true];
  var hello = "hello"
  console.log(typeof arr;
  console.log(); 
  console.log();
  ```

  

* 数组方法 push()/pop()

  push用于在数组末端添加一个或多个元素，并返回添加新元素后的数组长度。注意，该方法会改变原数组。

  pop方法用于删除数组的最后一个元素，并返回该元素。注意，该方法会改变原数组。

  ```javascript
  var arr = [];
  arr.push("尚学堂")
  arr.push('itbaizhan')
  arr.push(true,{})
  console.log(arr);//[尚学堂，'itbaizhan',true,{}]
  
  var arr = ['尚学堂'，'itbaizhan','web前端']；
  
  arr.pop()//'web前端'
  console.log(arr);//['尚学堂'，'itbaizhan']
  ```

  

* 数组方法 join()

  join方法以指定参数作为分隔符，将所有数组成员连接为一个字符串返回。如果不提供参数，默认用逗号分隔。

  ```javascript
  var a = [1,2,3,4];
  
  a.join(' ')//'1 2 3 4'
  a.join('|')//"1|2|3|4"
  a.join()//"1,2,3,4"
  ```

  

* 数组方法concat()

  用于多个数组的合并。它将新数组的成员，添加到原数组成员的后部，然后返回一个新数组，原数组不变

  ```javascript
  ['hello'].concat(['world'])
  //["hello","world"]
  ['hello'].concat(['world'],['!'])
  //["hello","world","!"]
  ```

  

* 数组方法slice()

  用于提取目标数组的一部分，返回一个新数组，原数组不变
  
  它的第一个参数为起始位置（从0开始），第二个参数为终止位置（但该位置的元素本身不包括在内）。
  
  如果忽略第二个参数，则一直返回到原数组的最后一个成员。
  
  ```javascript
  var arr = ['尚学堂'，'itbaizhan','百战程序员']；
  
  arr.slice(0)//['尚学堂'，'itbaizhan','百战程序员']
  arr.slice(1)//['itbaizhan','百战程序员']
  arr.slice(1,2)//['itbaizhan']
  arr.slice(2,6)//['百战程序员']
  arr.slice()//['尚学堂'，'itbaizhan','百战程序员']
  ```
  



#### 函数

可复用的模具

函数式一段可以反复调用的代码块

函数声明：function命令声明的代码区块，就是一个函数。function命令后面是函数名，函数名后面是一对圆括号，里面是传入函数的参数。函数体放在大括号里

```javascript
//两个数相加
var num1 = 100;
var num2 = 100;

function add(a,b){
    console.log(a+b);
}

add(num1,num2)
add(120,200);
```

除了用function命令声明函数，还可以采用变量复制的写法

```javascript
var print = function(s){
    console.log(s);
};
```

* 函数参数

  函数运行的时候，有时需要提供外部数据，不同的外部数据会得到不同的结果，这种外部数据就叫参数

  ```javascript
  function square(x){
      console.log(x*x);
  }
  
  square(2)//4
  square(3)//9
  ```

  

* 函数返回值

  JS函数提供两个接口实现与外界的交互，其中参数作为入口，接收外界信息；返回值作为出口，把运算结果反馈给外界。

  ```javascript
  function getName(Name){
      return name;
  }
  
  var myName = 
      getName("itbaizhan")
  	console.log(myName);//itbaizhan
  ```

  在函数中return后的语句都不会执行

* 数组去重应用场景

  在处理大量数据时，为了提高效率和减少冗杂，需要对数据进行去重操作。

  ```javascript
  //数据去重
  function unipue(arr){
      if(!Array.isArray(arr)){
          console.log("数据类型错误")；
          return；
      }
      //存储最终数据的数组
      let res =[]
      for(var i = 0;i<arr.length;i++){
          if(res.indexOf(arr[i])==-1){
              res.push(arr[i])
          }
      }
      return res;
  }
  ```

  
#### DOM之document

DOM是JS操作网页的接口，全称为“文档对象模型”。它的作用是将网页转为一个JS对象，从而可以用脚本进行各种操作。

浏览器会根据DOM模型，将结构化文档HTML解析成一系列的节点，再由这些节点组成一个树状结构。所有的节点和最终的树状结构，都有规范的对外接口。

* 节点
* do

## 参考资料

[bilibili JS入门教程]([【前端教程】JavaScript 2小时快速入门，全程无废话，入门到精通，前端js全套基础&实战教程，附源码+文档_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1NHoKYGEKJ/?vd_source=6aba70bfaeecdb8314d86a42c169cfd0))