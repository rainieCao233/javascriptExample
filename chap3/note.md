### 基本概念

#### 语法
- 区分大小写
- 标识符
 > 指变量、函数、属性的名字，或者函数的参数
 > 
 > 第一个字符必须是一个字母、下划线（_）或一个美元符号（$）；其他字符可以是字母、下划线、美元符号或数字。
- 注释
- 严格模式
 > 严格模式是为JavaScript 定义了一种不同的解析与执行模型。在严格模式下，ECMAScript 3 中的一些不确定的行为将得到处理，而且对某些不安全的操作也会抛出错误。

 ```
function doSomething(){
    "use strict";
    //函数体
}
 ```
- 语句
 > 分号结尾

#### 关键字与保留字
 > 关键字：可用于表示控制语句的开始或结束，或者用于执行特定操作等。
 > 
 > 保留字：不能用作标识符


#### 变量
> 如果在函数中使用var 定义一个变量，那么这个变量在函数退出后就会被销毁

#### 数据类型
> Undefined、Null、Boolean、Number、String、Object

- typeof操作符
> "object"——如果这个值是对象或null；

- undefined类型
> 无论在什么情况下都没有必要把一个变量的值显式地设置为undefined

```
var message; 
// var age
alert(message); // "undefined"
alert(age); // 产生错误
alert(typeof message); // "undefined"
alert(typeof age); // "undefined"
```

- Null类型
> 从逻辑角度来看，null 值表示一个空对象指针，而这也正是使用typeof 操作符检测null 值时会返回"object"的原因
>
> 只要意在保存对象的变量还没有真正保存对象，就应该明确地让该变量保存null 值

```
alert(null == undefined); //true
alert(null === undefined); //false
```

- Boolean类型
> 两个字面值：true 和false，True 和False（以及其他的混合大小写形式）都不是Boolean 值，只是标识符。

数据类型 | 转换为true的值 | 转换为false的值
---|---
Boolean | true | fasle
String | 任何非空字符串 | ""
Number | 任何非零数字 | 0/NaN
object | 任何对象 | nuill
undefined | 不适用 | undefined

- Number类型
> 整数和浮点数值（浮点数值在某些语言中也被称为双精度数值）

 - 浮点数值
 > 所谓浮点数值，就是该数值中必须包含一个小数点，并且小数点后面必须至少有一位数字

    ```
    //浮点数值的最高精度是 17 位小数，但在进行算术计算时其精确度远远不如整数
    0.1 + 0.2 = 0.30000000000000004!
    ```

 - 数值范围
    ```
    Number.MIN_VALUE = 5e-324;
    Number.MAX_VALUE = 1.7976931348623157e+308;
    ```
 > 如果某次计算的结果得到了一个超出JavaScript 数值范围的值，那么这个数值将被自动转换成特殊的+/-Infinity 值
 >
 > isFinite()

 - NaN
 > NaN，即非数值（Not a Number）是一个特殊的数值，这个数值用于表示一个本来要返回数值的操作数未返回数值的情况
 >
 > NaN != NaN
 >
 > isNaN()在接收到一个值之后，会尝试
将这个值转换为数值；isNaN(object)->valueOf()->toString()

 - 数值转换
 > Number()、parseInt()和parseFloat()

    ```
var num1 = Number("Hello world!"); //NaN
var num2 = Number(""); //0
var num3 = Number("000011"); //11
var num4 = Number(true); //1
var num5 = Number(null); //0
var num6 = Number(undefined); //NaN
    ```
    ```
var num1 = parseInt("1234blue"); // 1234
var num2 = parseInt(""); // NaN
var num3 = parseInt("0xA"); // 10（十六进制数）
var num4 = parseInt(22.5); // 22
var num5 = parseInt("0xf"); // 15（十六进制数）
var num6 = parseInt("70"); // 70（十进制数）
//ECMA3中070表示56，但ECMA5中表示70，稳妥的方式如num8
var num7 = parseInt("070"); // 56（八进制数）
var num8 = parseInt("70", 8); //56
    ```
    ```
//parseFloat()只解析十进制值
var num1 = parseFloat("1234blue"); //1234 （整数）
var num2 = parseFloat("0xA"); //0
var num3 = parseFloat("22.5"); //22.5
var num4 = parseFloat("22.34.5"); //22.34
var num5 = parseFloat("0908.5"); //908.5
var num6 = parseFloat("3.125e7"); //31250000
    ```

- String类型
 > String 类型用于表示由零或多个16 位Unicode 字符组成的字符序列，即字符串

    ```
//toString()
var num = 10;
alert(num.toString(2)); // "1010"
//String()
var value1;
alert(String(10)); // "10"
alert(String(true)); // "true"
alert(String(null)); // "null"
alert(String(value1)); // "undefined"
    ```

- Object类型
 > 对象其实就是一组数据和功能的集合
 >
 > var o = new Object();
 >
 > Object 的每个实例都具有下列属性和方法。
 >
 >constructor:保存着用于创建当前对象的函数。
 >
 >hasOwnProperty(propertyName):用于检查给定的属性在当前对象实例中
 >
 >isPrototypeOf(object)：用于检查传入的对象是否是传入对象的原型
 >
 >propertyIsEnumerable(propertyName)：用于检查给定的属性是否能够使用for-in 语句来枚举。
 >
 >toLocaleString()：返回对象的字符串表示，该字符串与执行环境的地区对应。
 >
 >toString()：返回对象的字符串表示。
 >
 >valueOf()：返回对象的字符串、数值或布尔值表示。

#### 操作符

- 一元操作符
 - 递增和递减操作符
    ```
var age = 29;
++age; //30
--age; //28
//操作符前置后置的区别是否先增减再操作
var s1 = "2";
var s2 = "z";
var b = false;
var f = 1.1;
var o = {
valueOf: function() {
return -1;
}
};
s1++; // 值变成数值3
s2++; // 值变成NaN
b++; // 值变成数值1
f--; // 值变成0.10000000000000009（由于浮点舍入错误所致）
o--; // 值变成数值-2
    ```

 - 一元加减操作符
 > 对非数值应用一元加操作符时，该操作符会像Number()转型函数一样对这个值执行转换。

- 位操作符
> 负数以二进制码存储，使用的格式是二进制补码，先求其绝对值的二进制码，再求二进制反码，最后将得到的二进制反码加1。

 -  非（NOT）
    ```
//执行按位非的结果就是返回数值的反码
var num1 = 25; // 二进制00000000000000000000000000011001
var num2 = ~num1; // 二进制11111111111111111111111111100110
alert(num2); // -26
//按位非操作的本质：操作数的负值减1。
    ```
 - 与（AND）
    ```
var result = 25 & 3;
alert(result); //1
    ```

 - 或（OR）
    ```
var result = 25 | 3;
alert(result); //27
    ```

 - 异或（XOR）
    ```
var result = 25 ^ 3;
alert(result); //26
    ```

 - 左移
    ```
var oldValue = 2; // 等于二进制的10
var newValue = oldValue << 5; // 等于二进制的1000000，十进制的64
    ```

 - 有符号的右移
    ```
爸爸开心了再研究
    ```
 - 无符号右移
    ```
爸爸开心了再研究
    ```

- 布尔操作符
 - 非（!）
 > 模拟Boolean()转型函数的行为再取反
 - 与（&&）
![and_rule.png](http://upload-images.jianshu.io/upload_images/1801528-533c088c29c9eb91.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 - 或（||）
![or_rule.png](http://upload-images.jianshu.io/upload_images/1801528-996dbdf4eb4f62e2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 乘性操作符
 - 乘
 > 如果乘积超过了ECMAScript 数值的表示范围，则返回Infinity 或-Infinity

    ```
NaN * a = NaN;
Infinity * 0 = NaN;
Infinity * (+/-)a = (+/-)Infinity 
Infinity * Infinity = Infinity;
    ```
 - 除
 > 如果商超过了ECMAScript 数值的表示范围，则返回Infinity 或-Infinity

    ```
NaN / a = NaN;
Infinity / Infinity = NaN;
0 / 0= NaN;
(+/-)a / 0 = (+/-)Infinity ;
Infinity / (+/-)a = (+/-)Infinity 
    ```
 - 求模
 > 求模（余数）操作符由一个百分号（%）表示

    ```
Infinity % a = NaN;
a % 0 = NaN;
Infinity % Infinity = NaN;
a % Infinity = a;
0 % a = 0;
    ```

- 加性操作符
 - 加
    ```
NaN + a = NaN;
Infinity + Infinity = Infinity;
Infinity - Infinity = NaN;
-Infinity - Infinity = -Infinity;
"ab" + "cd" = "abcd";
"ab" + 7 = "ab7";
    ```

 - 减法
     ```
NaN - a = NaN;
Infinity - Infinity = NaN;
-Infinity - Infinity = -Infinity;
5 - "2" = 3;
5 - null = 5;
    ```

- 关系操作符
> 小于（<）、大于（>）、小于等于（<=）和大于等于（>=）

  ```
var result = "Brick" < "alphabet"; //true
var result = "Brick".toLowerCase() < "alphabet".toLowerCase(); //false
var result = "23" < "3"; //true
var result = "23" < 3; //false
var result = "a" < 3; // false，因为"a"被转换成了NaN
//任何操作数与NaN 进行关系比较，结果都是false。
  ```

- 相等操作符
 - 相等和不相等
 > ==/!=
 
    ![special_rules.png](http://upload-images.jianshu.io/upload_images/1801528-1eb45585561cdeff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 - 全等和不全等
 > ===/!== 不允许类型转换

- 条件操作符
> variable = boolean_expression ? true_value : false_value;

- 赋值操作符
> 等于号（=）
> 
> *= | /= | %= | += | -= | <<= | >>= | >>>=

- 逗号操作符
 ```
var num1=1, num2=2, num3=3;
var num = (5, 1, 4, 8, 0); // num 的值为0
 ```

#### 语句

- if语句
```
if (i > 25) {
    alert("Greater than 25.");
} else {
    alert("Between 0 and 25, inclusive.");
}
```

- do-while语句
  ```
//最常用于循环体中的代码至少要被执行一次的情形
do {
    i += 2;
} while (i < 10);
  ```

- while语句
  ```
while (i < 10) {
    i += 2;
}
  ```

- for语句
  ```
for (var i = 0; i < count; i++){
    alert(i);
}
  ```

- for-in语句
  ```
//通过for-in 循环输出的属性名的顺序是不可预测的
for (var propName in window) {
    document.write(propName);
}
  ```

- label语句
  ```
start: for (var i=0; i < count; i++) {
    alert(i);
}
  ```

- break和continue语句
  ```
//break/continue跳出循环，但continue会继续做之后的循环
-----------break + label-----------
var num = 0;
outermost:
    for (var i=0; i < 10; i++) {
        for (var j=0; j < 10; j++) {
            if (i == 5 && j == 5) {
                break outermost;
            }
            num++;
        }
    }
alert(num); //55
-----------continue + label-----------
var num = 0;
outermost:
    for (var i=0; i < 10; i++) {
        for (var j=0; j < 10; j++) {
            if (i == 5 && j == 5) {
                continue outermost;
            }
            num++;
        }
    }
alert(num); //95
  ```

- with语句
  ```
//with 语句的作用是将代码的作用域设置到一个特定的对象中
var qs = location.search.substring(1);
var hostName = location.hostname;
var url = location.href;
//以上三行均有location对象
with(location){
    var qs = search.substring(1);
    var hostName = hostname;
    var url = href;
}
  ```

- switch语句
  ```
//switch 语句在比较值时使用的是全等操作符
switch (expression) {
    case value: statement
        break;
    case value: statement
        break;
    default: statement
}
----------其他用法----------
var num = 25;
switch (true) {
    case num < 0:
        alert("Less than 0.");
        break;
    case num >= 0 && num <= 10:
        alert("Between 0 and 10.");
        break;
    case num > 10 && num <= 20:
        alert("Between 10 and 20.");
        break;
    default:
        alert("More than 20.");
}
  ```

#### 函数
> 严格模式对函数有一些限制：
> 
>  不能把函数命名为eval 或arguments；
> 
>  不能把参数命名为eval 或arguments；
> 
>  不能出现两个命名参数同名的情况。

- 理解参数
> 参数在内部是用一个数组来表示的，并可在函数体内可以通过arguments 对象来访问参数数组

    ```
//下例中，修改arguments[1]，也就修改了num2，它们的内存空间是独立的，但它们的值会同步
//如果只传入了一个参数，那么为arguments[1]设置的值不会反应到命名参数中
function doAdd(num1, num2) {
arguments[1] = 10;
alert(arguments[0] + num2);
}
//ECMAScript 中的所有参数传递的都是值，不可能通过引用传递参数。
    ```

 > ECMAScript 函数不能像传统意义上那样实现重载，如果在ECMAScript 中定义了两个名字相同的函数，则该名字只属于后定义的函数

    ```
function addSomeNumber(num){
return num + 100;
}
function addSomeNumber(num) {
return num + 200;
}
var result = addSomeNumber(100); //300
//通过检查传入函数中参数的类型和数量并作出不同的反应，可以模仿方法的重载。
    ```















