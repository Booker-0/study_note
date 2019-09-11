## 基本概念

声明变量 ```var count =10```;

与c语言类似

布尔操作符操作一个值无论是什么数据类型都会先自动把该值转换成布尔类型

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

###### 没有重载

是通过接受的参数的类型和数量 后定义的函数覆盖了先定义的函数



## 变量，作用域和内存问题

