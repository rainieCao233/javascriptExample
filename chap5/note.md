### 引用类型

- Object

```
// 声明对象
var person = new Object();
var person = {
    name : "Nicholas",
    age : 29
};
//获取对象属性
1. person.name
2. person["name"] 
   // 可以通过变量来访问属性
   var propertyName = "name";
   alert(person[propertyName]); //"Nicholas"
   // 若属性名中有导致错误的字符
   person["first name"] = "Nicholas";
```

- Array

> ECMAScript 数组的每一项可以保存任何类型的数据

```
// 声明数组
var colors = new Array(); // new 可省略
var colors = new Array(20);
var colors = new Array("red", "blue", "green");
var colors = ["red", "blue", "green"];
// 数组属性
1. colors.length 
   //通过设置这个属性，可以从数组的末尾移除项或向数组中添加新项
   var colors = ["red", "blue", "green"];
   colors.length = 2;
   alert(colors[2]);   //undefined
   colors.length = 4;
   alert(colors[3]);   //undefined
   colors[colors.length] = "black";
// 检测数组
1. if (value instanceof Array){  //instanceof 假定只有一个全局执行环境
    //对数组执行某些操作
   }
2. if (Array.isArray(value)){
    //对数组执行某些操作
   }
// 转换方法
1. toString()方法会返回由数组中每个值的字符串形式拼接而成的一个以逗号分隔的字符串
2. valueOf()返回的还是数组
3. toLocaleString()方法经常也会返回与toString()和valueOf()方法相同的值，但也不总是如此
4. join()方法只接收一个参数，即用作分隔符的字符串
   var colors = ["red", "green", "blue"];
   alert(colors.join(",")); //red,green,blue
```
> 若数组中的某一项的值是null 或者undefined，那么该值在join()、toLocaleString()、toString()和valueOf()方法返回的结果中以空字符串表示。

```
1. 栈方法 Last-In-First-Out
   var colors = new Array();
   var count = colors.push("red", "green"); // 推入两项 并 返回数组长度
   alert(count); //2
   var item = colors.pop(); // 删除最后一项 并 返回最后一项
   alert(item); //"green"
   alert(colors.length); //1
2. 队列方法 First-In-First-Out
   var colors = new Array(); 
   var count = colors.push("red", "green"); // 推入两项
   var item = colors.shift(); // 删除第一项 并 返回删除项
   alert(item); // "red"
   alert(colors.length); // 1
   var count = colors.unshift("red", "green"); //推入两项
   alert(count); //3
3. 重排序方法
   ----- reverse() -----
   var values = [1, 2, 3, 4, 5];
   values.reverse();
   alert(values); //5,4,3,2,1
   ----- sort() -----
   var values = [0, 1, 5, 10, 15];
   values.sort(); // 默认按照字符串排序
   alert(values); // 0,1,10,15,5
   function compare(value1, value2) {
       return value2 - value1;
   }
   values.sort(compare);  // 按照compare方法进行排序
   alert(values); //0,1,5,10,15
```
```
//操作方法
1. concat()
   var colors = ["red", "green", "blue"];
   var colors2 = colors.concat("yellow", ["black", "brown"]);
   alert(colors2); //red,green,blue,yellow,black,brown
2. slice()
   var colors = ["red", "green", "blue", "yellow", "purple"];
   var colors2 = colors.slice(1);
   var colors3 = colors.slice(1,4); // .slice(start, end)
   // 如果 slice()方法的参数中有一个负数，则用数组长度加上该数来确定相应的位置
   alert(colors2); //green,blue,yellow,purple
   alert(colors3); //green,blue,yellow

   var colors = ["red", "green", "blue"];
   var removed = colors.splice(0,1); // 删除第一项
   alert(colors); // green,blue
   alert(removed); // red
   removed = colors.splice(1, 0, "yellow", "orange"); // 从位置1 开始插入两项
   alert(colors); // green,yellow,orange,blue
   alert(removed); // 返回的是一个空数组
   removed = colors.splice(1, 1, "red", "purple"); // 插入两项，删除一项
   alert(colors); // green,red,purple,orange,blue
   alert(removed); // yellow，返回的数组中只包含一项
```
```
// 位置方法
1. indexOf( 查找项, 查找位置索引 )
2. lastIndexOf( 查找项, 查找位置索引 )
   var numbers = [1,2,3,4,5,4,3,2,1];
   alert(numbers.indexOf(4)); //3
   alert(numbers.lastIndexOf(4)); //5
   alert(numbers.indexOf(4, 4)); //5
   alert(numbers.lastIndexOf(4, 4)); //3 从指定位置向前
   var person = { name: "Nicholas" };
   var people = [{ name: "Nicholas" }];
   var morePeople = [person];
   alert(people.indexOf(person)); //-1 两个对象
   alert(morePeople.indexOf(person)); //0 指同一对象
```
```
// 迭代方法
// 每个方法都接收两个参数：要在每一项上运行的函数和（可选的）运行该函数的作用域对象——影响this 的值。传入这些方法中的函数会接收三个参数：数组项的值、该项在数组中的位置和数组对象本身。
1. every()：如果该函数对每一项都返回true，则返回true
2. filter()：返回 该函数会返回true 的项 组成的数组
3. forEach()：没有返回值
4. map()：返回每次函数调用的结果组成的数组
5. some()：若该函数对任一项返回true，则返回true
```
```
// 归并方法
1. reduce()：从数组的第一项开始，逐个遍历到最后
   var values = [1,2,3,4,5];
   var sum = values.reduce(function(prev, cur, index, array){
       return prev + cur;
   });
   alert(sum); //15
2. reduceRight()：从数组的最后一项开始，向前遍历到第一项
   var values = [1,2,3,4,5];
   var sum = values.reduceRight(function(prev, cur, index, array){
       return prev + cur;
   });
   alert(sum); //15
```