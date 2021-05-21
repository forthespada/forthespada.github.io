# JavaScript



## 1. JavaScript 入门

### 	1. 编程简介

> 客户端与服务器端

> 编译型语言与脚本编程语言

1. URL 类型
   + 相对路径
   + 绝对路径
   + 文件相对路径

## 2.JavaScript语法

### 1. 语句

	**每条语句都以一个分号结束**；

### 2.数据类型

#### 1. 数据类型

+ 数值
+ 字符串
   字符串应当以 **" "** 来包裹。如果要输入具有语义的 **“ ”**,则可以使用转义符 **\\** 。例如： `他说：\“这是一段话。\”`
+ 布尔值
+ 变量
   关键字是**VAR** ，命名规则：
  + 变量名必须以一个字母、$或**_** 开始;
  + 变量名只能包含字母、数字、$、_ ;
  + 变量名区分大小写；
  + 避免使用关键字[^1]；
  + 一次性可以声明多个变量；
#### 2. 操作数据类型和变量

##### 1. 基本算术

```javascript
+ 加法
- 减法
* 乘法
/ 除法
```

##### 2.操作的顺序

	**永远先计算（ ）内的** 	

+ 组合数值：

  ```javascript
  var x=5,y=6,z=x+y;
  alert(z); //结果=11
  ```

+ 组合字符串：

  ```javascript
  var FirstName = "John" , LastName = "Smith" , FullName = FirstName + " " + LastName;
  alert(FullName); //结果=John Smith
  ```

+ 组合数值和字符串：

  ```javascript
  var VisitNum = 10000,message = "Numbers of Visits:"+ VisitNum ; 
  alert(message);
  ```

  ​**JavaScript可能将一个数值转换为一个字符串，例如在填写表单时。为了防止这种我们不期望发生地转换，我们可以采取以下办法**

>  （这在我们以下面的一串代码为例：）

```javascript
var NumofShoes = "2",
    NumofSocks = 4,
    TotalItem  = NumofShoes + NumofSocks;
alert(TotalItem);
```

+ 将加号至于 `NumofShoes` 前，即：

  ```javascript
  var TotalItem = +NumofShoes + NumofSocks     //这这里，加号是紧靠着变量的，中间无空格。这样可以让字符串转换为数字
  ```

  有这样一个例子：

  ```javascript
  var x = "5",y = 3,z = +x + y;
  alert(z);//输出的结果是5+3=8；

  var x = "5",y = "3",z = +x + +y;
  alert(z);//输出的结果是5+3=8；

  var x = "5",y = "3",z = +x  +y;
  alert(z);//输出的结果是“5”+"3"=53；
  ```

+ 使用 `Number()` 命令：

  ```javascript
  var NumofShoes = "2",
      NumofSocks = 4,
      TotalItem = Number(NumofShoes) + NumofSocks;
  alert(TotalItem);//输出的结果为6；
  ```

  > Number()在可能的情况下可以把一个字符串转换为数值；如果要转换的字符串非数字字符串，则可能被转换成NaN

##### 3. 修改变量中的值

```javascript
x = x + 3 ;
```

以上式子可以简写为 ` x += 3 ` （ `+=` 之间不可以有空格），同样地可以有以下的简写方法：

```javascript
x *= 3 // x = x * 3;
x /= 3 // x = x / 3;
x %= 3 // x = x % 3;
x ++   // x = x + 1; (同理，++之间不可以有空格)
x --   // x = x - 1;
```

这种修改方式同样适用于字符串：

```javascript
var message = "Hello", name = "Bob" ,message = message + " " + name;
alert(message);
```

+ [x] 类似的，可以将代码修改为**(未成功)**：

```javascript
var message = "Hello", 
    name = "Bob" ,
    message += " " + name;
alert(message);
```

#### 3.数组

##### 1. 数组的创建

数组使用来存储一系列的数据，凡是有一定规律或相关关系的数据值、字符串，皆可组成数组。

```javascript
var week = [ "mon" , "tues" , "wed" , "thurs" , "fri" , "sat" , "sun"]; //方法一
var week = new Array ("mon" , "tues" , "wed" , "thurs" , "fri" , "sat" , "sun"); //方法二
```

也可以创建一个空数组，以便日后向内填充内容，例如：购物车单，歌曲列表等等。

```javascript
var PlayList = [];
```

##### 2.数组的访问

```javascript
var week = [ "mon" , "tues" , "wed" , "thurs" , "fri" , "sat" , "sun"]; 
alert(week[0]) //返回值为 mon
```

**数组中第一个值的索引值为0。**

要想访问最后一项数组中的值，只需要知道这个数组中一共有多少项即可，这个任务我们可以通过 `length` 属性来执行：

```javascript
week[week.length-1]; //等价于 week[6] ,这里假设length为7
```

也可以使用变量的方法来找到想要的值：

```javascript
var i=0;
alert(week[i]);
```

##### 3.　向数组中添加项目

1.　要想向数组中添加新值，可以：

```javascript
week[0] = "mon" ;
```

	这样可以向数组中添加一个索引值为0，即位于第一位的数值，上面的数则　会被更改为：

```javascript
var week = [ "mon" , "mon" , "tues" , "wed" , "thurs" , "fri" , "sat" , "sun"]; 
```

2.　向数组的末尾添加项目：

+　直接添加，在知道末尾值的情况下：

```javascript
week [7] = "sun2" //仍然使用上面的例子；
```

+ 或者使用 `length` 属性：

```javascript
week.
```



## 附：部分功能

### 1. 请求消息

```javascript
var name = prompt("What's your name?","Please input your name")
```

> 没有在IE7 中激活的话 ，是不允许`prompt()`方法

这句话的意思就是将用户填写的信息“what's your name”中的内容放入变量`name` 中，之后就可以以想要的方式去使用这个变量。例如：

```java
document.write("<p>" + "Hello " + name + "!" + "</p>")
```



[^1]: 关键字包括：