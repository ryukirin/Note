# JS笔记

## 初识JS

### 浏览器执行JS简介

浏览器分为：

- 渲染引擎：用来解析HTML和CSS，俗称内核。比如chrome的blink
- JS引擎：也成为JS解释器，用来读取JS代码并对其进行后台处理。比如chrome的V8

### JS的组成

- ECMAScript: JavaScript语法，规定了JS的编程语法和基础核心知识，是所有浏览器厂商共同遵循的一套JS语法工业领域
- DOM：页面文档对象类型，可以通过DOM提供的接口对页面上的各种元素进行操作（大小位置颜色等）
- BOM：浏览器对象模型，通过BOM可以操作浏览器窗口

### JS的三种书写方式

- 行内式

  特殊情况下使用。更推荐使用单引号

- 内嵌式

  学习时常用

- 外部JS

  ```html
  <script src="./test.js"></script>
  script中间不允许有代码
  ```

  适合JS代码量大的场合

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 内嵌式JS -->
    <script>
        // 单行注释 ctrl+/
        /* 多行注释 
        shift+alt+a */
        alert("Liella!")
    </script>

    <!-- 外部JS -->
    <script src="./test.js"></script>
</head>

<body>
    <!-- 行内式js 直接写到元素内部 -->
    <!-- <input type="button" value="Liella!" onclick="alert('LoveLive! SuperStar')"> -->
</body>

</html>
```

### 输入输出

```javascript
// 输入框 用户可输入
prompt('input your age:')
// alert 弹出警示框
alert('result is:')
// console 控制台输出
console.log('hello world')
```

## 变量

```javascript
//声明变量
var 变量名;
//赋值
变量名 = 数值;
//声明变量并赋值（变量的初始化）
var 变量名 = 数值;
```

获取输入框（prompt）的信息

```javascript
var usrName = prompt('请输入姓名：');
```

声明多个变量

```javascript
var age = 14,
    usrName = 'jack';
```

声明变量特殊情况

- 只声明不赋值

  输入显示为undefined

- 不声明不赋值

  能运行，运行到这一行会报错

- 只赋值不声明

  能运行，不报错，正确，但是不提倡用

### 命名规范

- 由字母、数字、下划线、美元符号组成，如usrAge,num01,_name
- 严格区分大小写
- 不能以数字开头
- 不能是关键字
- 变量命名必须有意义
- 遵循驼峰命名法，首字母小写，后边单词的首字母大写，如myFirstName
- 尽量不要使用name作为变量名

## 数据类型

JS的数据类型是只有在程序运行的过程中，根据等号右边的值来确定的。

一个变量的数据类型可以变

```javascript
var x = 12;
x = 'a';
```

### 分类

- 简单数据类型：Number，String（默认""），Boolean（默认false），Undefined，Null
- 复杂数据类型：object

#### 数字型

包含整型和浮点数型，默认0

八进制：数字前加0就表示八进制

```js
var num01 = 010;
console.log(num01);
//8
```

十六进制：数字前加0x就表示十六进制

```js
var num02 = 0x11;
console.log(2);
//17
```

最大值和最小值

```js
console.log(Number.MAX_VALUE);
console.log(Number.MIN_VALUE);
//1.7976931348623157e+308
//5e-324
```

三个特殊值

```js
// 三个特殊值
// 无穷大
alert(Infinity);
console.log(Number.MAX_VALUE * 2);
// 负无穷
alert(-Infinity);
console.log(-Number.MAX_VALUE * 2);
// 非数值
alert(NaN);
console.log('num' - 100);
```

isNaN

```js
// isNaN 如果是数字则返回false 不是数字返回true
console.log(isNaN(12));
console.log(isNaN('num'));
//注：这里若是console.log(isNaN('12'));则也返回false
```

#### 字符串型

一般推荐单引号，当字符串内部也需要单引号的时候，使用外双内单或者外单内双。

转义符（表格中\后均不应带空格）

| 转义符 | 说明    |
| ------ | ------- |
| \ n    | 换行    |
| \ \    | 斜杠\   |
| \ '    | 单引号  |
| \ "    | 双引号  |
| \ t    | tab缩进 |
| \ b    | 空格    |

获取字符串长度

```js
var str = 'abcdefg';
console.log(str.length);
//7
```

字符串的拼接

```js
var newStr = 'xyz';
console.log(str + newStr);
//abcdefgxyz
console.log(str + 7);
//abcdefg7
console.log(7 + 7);
//14
console.log('7' + 7);
//77
```

#### 布尔型

true参加运算当1来看

false参加运算当0来看

```js
flag = true;
flag1 = false;
console.log(flag + 1);
//2
console.log(flag1 - 1);
//-1
console.log(flag / 1);
//1
console.log(flag1 * 1);
//0
```

#### Undefined和Null

```js
var v = undefined;
var space = null;
console.log(v + 'number');
//undefinednumber
console.log(space + 'number');
//nullnumber
console.log(v + 1);
//NaN
console.log(space + 1);
//1
```

### 检测数据类型

```js
var num01 = 12;
console.log(typeof num01);
//number
//null的类型检测出来会是object
var space = null;
console.log(typeof space);
//object
```

### 数据类型转换

- 转换为字符串类型
- 转换为数字型
- 转换为布尔型

#### 转换为字符串类型

| 方式                       | 说明                         | 案例                              |
| -------------------------- | ---------------------------- | --------------------------------- |
| toString()                 | 转成字符串                   | var num=1; alert(num.toString()); |
| String()强制转换           | 转成字符串                   | var num=1; alert(String(num));    |
| 加号拼接字符串（隐式转换） | 和字符串拼接的结果都是字符串 | var num=1; alert(num+'');         |

#### 转换为数字型

| 方式                   | 说明                         | 案例                |
| ---------------------- | ---------------------------- | ------------------- |
| parseInt(string)函数   | 将string转换为整数数值型     | parseInt('78')      |
| parseFloat(string)函数 | 将string转换为浮点数数值型   | parseFloat('78.21') |
| Number()强制转换       | 将string转换为数值型         | Number('12')        |
| js隐式转换（- * /）    | 利用算术运算隐式转换为数值型 | '12'-0              |

- 前两个转换时只会把这段字符串前一个符合格式的数字转换为数字型

  如：parseInt(12.22.1) 为12 parseFloat(12.22.1) 为12.22

  parseInt(12.2aaaaa2.1) 为12 parseFloat(12.2aaaaa2.1) 为12.2

  而Number()则是必须整个字符串必须是符合格式的数字

  如：Number('12.22.1') 为NaN

#### 小案例

```js
 var bYear = prompt("请输入您的出生年：");
 var date = new Date();
 var tYear = date.getFullYear();
 console.log(tYear);
 //隐式转换
 var age = tYear - bYear;
 alert("您今年" + age + "岁");
```

```js
 var a = prompt("请输入第一个值");
 var b = prompt("请输入第二个值");
 if (!isNaN(a) && !isNaN(b)) {
     var sum = (a - 0) + (b - 0);
     // var sum = parseFloat(a) + parseFloat(b);
     alert("两数之和为：" + sum);
 }
 else {
     alert("请输入数字!");
 }
```

#### 转换为布尔型

| 方式          | 说明               | 案例             |
| ------------- | ------------------ | ---------------- |
| Boolean()函数 | 其他类型转成布尔值 | Boolean("true"); |

- 代表空和否定的值会被转换为false，如''、0、NaN、null、undefined
- 其余值都会被转换成true

### 案例

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var usrName = prompt('请输入姓名：');
        var usrAge = prompt('请输入年龄：');
        var usrSex = prompt('请输入性别：');
        alert('您的姓名是：' + usrName +
            '\n您的年龄是：' + usrAge +
            '\n您的性别是：' + usrSex);
    </script>
</head>

<body>
```

## JS运算符

### 算术运算符

%取模（余数）

```js
console.log(5 % 3);
//2
```

浮点数算术运算会有问题（精度问题），避免用浮点数直接运算

不要直接拿着运算后的浮点数和浮点数比较是否相等

```js
var num = 0.2 + 0.1;
console.log(num == 0.3);
//false
```

### 递增递减运算符

- 前置递增运算符：

  ++num，自加1，先自加再返回值

- 后置递增运算符：

  num++，自加1，先返回值再自加

```js
// 前置递增运算符 先自加再返回值
var p = 10;
console.log(++p + 10);//21
// 后置递增运算符 先返回值再自加
p = 10;
console.log(p++ + 10);//20
//1.p++ = 11 但是返回10
//2.++p = 12
p = 10;
console.log(p++ + ++p);//22
```

### 比较运算符

```js
//==可以把字符串型转换为数字型
console.log(18 == '18');//true
console.log(18 === '18');//false
```

### 逻辑运算符

| 逻辑运算符 | 说明       | 案例          |
| ---------- | ---------- | ------------- |
| &&         | 逻辑与 and | true&&false   |
| \|\|       | 逻辑或 or  | true\|\|false |
| !          | 逻辑非 not | !true         |

#### 逻辑中断（短路运算）

- &&逻辑中断

  表达式1&&表达式2，若表达式1为真则返回表达式2，若表达式1为假则返回表达式1

  ```js
  console.log(123 && 456);//456
  console.log(0 && 456);//0
  console.log(0 && 456 && 78945);//0
  ```

- ||逻辑中断

  表达式1||表达式2，若表达式1为真则返回表达式1，若表达式1为假则返回表达式2

  ```js
  console.log(123 || 456);//123
  console.log(0 || 456);//456
  console.log(0 || 456 || 2367);//456
  console.log(0 || 0 || 2367);//2367
  ```

### 赋值运算符

| 赋值运算符 | 说明                 | 案例                        |
| ---------- | -------------------- | --------------------------- |
| =          | 直接赋值             | var usrName = 'Jack';       |
| +=、-=     | 加、减一个数后再赋值 | var age = 10; age += 5;//15 |
| *=、/=、%= | 乘、除、取模后再赋值 | var age = 10; age *= 5;//50 |

### 运算符优先级

| 优先级 | 运算符     | 顺序           |
| ------ | ---------- | -------------- |
| 1      | 小括号     | ()             |
| 2      | 一元运算符 | ++ -- !        |
| 3      | 算术运算符 | **先*/%后+-**  |
| 4      | 关系运算符 | > >= < <=      |
| 5      | 相等运算符 | == != !== ===  |
| 6      | 逻辑运算符 | **先&&后\|\|** |
| 7      | 赋值运算符 | =              |
| 8      | 逗号运算符 | ,              |

## 流程控制

案例1：判断闰年

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var year = prompt('请输入年份：');
        if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
            alert(year + '是闰年');
        }
        else {
            alert(year + '是平年');
        }
    </script>
</head>

<body>
</body>
</html>
```

案例2：判断成绩

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var score = prompt('请输入成绩：');
        //从大到小写可以节省代码，不用再写上限
        if (score >= 90) {
            alert('A');
        }
        else if (score >= 80) {
            alert('B');
        }
        else if (score >= 70) {
            alert('C');
        }
        else if (score >= 60) {
            alert('D');
        }
        else {
            alert('E');
        }
    </script>
</head>

<body>
</body>
</html>
```

案例3：三元表达式（相当于一个if else语句）

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var year = prompt("请输入年份：");
        //条件表达式?表达式1:表达式2
        //条件表达式为真则返回表达式1，为假则返回表达式2
        //alert(year % 4 == 0 && year % 100 != 0 || year % 400 == 0 ? '是闰年' : '是平年');
        var result = year % 4 == 0 && year % 100 != 0 || year % 400 == 0 ? '是闰年' : '是平年';
        alert(result);
    </script>
</head>

<body>
</body>

</html>
```

案例4：查询水果

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var fName = prompt('请输入名称：');
        //switch语句匹配必须是全等（===）
        switch (fName) {
            case '苹果':
                alert('3.5rmb/kg');
                break;
            case '西瓜':
                alert('13.5rmb/kg');
                break;
            case '橘子':
                alert('6.5rmb/kg');
                break;
            case '香蕉':
                alert('2.5rmb/kg');
                break;
            default:
                alert('没有此水果');
        }
    </script>
</head>

<body>
</body>
</html>
```

有判断固定值用switch，有判断范围用if esle if

## 循环

案例1：求和

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var sum = 0;
        // 求1-100之间所有整数的和
        for (var i = 1; i <= 100; i++) {
            // sum = sum + i;
            sum += i;
        }
        console.log(sum);
        // 求1-100之间所有整数的平均值
        var avg = sum / 100;
        console.log(avg);
        // 求1-100之间所有奇数和偶数的和
        sum1 = 0;
        sum2 = 0;
        for (var i = 1; i <= 100; i++) {
            if (i % 2 == 0) {
                sum1 += i;
            }
            else if (i % 2 == 1) {
                sum2 += i;
            }
        }
        console.log(sum1);
        console.log(sum2);
        // 求1-100之间所有能被3整除的数字的和
        sum = 0;
        for (var i = 1; i <= 100; i++) {
            if (i % 3 == 0) {
                sum += i;
            }
        }
        console.log(sum);
    </script>
</head>

<body>
</body>
</html>
```

案例2：求学生成绩

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var sum = 0, avg = 0, num = prompt('请输入班级人数：');
        for (var i = 1; i <= num; i++) {
            score = Number(prompt('请输入第' + i + '个学生的成绩：'));
            sum += score;
        }
        avg = sum / num;
        alert('该班级的总成绩为：' + sum + '\n平均成绩为：' + avg);
    </script>
</head>

<body>
</body>
</html>
```

案例3：输出星星金字塔

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var num = prompt('请输入要打印星星的行数：');
        var str = '';
        for (var i = num; i > 0; i--) {
            for (var j = i; j > 0; j--) {
                str = str + '⭐';
            }
            str = str + '\n';
        }
        console.log(str);
    </script>
</head>

<body>
</body>

</html>
```

案例3：输出九九乘法表

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var str = '';
        for (var i = 1; i <= 9; i++) {
            for (var j = 1; j <= i; j++) {
                str = str + j + '×' + i + '=' + Number(i) * Number(j) + '\t'
            }
            str = str + '\n';
        }
        console.log(str);
    </script>
</head>

<body>
</body>
</html>
```

案例4：while循环

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var i = 1;
        while (i <= 100) {
            console.log(i + '岁');
            i++;
        }
        // 求1-100之间所有整数的和
        var sum = 0, num = 0;
        while (num <= 100) {
            sum += num;
            num++;
        }
        console.log(sum);        
        var love = prompt('你爱我吗？');
        while (love != '我爱你') {
            love = prompt('你爱我吗？');
        }
    </script>
</head>

<body>
</body>

</html>
```

案例5：do while循环

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var i = 1;
        do {
            console.log(i + '岁');
            i++;
        }
        while (i <= 100)
        // 求1-100之间所有整数的和
        var sum = 0, num = 0;
        do {
            sum += num;
            num++;
        } while (num <= 100)
        console.log(sum);
        do {
            var love = prompt('你爱我吗？');
        } while (love != '我爱你')
    </script>
</head>

<body>
</body>

</html>
```

案例6：continue和break

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        //遇到坏包子扔掉继续吃
        var sum = 0;
        var bao = ['正常', '正常', '坏了', '正常', '正常'];
        for (var i = 0; i < 5; i++) {
            if (bao[i] == '坏了') {
                continue;
            }
            var num = i + 1;
            console.log('正在吃第' + num + '个包子');
            sum++;
        }
        console.log('一共吃了' + sum + '个包子');
        //遇到坏包子就不继续吃了
        sum = 0;
        for (var i = 0; i < 5; i++) {
            if (bao[i] == '坏了') {
                break;
            }
            var num = i + 1;
            console.log('正在吃第' + num + '个包子');
            sum++;
        }
        console.log('一共吃了' + sum + '个包子');
        //求1-100不可以被7整除的数字之和
        sum = 0;
        for (var i = 1; i <= 100; i++) {
            if (i % 7 == 0) {
                continue;
            }
            sum += i;
        }
        console.log(sum);
        //1-100除去个位是3的数的和
        var sum = 0;
        for (var i = 1; i <= 100; i++) {
            if (i % 10 == 3) {
                continue;
            }
            sum += i;
        }
        console.log(sum);
    </script>
</head>

<body>
</body>

</html>
```

案例7：简易ATM

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var num = prompt('请输入你要的操作编号：\n' +
            '1.存钱\n' +
            '2.取钱\n' +
            '3.显示余额\n' +
            '4.退出');
        var total = 100;
        while (num != '4') {
            switch (num) {
                case '1':
                    var add = parseFloat(prompt('请输入存款数：'));
                    total += add;
                    alert('存款成功！目前余额为' + total);
                    break;
                case '2':
                    var reduce = parseFloat(prompt('请输入取款数：'));
                    if (reduce <= total) {
                        total -= reduce;
                        alert('取款成功！目前余额为' + total);
                    }
                    else {
                        alert('余额不足！目前余额为' + total);
                    }
                    break;
                case '3':
                    alert('目前余额为' + total);
                    break;
                default:
                    alert('请输入正确编号！');
            }
            num = prompt('请输入你要的操作编号：\n' +
                '1.存钱\n' +
                '2.取钱\n' +
                '3.显示余额\n' +
                '4.退出');
        }
        alert('已退出！');
    </script>
</head>

<body>
</body>

</html>
```

## 数组

### 创建

```js
//用new创建
var arr = new Array();
//创建空数组
var arr = [];
//创建带初始值的数组
var arr = [1,2,3,4];
```

### 获取数组元素

```js
console.log(arr[0]);
```

遍历数组：

```js
var arr = ['red', 'blue', 'green'];
for (i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

### 添加数组元素

```js
//通过改变length
var arr = [1, 2, 3, 4];
console.log('length:' + arr.length);
arr.length = 7;
console.log(arr);
//[1, 2, 3, 4, empty × 3]
//修改索引号追加元素
arr[5] = 3;
arr[7] = 1;
console.log(arr);
//[1, 2, 3, 4, empty, 3, empty, 1]
```

筛选数组元素（大于10的）

```js
var arr = [2, 4, 7, 10, 23, 44, 2];
var arr1 = [];
// var num = 0;
for (var i = 0; i < arr.length; i++) {
    if (arr[i] > 10) {
        // arr1[num] = arr[i];
        // num++;
        arr1[arr1.length] = arr[i];
    }
}
console.log(arr1);
```

### 冒泡排序

动图演示：

![冒泡排序](https://www.runoob.com/wp-content/uploads/2019/03/bubbleSort.gif)

思路：

一共分两层：
外层是每一次遍历比较算一轮，一共比较数组长度-1轮（因为两两比较，可以看成最后一次比较可以一下子确定两个数）

内层是左右相互比较，左比右大则互换位置，外层每进行一轮，内层的比较个数-1，因为外层每一轮都会确定一个数的位置

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var arr = [3, 2, 5, 1, 4];
        var tmp = 0;
        for (var i = arr.length - 1; i > 0; i--) {
            for (var j = 0; j < i; j++) {
                if (arr[j] > arr[j + 1]) {
                    tmp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = tmp;
                }
            }
        }
        console.log(arr);
    </script>
</head>

<body>
</body>

</html>
```

## 函数

### 声明函数

```js
function 函数名(参数1,参数2,...){
    函数体
}
```

案例1：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        function getSum(num1, num2) {
            console.log(num1 + num2);
        }
        function getTotalSum(num1, num2) {
            var min = num1, max = num2, tmp = 0, sum = 0;
            if (num1 > num2) {
                tmp = min;
                min = max;
                max = tmp;
            }
            for (var i = min; i <= max; i++) {
                sum += i;
            }
            // return sum;
            console.log('sum:' + sum);
        }
        getSum(2, 4);//6
        getTotalSum(12, 5);//68
        //如果传参个数不对不会报错，只会结果显示不正确
        //多于形参的个数会只取形参个数的实参
        //少于形参的个数会将缺少的参数自动定义为undefined
    </script>
</head>

<body>
</body>

</html>
```

### return

- 返回值，只能返回一个值，如果有多个值返回，只取最后一个值
- return之后的代码不被执行
- 没有return，函数返回undefined

