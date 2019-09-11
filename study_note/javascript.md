## 基本概念

声明变量 ```var count =10```;

与c语言类似

布尔操作符操作一个值无论是什么数据类型都会先自动把该值转换成布尔类型

boolean类型只有true和false

!!"blue"等价于Boolean()函数

#### 加性操作符

5+“5”结果会是“55”字符串值 

有字符串类型则会都转换成字符串类型

#### for in 语句

可以用来枚举对象的属性

for (property in expression) statement

如``` for (var propName in window) {``` 

```document.write(propName);```

```}```

#### label 语句



#### with 语句



#### switch语句

可以使用任何数据类型



#### 函数

格式 ```function functionName(arg0,arg1,..) {```

```statements```

```}```

参数实际上是放在一个参数数组中，从而参数不是必须命名的

```javascript
arguments.length返回参数个数	
```

###### **没有重载**

是通过接受的参数的类型和数量 后定义的函数覆盖了先定义的函数



## 变量，作用域和内存问题

基本类型值和引用类型值 基本类型值是简单的数据段，引用类型值是对象类型

则复制引用型变量时实际上是创建一个新的指针，改变obj1的属性也会改变obj2

**javascript的参数是按值传递的**

typeof操作符用来判断变量类型



### 执行环境及作用域

执行环境：定义了变量或函数有权访问的其他数据，决定了它们各自的行为

执行环境特性： 内部环境可以通过作用域链访问所有的外部环境，但外部环境不能访问内部环境中的任何变量和函数(建立在函数基础之上)

`var color = "blue";`

`function changeColor(){`

`var anotherColor = "red";`

`function swapColors(){`

`var tempColor = anotherColor;`

`anotherColor = color;`

`color=tempColor;`

`}//这里可以访问 color、 anotherColor 和 tempColor`

`swapColors();// 这里可以访问 color 和 anotherColor，但不能访问 tempColor `

`}`

`changeColor();`

![1568188092586](C:\Users\ADMINI~1\AppData\Local\Temp\1568188092586.png)

作用域链的前端始终是当前执行的代码所在环境的变量对象

标识符解析是沿着作用域链一级一级地搜索标识符的过程。搜索过程始终从作用域链的前端开始，
然后逐级地向后回溯，直至找到标识符为止（如果找不到标识符，通常会导致错误发生）。 

#### 延长作用域链

当执行流进入下列任何一个语句时，作用域链就会
得到加长：
 try-catch 语句的 catch 块；
 with 语句。
这两个语句都会在作用域链的前端添加一个变量对象。对 with 语句来说，会将指定的对象添加到
作用域链中。对 catch 语句来说，会创建一个新的变量对象，其中包含的是被抛出的错误对象的声明。 

``function buildUrl() {`
`var qs = "?debug=true";`
`with(location){`
`var url = href + qs;`
`}`
`return url;`
`}`

在此with语句接收的是location对象，因此其变量对象中就包含了 location 对象的所有属
性和方法，而这个变量对象被添加到了作用域链的前端  

#### 没有块级作用域

`for (var i=0; i < 10; i++){`
`doSomething(i);`
`}`
`alert(i); //10` 

因为由 for 语句创建的变量 i 即使在 for 循环执行结束后，也依旧会存在
于循环外部的执行环境中 

使用 var 声明的变量会自动被添加到最接近的环境中。在函数内部，最接近的环境就是函数的局部
环境；在 with 语句中，最接近的环境是函数环境。 

如果初始化变量时没有使用 var 声明，该变量会自动被添加到全局环境。 

**查询标识符** 

当在某个环境中为了读取或写入而引用一个标识符时，必须通过搜索来确定该标识符实际代表什
么。搜索过程从作用域链的前端开始，向上逐级查询与给定名字匹配的标识符。如果在局部环境中找到
了该标识符，搜索过程停止，变量就绪。 



## 引用类型

#### Object类型

创建实例方式 1`var person = new Object();`

对象字面量 

``var person = {`
`name : "Nicholas",`
`age : 29`
};` //注意最后一个属性没有逗号

对象字面量也是向函数传递大量可选参数的首选方式 

`function displayInfo(args) {`
`var output = "";`
`if (typeof args.name == "string"){` 

`output += "Name: " + args.name + "\n";`
`}`
`if (typeof args.age == "number") {`
`output += "Age: " + args.age + "\n";`
`}`
`alert(output);`
`}` 

`displayInfo({`

​	name:"Nicholas",

​	age:29

`})`;



#### Array类型

特点：1.ECMAScript 数组的每一项可以保存任何类型的数据 

2.ECMAScript 数组的大小是可以动态调整的，即可以随着数据的添加自动增长以容
纳新增数据

创建方式1

`var colors = new Array(20);`//该代码将创建length值为20的数组

创建方式2 数组字面量表示法 

var colors = ["red", "blue", "green"]; 

