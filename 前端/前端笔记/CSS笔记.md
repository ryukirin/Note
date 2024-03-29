# CSS笔记

CSS就是美化网页的。

CSS是层叠样式表（Cascading Style Sheets）的简称。

有时也称为CSS样式表或级联样式表。

也是一种标记语言。

## CSS简介

选择器+声明

```css
h1 {
    color: red;
    ...
}
```

选择器{属性：值}

### CSS代码风格

- 样式格式书写：展开格式，一个样式写一行。
- 样式大小写：小写。
- 空格规范：
  - 属性值前，冒号后边，保留一个空格。
  - 选择器和大括号间保留一个空格。

## CSS基础选择器

选择器就是选择标签用的

基础选择器就是由单个选择器组成的：

- 标签选择器：选择HTML标签名称作为选择器，会把所有该标签选中进行设置。

  ```css
  标签名 {
  	属性1: 属性值1;
      属性2: 属性值2;
      属性3: 属性值3;
      ...
  }
  ```

- 类选择器：可以单独选择一个或者几个标签，可以实现差异化设置。

  ```css
  .类名 {
  	属性1: 属性值1;
  	...
  }
  ```

  - 类选择器使用.进行标识，后边紧跟类名
  - 可以理解为给这个标签起了个名字
  - 长名称或词组可以使用中横线来为选择器命名
  - 不要使用纯数字或中文命名，尽量使用英文
  - 命名要有意义，让别人一眼知道是什么

  类选择器还有个特殊用法叫多类名

  ```html
  <div class="类名1 类名2">
      ...
  </div>
  ```

  可以把共同的样式和独有样式分开，节省代码并且方便修改

- id选择器

  ```css
  #id名 {
      属性1: 属性值1;
      ...
  }
  ```

  和类选择器最大区别就是只能调用一次

  在开发过程中通常用于页面唯一性元素上，和JavaScript搭配使用

- 通配符选择器：选择全部的标签

  ```css
  * {
      属性1: 属性值1;
      ...
  }
  ```

  不用调用，自动使用，特殊场景才用

| 基础选择器   | 作用                          | 特点                               | 使用情况         | 用法                          |
| ------------ | ----------------------------- | ---------------------------------- | ---------------- | ----------------------------- |
| 标签选择器   | 可以选出所有相同的标签，比如p | 不能差异化选择                     | 较多             | p {<br/>color: red;<br/>}     |
| 类选择器     | 可以选出1个或多个标签         | 可以根据需求选择                   | 非常多           | .nav {<br />color: red;<br/>} |
| id选择器     | 一次只能选择一个标签          | ID属性只能在每个HTML文档中出现一次 | 一般和JS搭配使用 | #nav {<br />color: red;<br/>} |
| 通配符选择器 | 选择所有的标签                | 选择的太多，有部分不需要           | 特殊情况使用     | * {<br />color: red;<br/>}    |

## CSS字体属性

### 字体系列

使用font-family定义文本的字体系列

```css
p {
    font-family: "微软雅黑";
}
div {
    font-family: Arial,"微软雅黑","Microsoft Yahei";
}
```

尽量使用系统默认字体，保证任何用户的浏览器中都能正常显示。

最常见的字体："Microsoft Yahei",tahoma,arial,"Hiragino Sans GB"

### 字体大小

font-size，必须加px。谷歌浏览器默认16px，但是不要默认，要指定大小。

标题标签比较特殊，需要单独指定大小

### 字体粗细

font-weight：

- normal：正常
- bold：加粗
- bolder：特粗
- lighter：细体
- number：使用数字控制粗细，不带单位，100-900，仅限整百，实际开发中更提倡。400相当于normal

### 文字样式

font-style：

- normal：默认值，标准字体样式
- italic：斜体

### 复合属性

```css
body {
    font: font-style font-weight font-size/line-height font-family;
}
```

不可以颠倒顺序，不需要的属性可以不设置（取默认值），但必须保留font-size和font-family属性，否则不起作用。

| 属性        | 表示     | 注意点                                                       |
| ----------- | -------- | ------------------------------------------------------------ |
| font-size   | 字号     | 我们通常用的单位是px像素，一定要有单位                       |
| font-family | 字体     | 实际工作中按团队约定设置                                     |
| font-weight | 字体粗细 | 加粗是700或bold，普通是normal或400，数字不跟单位             |
| font-style  | 字体样式 | 倾斜是italic，不倾斜是normal，工作中常用normal使倾斜变不倾斜 |
| font        | 字体连写 | 有顺序，不能换位置，字号字体必须保留                         |

## CSS文本属性

### 文本颜色

color

- 预定义的颜色值：red、blue之类的
- 十六进制：#FF0000之类的，开发最常用
- RGB代码：rbg(255,0,0)或rbg(100%,0%,0%)之类的

### 对齐属性

text-align

- left：左对齐，默认
- right：右对齐
- center：居中

### 装饰文本

text-decoration

- none：默认，啥也没有（最常用），可以把a（超链接）的默认下划线去掉。
- underline：下划线（常用）
- overline：上划线（几乎不用）
- line-through：删除线（不常用）

### 文本缩进

text-indent

- px：像素
- em：相对单位，当前元素（font-size）一个文字的大小，如果没有设置，就是父元素的一个文字大小。

### 行间距

line-height，行间距 = 上间距+文本高度+下间距

测量行高：从上一行的最低端量到这一行的最低端

| 属性            | 表示     | 注意点                                                |
| --------------- | -------- | ----------------------------------------------------- |
| color           | 文本颜色 | 常用16进制，并且是简写形式，如#FFF                    |
| text-align      | 文本对齐 | 设置对齐方式                                          |
| text-indent     | 文本缩进 | 首行缩进两字符：text-indent: 2em;                     |
| text-decoration | 文本装饰 | 重点是添加下划线：underline和取消下划线：none         |
| line-height     | 行高     | 控制行与行之间的距离，行间距 = 上间距+文本高度+下间距 |

 ## CSS的引入方式

三种样式表：

- 行内样式表（行内式）
- 内部样式表（嵌入式）
- 外部样式表（链接式）

### 内部样式表

```html
<style>
	css...
</style>
```

理论上可以放到HTML文档任何地方，但是一般会放在head标签中，可以控制整个页面的样式，结构样式分离了，没完全分离。

### 行内样式表

适合于修改简单样式

```html
<div style="color: red;">
    ...
</div>
```

可以控制当前的标签样式，不推荐大量使用

### 外部样式表

使用最多的，单独写到css文件中，再引用到html文件中。

- 先新建一个后缀名为.css的样式文件，将CSS代码全部放里
- 引入到html文件中

```html
<link rel="stylesheet" href="xxx.css">
```

- rel：指明当前文档和被链接文档的关系，此时指定为stylesheet
- href：被链接文档的路径，可以是绝对路径也可以是相对路径

| 样式表     | 优点               | 缺点         | 使用情况 | 控制范围 |
| ---------- | ------------------ | ------------ | -------- | -------- |
| 行内样式表 | 书写方便，权重高   | 结构样式混写 | 较少     | 一个标签 |
| 内部样式表 | 部分结构和样式分离 | 没有彻底分离 | 较多     | 一个页面 |
| 外部样式表 | 完全结构样式分离   | 需要引入     | 最多     | 多个页面 |

当设置有冲突时，style和link哪个在下（靠近body）哪个生效

## Emmet语法

### 快速生成HTML结构语法

- 生成标签，直接输入标签名+tab键

- 生成多个相同标签，用标签名+*+tab键

- 父子关系的标签，用>，例如：ul>li即可生成无序列表

- 兄弟关系的标签，用+

- 生成带有类名或id名的直接写#id或.class就行了，默认div，前边带上标签名可生成其他标签的，例如ul>li#two即为

  ```html
  <ul>
      <li id="two"></li>
  </ul>
  ```

- 如果生成的div是有顺序的，可以用自增符号\$ ，例：.demo\$*5即为：

  ```html
  <div class="demo1"></div>
  <div class="demo2"></div>
  <div class="demo3"></div>
  <div class="demo4"></div>
  <div class="demo5"></div>
  ```

- 如果想要在生成的标签内部些内容可以用{}表示，例如：div{test}*5即为：

  ```html
  <div>test</div>
  <div>test</div>
  <div>test</div>
  <div>test</div>
  <div>test</div>
  ```

### 快速生成CSS样式语法

简写形式即可

### 快速格式化代码

shitf+alt+f

## CSS的复合选择器

可以更准确高效的选择目标元素（标签）

- 后代选择器
- 子选择器
- 并集选择器
- 伪类选择器

### 后代选择器

又称包含选择器

可以选择父元素里的子元素

### 子选择器

只能选择作为某元素的最近一级子元素，简单来讲就是亲儿子

```css
div>p {
    ...
}
```

### 并集选择器

可以选择多组标签，同时定义样式

```css
div,
p {
    ...
}
```

### 伪类选择器

用于向某些选择器添加特殊效果，比如给链接添加特殊效果，或选择第1个或第n个元素。

特点：用冒号表示，比如:hover

种类有很多，比如链接伪类、结构伪类等

#### 链接伪类

```css
/*选择所有未被访问的链接*/
a:link
/*选择所有已被访问的链接*/
a:visited
/*选择鼠标指针位于其上的链接*/
a:hover
/*选择活动链接（鼠标按下未弹起的链接）*/
a:active
```

不要改顺序，按照LVHA的顺序来，否则可能会不生效。

链接在浏览器中有单独的默认样式，给body设置样式时不会对链接生效，所以一定要单独指定样式。

#### focus伪类

用于选取获得焦点（光标）的表单元素

一般是input类表单才能获取

```css
input:focus {
    background-color: yellow;
}
```

| 选择器          | 作用                       | 特征             | 使用情况 | 隔开符号/用法例                                              |
| --------------- | -------------------------- | ---------------- | -------- | ------------------------------------------------------------ |
| 后代选择器      | 选择后代元素               | 可以是子孙后代   | 较多     | 空格/div a                                                   |
| 子代选择器      | 选择最近一级元素（亲儿子） | 只能是亲儿子     | 较少     | 大于号/div>a                                                 |
| 并集选择器      | 选择某些标签相同的元素     | 可以用于集体声明 | 较多     | 逗号/div,a                                                   |
| 链接伪类选择器  | 选择不同状态的链接         | 跟链接有关       | 较多     | 开发过程中一般用a{}来控制普通状态下链接的样式，再用a:hover定义鼠标停留时的样式即可 |
| focus伪类选择器 | 选择获得光标的表单         | 跟表单有关       | 较少     | input:focus                                                  |

## CSS的元素显示模式

即元素以什么方式进行显示

一般分为块元素和行内元素

### 块元素

h1-h6、p、div、ul、ol、li等，其中div是最典型的块元素

- 自己独占一行
- 高度、宽度、外边距和内边距都可以控制
- 宽度默认是容器（父级宽度）的100%
- 是一个容器及盒子，里边可以放行内或者块级元素。

注意：

- 文字类元素不能放块级元素
- p、h1-h6等都是文字类元素

### 行内元素

也叫内联元素

常见的有a、strong、b、em、i、del、s、ins、u、span等

其中span最为典型

- 高宽设置无效

- 行内元素只能容纳文本或其他行内元素

- a里不能再放a
- 特殊情况a里可以放块级元素，但是最好给a转换一下块级模式

### 行内块元素

img、input、td等，具有块元素和行元素的特点，有些资料称之为行内块元素。

- 在一行上，但是会有缝隙，一行内可以有多个（行内元素特点）
- 默认宽度就是本身内容的宽度（行内元素特点）
- 高度、行高、内外边距都可以控制（块级元素特点）

| 元素模式   | 元素排列             | 设置样式           | 默认宽度       | 包含                   |
| ---------- | -------------------- | ------------------ | -------------- | ---------------------- |
| 块级元素   | 一个占一行           | 可以设置宽度高度   | 容器的100%     | 可以包含任何标签       |
| 行内元素   | 一行可以放多个       | 不可以设置宽度高度 | 本身内容的宽度 | 容纳文本或其他行内元素 |
| 行内块元素 | 一行放多个行内块元素 | 可以设置宽度高度   | 本身内容的宽度 |                        |

### 元素显示模式转换

特殊情况下，需要元素模式的转换，即一种模式的元素需要另外一种模式的特性。

比如想要增加链接a的触发范围

- 转化为块级元素：display:block;
- 转化为行内元素：display:inline;
- 转化为行内块元素：display:inline-block;

### 设置垂直居中

单行文字可以通过行高=盒子高度设置

比如div中的文字可以设置line-height的数值 = height的数值来实现

## CSS的背景

### 背景颜色

background-color:transparent|color;

透明（默认）和颜色

### 背景图片

非常便于控制位置

background-image:none|url();

### 背景平铺

background-repeat:repeat|no-repeat|repeat-x|repeat-y;

平铺|不平铺|横着铺|竖着铺

### 背景图片位置

background-position:x y;

x和y可以是：

- 精确单位：百分数、长度值，第一个肯定是X第二个肯定是Y
- 方位名词：top/center/bottom/left/right，此时前后顺序无所谓，如果第二个参数省略，默认居中
- 混合单位，可以一个是精确，一个是方位，顺序一定是先X后Y

### 背景图像固定（背景附着）

background-attachment:fixed|scroll;

固定|滚动

### 复合写法

background:颜色 图片 平铺 滚动 位置

没有固定顺序，只是常用顺序

### 背景色半透明

background: rgba(0,0,0,0);

最后一个是透明度的意思0-1之间，1是不透明，0是完全透明

内容透明度无影响

| 属性                  | 作用           | 值                                                           |
| --------------------- | -------------- | ------------------------------------------------------------ |
| background-color      | 背景颜色       | 预定义的颜色值/16进制/RGB                                    |
| background-image      | 背景图片       | url(路径)                                                    |
| background-repeat     | 是否平铺repeat | repeat\|no-repeat\|repeat-x\|repeat-y                        |
| background-position   | 背景位置       | x y，可以是精确长度或者方位名词                              |
| background-attachment | 背景附着       | scroll\|fixed                                                |
| 背景简写              | 书写更简单     | 颜色 图片 平铺 滚动 位置                                     |
| 背景色半透明          | 背景颜色半透明 | rgba(0,0,0,0)最后一个是透明度的意思0-1之间，1是不透明，0是完全透明 |

## CSS三大特性

层叠性、继承性、优先级

### 层叠性

给相同选择器设置相同样式，会触发层叠性原则：

- 样式冲突就近原则，离结构近的执行，若为引入文件就是在下方的定义
- 样式不冲突，不会层叠

### 继承性

子标签会继承父标签的某些样式，可以简化代码。

可以继承的有text-/font-/line-/color等

#### 行高的继承

可以跟单位也可以不跟，不跟就是当前子元素的字体大小的多少倍

不跟单位的最大好处就是可以让子元素根据自己的文字大小自动去调整

### 优先级

当一个元素指定多个选择器则：

- 选择器相同，执行层叠性
- 选择器不同，则根据选择器权重执行

权重如下：

| 选择器               | 选择器权重（不会改变，不会进位，只会同位相加，比较从左往右比较） |
| -------------------- | ------------------------------------------------------------ |
| 继承或者*            | 0,0,0,0                                                      |
| 元素选择器           | 0,0,0,1                                                      |
| 类选择器，伪类选择器 | 0,0,1,0                                                      |
| ID选择器             | 0,1,0,0                                                      |
| 行内样式 style=""    | 1,0,0,0                                                      |
| !important 重要的    | =无穷大                                                      |

链接浏览器默认制定了一个样式：蓝色，有下划线，故继承过来的text-decoration和color全都无效

#### 权重的叠加

如果是复合选择器，则会有权重叠加，需要计算权重

权重不会改变，不会进位，只会同位相加，比较从左往右比较

注：

a:hover的权重为0,0,1,1不是0,0,1,0因为前边有个标签选择器

例子：[hover失效的一个和权重有关的原因](https://blog.csdn.net/weixin_46102597/article/details/104228185) 

## 盒子模型

网页布局过程：

- 选准备好相关的网页元素，网页元素基本都是盒子Box
- CSS设置好盒子样式，然后摆放到相应位置
- 往盒子里装内容

网页布局核心本质：用盒子摆布局

### 组成部分

盒子模型就是把HTML页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器

CSS盒子模型本质是一个盒子，封装周围的HTML元素，包括边框、外边距、内边距和实际内容

- border边框
- content内容
- padding内边距：边框和内容的距离
- margin外边距：盒子之间的距离

#### 边框(border)

边框宽度（粗细）、边框样式以及边框颜色

```css
border : border-widtn || border-style || border-color
```

border 边框 样式 颜色 没有顺序

```css
border-top: 1px solid red;
border-bottom: 5px solid red;
border-left: 5px solid yellow;
border-right: 5px solid purple;
```

表格的细线边框

```css
 /* 合并相邻的边框 */
 border-collapse: collapse;
```

- 边框会影响到盒子的实际大小，如200 * 200px的盒子加上10px的边框实际大小为220 * 220px

#### 内边距(padding)

| 值的个数                     | 意思                              |
| ---------------------------- | --------------------------------- |
| padding: 5px;                | 上下左右均为5px                   |
| padding: 5px 10px;           | 上下5px 左右10px                  |
| padding: 5px 10px 20px;      | 上5px 左右10px 下20px             |
| padding: 5px 10px 20px 30px; | 上5px 右10px 下20px 左30px 顺时针 |

- 内边距也会影响到盒子的实际大小，如200 * 200px的盒子加上10px的内边距实际大小为220 * 220px

- 如果不指定weight值，则不会改变盒子宽度

  ```css
  h1 {
      /*此时h1没有设置宽度
      所以长度默认为body的长度
      padding只会改变高度不会改变宽度*/
      height: 40px;
      padding: 30px;
  }
  h2 {
      /*对比：
      此时h2设置了宽度
      padding会改变宽度*/
      height: 40px;
      padding: 30px;
      width: 1000px;
  }
  ```

#### 外边距(margin)

| 值的个数                    | 意思                              |
| --------------------------- | --------------------------------- |
| margin: 5px;                | 上下左右均为5px                   |
| margin: 5px 10px;           | 上下5px 左右10px                  |
| margin: 5px 10px 20px;      | 上5px 左右10px 下20px             |
| margin: 5px 10px 20px 30px; | 上5px 右10px 下20px 左30px 顺时针 |

与padding完全一致

使用margin让块级盒子水平居中：

- 盒子必须指定了宽度
- 左右外边距都设置为auto
- 行内元素或行内块元素使用给父元素添加text-align:center即可

#### 外边距合并（外边距塌陷）

- 相邻块元素垂直外边距的合并：当上下相邻的两个块元素（兄弟关系）相遇时，如果上边的元素有margin-bottom，下边的元素有margin-top，则它们之间的垂直间距取两个值中较大者。

- 嵌套块元素垂直外边距的塌陷：对于两个嵌套关系（父子关系）的块元素，若父元素有margin-top的同时子元素也有margin-top，则此时父元素的margin-top取两个值较大的，并且子元素不会与父元素有上边距。注：这种情况只出现在父元素下第一个子元素中。

  如何解决：

  - 可以为父元素定义上边框
  - 可以为父元素定义上内边框
  - 可以为父元素添加overflow:hidden

#### 清除内外边距

很多网页元素都有默认的内外边距，且不同浏览器下不一样，因此布局前需要清除网页元素的内外边距

```css
* {
    padding: 0;
    margin: 0;
}
```

行内元素尽量只设置左右的内外边距，因为行内元素的上下边距设置不会生效。若真的需要上下边距，display: block; 或者 display: inline-block;

### 圆角边框

```css
border-radius:length;
```

length是与矩形角相切的圆的半径，可以是数值或者百分比（百分比的话大多为椭圆与矩形角相切，半长轴和半短轴为长和宽的x%，当盒子是正方形时，为圆）

- 如果是正方形，length=高度的一半或者50%，可以画圆
- 如果是矩形，length=高度一半可以设置为两个半圆+矩形
- 该属性是简写，可以跟四个值，左上右上右下左下，分开是border-top-left-radius、border-top-left-radius、border-top-right-radius、border-bottom-right-radius、border-bottom-left-radius

### 盒子阴影

```css
box-shadow: h-shadow v-shadow blur spread color inset;
```

| 值       | 描述                                             |
| -------- | ------------------------------------------------ |
| h-shadow | 必填，水平阴影的位置，正值阴影在右方，负值在左方 |
| v-shadow | 必填，垂直阴影的位置，正值阴影在下方，负值在上方 |
| blur     | 可选，模糊距离                                   |
| spread   | 可选，阴影的尺寸                                 |
| color    | 可选，阴影的颜色                                 |
| inset    | 可选，将外部阴影（outset）改为内部阴影           |

阴影不占空间，不影响排列

### 文字阴影

```css
text-shadow: h-shadow v-shadow blur color;
```

| 值       | 描述                                             |
| -------- | ------------------------------------------------ |
| h-shadow | 必填，水平阴影的位置，正值阴影在右方，负值在左方 |
| v-shadow | 必填，垂直阴影的位置，正值阴影在下方，负值在上方 |
| blur     | 可选，模糊距离                                   |
| color    | 可选，阴影的颜色                                 |

## CSS浮动

### 浮动

#### 传统网页布局的三种方式

网页布局的本质——用css来摆放盒子，把盒子摆放到相应位置

- 普通流（标准流）

- 浮动
- 定位

一般的网页包括了全部三种布局方式

浮动可以改变默认的排列方式

最典型的应用：让多个块级元素在一行内排列显示且无缝隙

**多个块级元素纵向排列选标准流，横向排列选浮动**

#### 普通流（标准流/文档流）

按标签默认的方式排列

- 块级元素独占一行，自上而下排列

- 行内元素自左至右排列，在父元素边缘自动换行

#### 浮动

float用于创建浮动窗，将其移动到一边，直到左边缘或右边缘及包含块或另一个浮动框的边缘

```css
选择器 {
    float: 属性;
}
```

| 属性值 | 描述               |
| ------ | ------------------ |
| none   | 元素不浮动（默认） |
| left   | 向左浮动           |
| right  | 向右浮动           |

#### 浮动的特性

- 浮动元素会脱离标准流（脱标），浮动的盒子不再保留原先的位置，即会跑到上一图层，遮挡下一个标准流盒子
- 浮动的元素会一行内显示并且元素顶部对齐，如果父级元素装不下，才会另起一行
- 浮动的元素会具有行内块元素的特性

为了约束浮动元素的位置，网页布局一般采取：

- 使用标准流父元素排列上下位置，内部子元素采取浮动排列左右位置

- 先设置盒子大小，再设置盒子位置

### 常见的网页布局

![image-20220105175506707](D:\资料\资料\前端学习\图片\image-20220105175506707.png)

![image-20220105175548877](D:\资料\资料\前端学习\图片\image-20220105175548877.png)

#### 浮动布局的注意点

- 浮动和标准流的父盒子搭配

  先用标准流的父元素排列上下位置，之后内部子元素采用浮动排列左右位置

- 一个元素浮动，理论上其余兄弟元素也要浮动，浮动的盒子只会影响后边的标准流。例：

  当ABC三个div均为标准流时，三个div竖排列。当A为浮动，B为标准流，C为浮动时，B会被A遮挡，C仍然在B的下方竖排列。

### 清除浮动

由于父级盒子很多情况下不方便给高度，但是子盒子浮动不占有位置，所以当父盒子没有设置高度，子盒子设置浮动时，下边的标准流盒子会被当前子盒子覆盖部分。所以我们需要清除浮动。

清除浮动本质就是清除浮动元素造成的影响

```css
选择器 {
    clear: 属性值;
}
```

| 属性值 | 描述                                               |
| ------ | -------------------------------------------------- |
| left   | 不允许左侧有浮动元素（清除左侧浮动的影响）         |
| right  | 不允许左侧有浮动元素（清除左右侧浮动的影响）       |
| both   | 同时清除左右两侧浮动的影响（最常用，基本只用这个） |

清除浮动的策略：闭合浮动

- 额外标签法/隔墙法
- 父级添加overflow属性
- 父级添加after伪元素
- 父级添加双伪元素

#### 额外标签法

在浮动元素末尾添加一个空的标签，例如

```html
<div style="clear:both"></div>
或
<br />
```

例

```html
<style>
    .clear {
        clear: both;
    }
</style>
<!-- 在body中添加空标签
其余class详细样式省略了 -->
<body>
    <div class="box">
        <div class="one"></div>
        <div class="two"></div>
        <!-- 新添加的标签必须是块级元素或者br -->
        <div class="clear"></div>
    </div>
    <div class="footer"></div>
</body>
```

- 优点：通俗易懂，书写方便
- 缺点：添加许多无意义的标签，结构化较差

#### 父级添加overflow属性

```css
选择器 {
    overflow: hidden/auto/scroll;
}
```

- 优点：代码简洁
- 缺点：无法显示溢出部分

#### 父级添加after伪元素

是额外标签法的升级版

```html
<style>
    .clearfix::after {
            content: "";
            display: block;
            height: 0;
            clear: both;
            visibility: hidden;
        }

        .clearfix {
            /* IE6、7专有 */
            *zoom: 1;
        }
</style>

父元素原本的class为box，现在应该写成：

<div class="box clearfix">
    子元素
</div>
```

- 优点：没有额外增加标签，结构更简单
- 缺点：需要照顾低版本浏览器

#### 父级添加双伪元素

```html
<style>
        .clearfix::before,
        .clearfix::after {
            content: "";
            display: table;
        }

        .clearfix::after {
            clear: both;
        }

        .clearfix {
            /* IE6、7专有 */
            *zoom: 1;
        }
</style>

父元素原本的class为box，现在应该写成：

<div class="box clearfix">
    子元素
</div>
```

- 优点：代码更简洁
- 缺点：需要照顾低版本浏览器

## PS 切图

### 常见的图片格式

- jpg：对色彩的信息保留较好，高清，颜色较多，产品类图片常用
- gif：最多只能存256色， 通常用来显示简单图形或字体，但是可以保存透明背景和动画效果，常用于一些图片小动画效果
- png：结合了gif和jpg的优点，存储形式丰富，能够保持透明背景
- PSD：PS专有格式，可以存放图层、通道、遮罩等多种设计稿，可以从中直接复制文字、获得图片以及测量大小和距离

### 切图方式

- 图层切图：

  选中图层->右键“快速导出为PNG”

  若是需要多个图层一起导出（比如图上有文字但是分了图层的情况）

  选中两个图层ctrl+E合并图层再导出

- 切片切图：

  利用切片工具（在左侧工具栏中）手动划出图片->文件->存储为web设备所用格式->选择我们要的图片格式（JPEG）->存储->切片：选中的切片->保存

  - 若想导出透明背景，在右侧图层框拉到最低端将背景不可视（显示框中显示为灰色方格），再进行切片，保存为png格式

  - 若不想要切片了，单击切片按delete键

  - 若想移动切片（这里指的是切片框而不是切片中的内容），切片选择工具->点击切片->按着鼠标左键或者键盘方向键移动

- PS插件切图：

  Cutterman插件，需要ps是完整版，而不是绿色版

## 案例：学成在线网页

### CSS属性书写顺序

- 布局定位属性：display / position / float / clear / visibility / overflow（建议display第一个写，毕竟关系到模式）
- 自身属性：widtn / height / margin / padding / border / background
- 文本属性：color / font / text-align / verical-align / white-space / break-word
- 其他属性（CSS3）：content / cursor / border-radius / box-shadow / background:linear-gradient

### 页面布局整体思路

- 必须确认页面的版心（可视区），一般是给定宽度的居中对齐的盒子，宽度我们测量可得知
- 分析页面中的行模块，以及每个行模块中的列模块
- 一行中的列模块经常浮动布局，先确定每个列的大小，之后确定列的位置
- 制作HTML结构，我们还是遵循，先有结构，后有样式的原则
- 先理清楚布局结构，再写代码

### 头部制作

#### 导航栏

实际开发中，不会直接使用 a 而是用 li>a 制作

- 这样做语义更清晰
- 如果直接用a会比较容易被识别为堆砌关键字，可能会被搜索引擎降权，从而影响网站排名

这个导航栏可以不加宽度，方便以后继续添加文字

导航栏每块文字不一样多，最好给 a 左右加padding撑开盒子，而不是指定宽度

## CSS定位

### 为什么需要定位

以下情况标准流实现不了：

- 某个元素可以自由地在一个盒子内移动位置，并且压住其他盒子
- 当我们滚动窗口时，盒子固定在屏幕上（浮窗）

所以需要定位来实现。

- 浮动可以让多个块级盒子没有缝隙排列显示，常用于横向排列盒子
- 定位则是可以让盒子自由的在某个盒子内移动位置或者固定屏幕中某个位置，并且可以压住其他盒子

定位也是在摆盒子，按照定位的方式移动盒子

### 定位组成

定位 = 定位模式 + 边偏离

#### 定位模式

通过 CSS 的 position 属性来设置，其值可以分为四个：

| 值       | 语义     |
| -------- | -------- |
| static   | 静态定位 |
| relative | 相对定位 |
| absolute | 绝对定位 |
| fixed    | 固定定位 |

#### 边偏移

就是定位的盒子移动到最终位置，有top/bottom/left/right四个属性

| 边偏移属性 | 举例          | 描述                                           |
| ---------- | ------------- | ---------------------------------------------- |
| top        | top: 80px;    | 顶端偏移量，定义元素相对于其父元素上边线的距离 |
| bottom     | bottom: 80px; | 底部偏移量，定义元素相对于其父元素下边线的距离 |
| left       | left: 80px;   | 左侧偏移量，定义元素相对于其父元素左边线的距离 |
| right      | right: 80px;  | 左侧偏移量，定义元素相对于其父元素右边线的距离 |

#### 静态定位 static

默认的定位方式，无定位的意思

```css
选择器 {
    position: static;
}
```

按照标准流摆放，没有边偏移

很少用到

#### 相对定位 relative

元素在移动位置时，是相对于其原来位置来讲的

```css
选择器 {
    position: relative;
}
```

原来在标准流的位置继续占有，不影响后边的盒子（如果原先两个盒子紧贴着上下排列，且移动的盒子为上边的盒子，往下移动，，下方的盒子不会动，则会遮挡下方的盒子）

#### 绝对定位 absolute

绝对定位：元素在移动的时候，是相对于它的祖先元素来说的

```css
选择器 {
    position: absolute;
}
```

- 如果没有祖先元素或者祖先元素没有定位，则以浏览器为准定位
- 如果祖先元素有定位，则以最近一级的有定位的祖先元素为参考点移动位置
- 绝对定位不再占有原先位置（脱标）

#### 子绝父相

子级是绝对定位的话，父级要用相对定位（大多数情况）

- 子级绝对定位，不占有位置，可以放到父元素里任意一个地方，不会影响其他兄弟盒子
- 父级盒子需要加定位限制子盒子在父盒子内显示
- 父盒子布局时，需要占有位置，所以只能是相对定位

#### 固定定位 fixed

固定定位是元素固定于浏览器可视区的位置。主要用于浏览器页面滚动元素位置不会改变的场景。（浮窗）

```css
选择器 {
    position: fixed;
}
```

- 以浏览器的可视窗口为参照点移动元素
- 不占有原有位置

也可以看成特殊的绝对定位

##### tips：固定在版心右侧位置

- 让固定定位的盒子left: 50%; 走到浏览器可视区（也可看作版心）的一半
- 让固定定位的盒子margin-left: 版心宽度一半的距离，多走版心宽度的一半位置

例：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .page {
            height: 1000px;
            width: 1200px;
            margin: auto;
            background-color: bisque;
        }

        .fixed {
            position: fixed;
            top: 200px;
            left: 50%;
            margin-left: 600px;
            width: 100px;
            height: 100px;
            background-color: cornflowerblue;
        }
    </style>
</head>

<body>
    <div class="page">
        <div class="fixed">fixed</div>
    </div>
</body>

</html>
```

效果图：

![image-20220114194033691](D:\资料\资料\前端学习\图片\image-20220114194033691.png)

#### 粘性定位 sticky

是相对定位和固定定位的结合，效果为页面滚动时元素先滚动到一定位置之后固定

```css
选择器 {
    position: sticky;
    top: 10px;
}
```

- 以浏览器的可视窗口为参照点移动元素（固定定位特点）
- 占有原先位置（相对定位特点）

- 必须添加top/left/right/bottom其中一个才有效（指之后固定在哪里）

不常用，因为兼容性较差，通常这种效果用js实现

#### 定位总结

| 定位模式 | 是否脱标 | 移动位置           | 是否常用   |
| -------- | -------- | ------------------ | ---------- |
| 静态定位 | 否       | 不能使用边偏移     | 很少       |
| 相对定位 | 否       | 相对于自身位置移动 | 常用       |
| 绝对定位 | 是       | 带有定位的父级元素 | 常用       |
| 固定定位 | 是       | 浏览器可视区       | 常用       |
| 粘性定位 | 否       | 浏览器可视区       | 现阶段很少 |

#### 定位叠放次序 z-index

在盒子重叠时，z-index 控制z轴（图层）的先后顺序

```css
选择器 {
    z-index: 1;
}
```

- 数值可以是正整数、负值或者0，默认是auto，数值越大，盒子越靠上
- 如果属性值相同，则按照书写顺序后来者居上
- z-index不能加单位
- 只有有定位的盒子才有z-index属性

#### 定位的拓展

##### 绝对定位的盒子居中

```css
position: absolute;
/* 水平居中 */
left: 50%;
margin-left: -width的一半
/* 垂直居中 */
top: 50%;
margin-top: -height的一半
```

##### 定位的特殊特性

绝对定位和固定定位也和浮动类似

- 行内元素加绝对定位或者固定定位，可以直接设置高度和宽度
- 块级元素添加绝对或者固定定位，如果不给宽高，默认大小是内容的大小

##### 脱标的盒子不会触发外边距塌陷

绝对定位和固定定位不会触发外边距塌陷

##### 定位会压住标准流文字

浮动元素不会，只会压住盒子不会压住文字和图片

## 网页布局总结

- 标准流

  可以让盒子上下排列或者左右排列，垂直的块级盒子显示就用标准流布局。

- 浮动

  可以让多个块级元素一行显示或者左右对齐盒子，多个块级盒子水平显示就用浮动布局。

- 定位

  最大特点就是有层叠的概念，可以让多个盒子前后叠压来显示，如果元素自由在某个盒子内移动就用定位布局。

## 元素的显示与隐藏

- display显示隐藏
- visibility显示隐藏
- overflow溢出显示隐藏

### display显示隐藏

- display: none; 隐藏对象，位置不保留
- display: block; 显示元素（也有转化为块级元素的意思）

很常用

### visibility显示隐藏

- visibility: hidden; 隐藏，位置保留
- visibility: visible; 显示

### overflow溢出显示隐藏

- overflow: visible; 显示溢出部分（默认）
- overflow: hidden; 不显示溢出部分
- overflow: scroll; 带滚动条显示溢出部分，不溢出时也显示滚动条
- overflow: auto; 不溢出时不显示滚动条，溢出时显示滚动条

如果有定位的盒子慎用，因为会隐藏多余部分（定位到盒子外边显示的部分）
