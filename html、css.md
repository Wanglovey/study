# HTML

## 基础知识

### HTML

HTML即超文本标记语言。它是一种标记语言，而非编程语言，不能使用逻辑运算。	HTML通过标签将网络上的文档格式进行统一，使分散网络资源链接为一个逻辑整体，即HTML使用标签来描述网页内容

### 超文本

超文本是一种组织信息的方法，通过超级链接将多种媒介关联起来

### 静态网页

静态网页即代码写完后页面内容不会再发生任何改变的网页

注意：幻灯片效果、文字滚动效果等动画也属于静态网页

### 动态网页

动态网页即页面代码没有变，但显示的内容可以随着时间、环境或者数据库操作的结果而发生改变的网页

### 标签（标记）

标记即标签，是用<>包裹的具有一定含义的内容

标记语言就是一套标记标签

### 块级元素和行级元素

#### 块级元素

块级元素在浏览器中会单独占一行，宽度自动填满其父元素宽度，块级元素可以设置width，height属性

#### 行内元素

行内元素在浏览器中不会单独占一行，相邻的行内元素会排列在同一行，直到一行排不下才会换行

行内元素的宽度随元素的内容而变化，对行内元素设置width和height无效

行内元素一般用在网站内容之中的某些细节或部位，用以强调，如`<strong>标签`等

### W3C标准

万维网联盟（W3C）标准不是某一个标准，而是一系列标准的集合

W3C标准规定了网页主要由三部分组成：

- 结构（Structure）

- 表现（Presentation）

- 行为（Behavior）。

> 结构即HTML，表现即CSS，行为即JavaScript
>

### HTML5

#### 什么是HTML5

HTML5由W3C和WHAT组织机构共同研发出来的，于2014年正式发布，是新一代网页开发标准。

#### HTML5的特性

- 简易性
- 可拓展性
- 平台无关性
- 通用性

#### HTML5新功能

- 增加了audio和video音频播放，抛弃了Flash


- 新增了canvas画布（绘画，制作动画（如小游戏开发等））


- 地理定位

- 增加了离线缓存


- 硬件加速


- Web Socket（全双工通信）


- 增加了本地存储


- 新增了一些语义化标签


### 浏览器及其内核

#### 五大主流浏览器

- IE（edge）

- Firefox
- Chrome
- Opera
- safari

#### 浏览器内核的组成

浏览器内核由渲染引擎和JS引擎两部分组成

#### 五大浏览器内核

- Trident内核
  - 代表产品为IE，又称IE内核


- Gecko内核

  - 代表产品为Firefox，Gecko为开源内核，但其使用人数较少，启动速度较慢


- webKit内核

  - 主要用于Mac OS，代表产品为Safari、2013年前的Chrome、iPhone/ipad
  - 是安卓4.4版本及之前所采用的的内核
- Presto内核
  - 代表产品为OperaPresto，13年后被Opera弃用


- Blink内核

  - 2013年发布，现在Chrome和Opera内核都是Blink
  - 安卓4.4之后使用该内核

> 注：国内大多数浏览器采用双核驱动
>

### 几种常用开发工具

#### Dcloud HBuilder

拥有完整的语法提示和代码输入法，编写代码速度更加快捷，默认添加emmet语法插件。轻量级开发软件，无需安装

#### Sublime Text 3

轻量级软件，功能强大，可以写很多文件，还可跨平台使用

#### VS code

轻量级软件，功能强大

#### webstorm

重量级软件，HTML5编辑工具，支持代码格式化，推荐前端工程师使用，占用内存和CPU高

#### notepad++

轻量级软件

### SEO

#### 什么是SEO

SEO(Search Engine Optimization)即搜索引擎优化

#### SEO的作用

我们可以根据SEO规则优化自己的网站，让自己的网站在搜索引擎中的排名更靠前

#### 提升SEO的常见方法

1.竞价排名（最有用）

2.将网页制作成html后缀

3.标签语义化

4.......

#### SEO三大标签

SEO三大标签即对SEO最有用的三种标签

1. title              网页标题标签

2. description 网页描述标签

3. keywords    网页关键词标签

 

### 标签

#### 标签的组成

标签由标签名、标签属性和文本内容三部分组成

> 注意：单标签没有文本内容

#### 基本标签

```html
<div>、<hx>、<p>、<br />、<hr />、<a>、<img>、<span>、<ul>、<il>
```


#### 标签属性

标签属性是对标签的一种描述方式，标签属性分通用属性、自有属性和自定义属性。

##### 通用属性

通用属性是所有标签都具有的属性（除`<br/>`和`<hr/>`标签外）

通用属性有：

- id
  - 用来给标签取一个唯一的名称。id名称在一个网页必须是唯一的。

- class
  - 用来给标签取一个类名。

- style
  - 用来设置该标签的行内样式。

- title
  - 当鼠标移到该标签，所显示的提示内容。

##### 自有属性

自有属性是每个标签自己拥有的特殊属性

##### 自定义属性

自定义属性是用户自定义的标签属性，该属性通常用来传值或用于图片懒加载等

格式：`data-*`

- 获取自定义属性的方式

1. 兼容性获取


```javascript
dom.getAttribute("自定义属性名")
```

2. H5新增

```
dom.dataset.* 或 dom.dataset[‘*’]
```

- 自定义属性样例


```html
<img data-src="图片名" alt="提示文本"/>
```

> data-src为自定义属性

## 表格

### 表格标签

```html
caption	标题
thead	表头
tbody	表体
tfoot	表尾
tr	行
th	标题列
td	普通列
```

### 表格属性

> 表格属性大部分可由css代替，因此下方仅介绍目前较常用的表格属性

```html
width	表格宽度，默认单位是像素
align	表格对齐方式(left(默认)/center/right)
cellpadding	单元格文本与边框的距离
cellspacing	单元格边框间距
rowspan=跨行数跨行
colspan=跨列数跨列
```

>  注意：margin属性对表格的css或者`display:table-cell`修饰的标签无效
>

### 表格格式

```
<table>
    <caption>表格名称</caption>
    <thead>
        <tr>
            <th>名称</th>
            <th>年龄</th>
            ...
        </tr>
    </thead>
    <tbody>
    ...
    </tbody>
    <tfoot>
    ...
    </tfoot>
</table>
```

## form表单

### form表单标签

form表单标签是所有标签最核心标签之一。它是用来实现前后端交互的一个重要标签。

- form标签的常用属性


```
name	表单名称
action	表单数据提交的地方。值为#、后台文件名或URL。若为#，则表示提交到当前文件下
method	前端提交数据到后端的方法，值为get/post，get为默认值
```

### 表单属性

```
formaction	修改action数据提交的地方
formenctype	修改表单请求的类型
formmethod	修改数据提交的方法
form	设置表单元素属于哪个表单
novalidate	不验证
```

> 上方的属性为表单元素的属性，而非form标签的属性

### 表单元素的分类

#### input类

input类主要用来输入，选择或发出指令，type属性是其关键属性

##### input类的常用属性

```html
placeholder	提示
name	专有名称，必填项，且在同一个表单中必须唯一存在
minlength	最少输入的字符个数
maxlength	最多输入的字符个数
disabled	使input失效
readonly	是input为只读属性
value	保存input标签的值，也可以利用此属性为input标签设置默认值

以下属性为HTML5新增属性
autocomplete	表单的默认填充行为（html5新属性）
可选值：on/off	启用/禁用自动完成行为，默认状态为启用
autofocus	自动获焦
step	步长
multiple	多选
pattern	正则匹配，我也不会用
required	标记此选项必须输入，不能为空
```

##### type属性常用值

- text
  - 表示单行文本输入框，该值为默认值。

-  password	

  - 密码输入框


- radio

  - 单选按钮，通常为两个input及以上配合使用，并且需要使用name属性才能实现单选功能。

  - 样例


  - ```
    <input type="radio" name="sex" value="男"/>男
    <input type="radio" name="sex" value="女"/>女
    ```

- checkbox

  - 复选框，可以用来选择0项、1项或多项。


  - 自有属性：`checked	默认选中`


  - 样例


  - ```
    <input type="checkbox" name="sex" value="男">男
    <input type="checkbox" name="sex" value="女">女
    <input type="checkbox" name="sex" value="未知">未知
    ```

- file

  - 文件上传按钮


  - 自有属性：`multiple	多选文件`


- button	

  - 普通按钮


- image

  - 图片提交按钮，与submit功能，能够提交表单


  - 自有属性 `src 用来加载提示图片`


- submit

  - 提交按钮，用来将表单数据提交到后台。


- reset

  - 重置按钮，将表单所有组件输入的内容全部清空，还原为初始状态。

以下为HTML5新增的type属性

```
color	拾色器
email	输入邮箱
tel	输入电话号码
url	输入网址
number	数字
range	范围
search	搜索
date	选择日期
datetime	选择日期时间
datetime-local	本地日期时间
year	选择年份
month	选择月份
time	选择时间
```

#### textarea

textarea也叫文本域（或者称为多行文本框），用于输入大批量的文本内容

- 常用属性


```html
name	名称
cols	文本域列数
rows	文本域行数
placeholder	文本域的提示信息
minlength	最小长度
maxlength	最大长度
required	表示必须输入此项
value	文本域中的值
```

#### select

下拉列表框，默认用于单项选择。用option呈现每个选项。

- 常用属性


```html
multiple	表示此select类可以多选，这时的下拉列表框变成了列表框
size	最多同时显示的选项数
```

- 样例


```html
<select name="num">
  <option value="1">1</option>
  <option value="2">2</option>
  <option value="3">3</option>
</select>
```

#### button

普通按钮，具有提交功能

button可以单独使用，不一定要写在form元素中，但如果写在了form中，则该按钮具有提交功能

## 列表

#### 什么是列表

不是描述性的文本的任何内容都可以认为是列表。比如：菜单、商品列表等。

#### 列表类型

列表具有三种类型

- 无序(ul)
- 有序(ol)
- 自定义列表(dl)。

ul和ol的列表项都是用li表示的，而dl是由一个dt和一个或多个dd组成的。

dl一般用来设定一个定义，比如名词解释等。

dt（标题）和dd（描述）是用来对dt的内容进行解释并说明的

## iframe框架集

iframe即框架集，可以用来将多个网页文件组合成一个文件

常用属性：

```
name	框架名
src	引入的外部html文件
scrolling	滚动条(yes/no/auto)
width	宽度(%/px)
height	高度(%/px)
frameborder	是否有边框(1/0)
marginheight	框架离顶部和底端的距离(%/px)
marginwidth	框架离左右的距离(%/px)
```

> 注意：在实际开发，尽量减少`iframe`的使用，因为它破坏了前进和后退功能，且不利于`SEO`
>

## 文本格式化标签

文本格式化标签是用来美化文本的一类

```html
<b>	粗体字
<strong>	粗体字，与b不同之处仅在于strong表示强调，主要用于SEO引擎优化时提取关键字
<i>	斜体字
<em>	斜体字，同时也表示强调，强调作用见上
<pre>	定义预格式化的文本，被包含在pre标签元素中的文本会保留空格和换行符，文本也会呈现为等宽字体
<small>	小型文本
<sub>	定义下标文本
<sup>	定义上标文本
```

## 转义字符

```
&lt	小于号
&gt	大于号
&amp	&号
&nbsp	空格
&copy	版权符号 
&times	乘号（叉号）
&divide	除号
```

## 网页布局标签

```html
header	页首
nav	导航栏
aside	侧边栏
main	主体
section	区块
article	文章
footer	页尾
```

## 语义化标签

> 下方的语义化标签为HTML5新增标签

```html
mark	高亮显示(行级)
details	描述标签，一般用于名词解释或用于封装一个区块等
summary	摘要标签，需要在details标签中才能使用
meter	能够度量给定范围内的数据比例，类似进度条，但不应作为进度条使用
属性：value/min/max
progress	进度条标签
属性：value/min/max
dialog	在网页中央显示一个对话框或窗口，兼容性较差
属性：open
figure	用于对元素进行组合（一般用来组合一张图的标题、图片和图片描述等）
```

## 多媒体标签

> 多媒体标签为HTML5新增标签

### audio

- 支持的格式
  - `.mp3/.ogg/.wav`

- 属性


```
src	文件路径
autoplay	自动播放
loop	循环
controls	控制条
muted	静音
preload	预加载（当使用autoplay时，preload自动失效）
```

### video

- 支持的格式
  - `.mp4/.ogg/.webm`

- 属性


```
src	文件路径
autoplay	自动播放
loop	循环
controls	控制条
muted	静音
preload	预加载（当使用autoplay时，preload自动失效）
width	宽度
height	高度
poster	海报
```

### embed

嵌入内容或加载插件。

- 属性


```
src	文件路径
width	宽度
height	高度
type	类型
```

### canvas

画布标签，本质上是一个容器元素。

> 注意：
>
> 1. 单独使用canvas没有什么意义，它必须结合Javascript使用。它的具体功能体现是通过Javascript体现现来的
> 2. canvas的宽高不要通过css实现，而是直接使用标签属性width和height实现。

## HTML5常用属性

- `contentEditable`

将标签转换为可编辑状态。可用于所有标签。

属性值：true/false。

- hidden


对元素进行隐藏。一般用来传值或当某个条件成立，执行内容显示。默认值为hidden。

- data-*


自定义属性，一般用于传值。

- multiple


规定输入域中可选择多个内容。用于表单元素中，如file/select。

- required


约束表单元互在提交前必须输入值。用于表单组件中，需要结合提交按钮使用。

- pattern


用于验证输入字段的模式。用于表单组件中，需要结合提交按钮使用

## web字体引入

web字体引入指开发者在开发时为网页引入外部字体。

- 语法


```
@font-face {
    font-family: 字体名;
    src: url("字体文件.ttf") format("字体文件格式以处理浏览器兼容"),url(字体文件.woff) format(...), ...;
}
```

> 注意：可以同时引入多个字体文件，字体一样，但是文件的扩展名不一样
>
> 这样做的目的是为了处理浏览器兼容。

## 代码规范

### 常见规范

1. 定义语言编码

```
<meta charset="utf-8"/>
```

2. JavaScript定义

   ```html
   <script language="javascript" type="text/javascript">
   脚本代码
   </script>
   ```

3. css定义

   ```
   <style type="text/css">
   样式设置
   </style>
   ```

> 为保证各个浏览器的兼容性，在写css时请带上单位

4. 不要在注释内容中使用“--”
5. 所有的标签和属性的名字都必须用小写
6. 所有的属性值必须用双引号引起来
7. 如果文档中要输出<,>和&等，请使用实体转义符实现
8. 属性要么不写，要么就要给所有的属性赋一个值，否则如果没赋值，默认它的值就是**属性名本身**
9. 所有的标签都必须要有一个相应的结束标记（**标签必须要闭合**），尤其是单标签
10. 所有的标签必须合理嵌套，不能出现嵌套交叉情况
11. 图片要添加有意义的alt属性
12. 在form表单中增加label标签，增加用户的体验度

### 标签嵌套规则

1. 块级元素可以包含内联元素和某些块级元素，但内联元素却不能包含块级元素，它只能包含其他内联元素

2. 块级元素禁止放入p标签内

3. 有几个特殊的块级元素只能包含内联元素，不能再包含块级元素
   - 这几个特殊的标签是：`hx类标签，p标签、dt标签` 

4. 块级元素与块级元素并列，行内元素与行内元素并列，不允许块元素和行元素并列

### 块级元素和行级元素列表

- 块级元素


```
div、p、hx、ul、ol、dl、li、dd、table、hr、blockquote、address、menu、pre、header、section、aside、footer
```

- 行内元素


```
span、img、a、label、input、abbr（缩写）、button、em等格式化标签...
```

> img实际上属于行级块标签，相当于执行了`display:inline-block`的CSS语法
>

### 语义化标签

在书写HTML的时候尽量做到语义化标签，即能够通过标签使人明白每个标签的用途

- 优点


1. 更容易被搜索引擎收录

2. 更容易让屏幕阅读器读出网页内容

3. 能够更好的体现页面的主题

4. 兼容性更好，支持更多的网络设备

- 语义化标签的类型


```
<a>	超链接，可以用title属性显示提示内容
<p>	文章段落
<hx>	文章标题
<strong>、<em>	表示强调，em斜体，strong粗体
<q>	引用，浏览器会对q标签引用内容自动添加双引号
<address>	为网页加入地址信息或者联系方式等
<ul>	无序列表
<ol>	有序列表
<caption>	为表格添加标题和摘要，摘要的内容不会再浏览器中呈现，作用是增加表格的可读性（语义化）
```

### 搭建项目结构时文件和目录准备

1. 新建项目文件夹xtx-pc-client，在编辑器中打开

> 注意：
>
> 在实际开发中，项目文件夹不建议使用中文
>
> 所有项目相关文件都保存在xtx-pc-clien目录中
>

2. 复制favicon.ico到xtx-pc-client目录

> 注意：一般习惯将ico图标放在项目根目录
>

3. 复制images、uploads和lib目录到xtx-pc-clien目录中

注意：

> images：存放网站固定使用的图片素材，如logo、样式修饰图片等
>
> uploads：存放网站非固定使用的图片素材，如：商品图片、宣传图片等
>
> lib：存放网站使用的模板或者引入的外部文件、框架、库等
>

4. 新建index.html在根目录

5. 新建css文件夹保存网站样式，并新建以下三个css文件：

```
base.css	基础公共样式，里面保存着默认样式
common.css	该网站中多个网页相同模块的重复样式，如头部、底部
index.css	首页样式
```

### 企业官网文件命名规范

项目开发时，项目中文件或目录名中**不能出现汉字和空格**之类的其他字符，**文件和目录名**一般以字母或下划线开头，其后可以出现字母数字或者下划线，切记**不可出现空格**

- 几种常用目录名


```
产品目录	xxxxx(产品名)pro
图片文件目录	images/img/pic
视频	video
音频	music
文件工程	file
```

- 几种常用文件名


```
首页	index.html（必须是这个）
订单页 	order.html
公司介绍 	about.html
新闻列表 	news.html
新闻详情页	news_details.html
产品列表 	product.html
产品详情页	pro_details.html
联系我们 	contact.html
```



# CSS

## 基础知识

### FC（格式上下文）

FC即Fomatting Context(格式上下文)。它是CSS2.1规范中的一个概念。

FC具体指的是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。

FC分为：BFC和IFC。

#### BFC（块级格式上下文）

##### BFC特性（规则）

1. 内部的盒子会在垂直方向上一个接一个的放置
2. 垂直方向上的距离会叠加，值由最大margin值决定（如果不想要叠加，则需将该盒子变成一个独立的盒子）
3. BFC的区域不会float元素区域重叠
4. 计算BFC的高度时，浮动元素也参与计算
5. BFC就是页面上的一个独立的容器，容器里面的子元素不会影响到外面的元素

##### 形成BFC的条件

1. 浮动元素（float除none以外的值）
2. 定位元素（position(absolute/fixed))
3. display（值为inline-block/table-cell/table-caption时）
4. overflow（值为hidden/auto/scroll时）

##### BFC的作用

1. 解决margin重叠的问题（添加独立BFC）
2. 解决浮动高度塌陷的问题（在父级添加overflow:hidden）
3. 解决侵占浮动元素的问题（添加overflow:hidden清除浮动）

#### IFC：内联（行级）格式上下文

##### IFC特性（规则）

1. IFC的元素会在一行中从左至右排列
2. 在一行上的所有元素会在该区域形成一个行框
3. 行宽的高度为包含框的高度，高度为行框中最高元素的高度
4. 浮动的元素不会在行框中，并且浮动元素会压缩行框的宽度
5. 行框的宽度容纳不下子元素时，子元素会换下一行显示，并且会产生新行框
6. 行框的元素内遵循text-align和vertical-align

##### 形成IFC的条件

1. font-size
2. line-height
3. height
4. vertical-align

### CSS基础知识

#### 什么是CSS

CSS即层叠样式表，是用来美化网页的工具。

#### CSS的基本语法

```
选择器 {
属性: 属性值;
}
```

#### CSS的特性

##### 继承性

- 特性

子元素有默认继承父元素样式的特性

> 注意：可以通过调试工具判断样式是否可以继承

##### 层叠性

- 特性

1. 给同一个标签设置不同样式，样式会层叠叠加，共同作用在标签上

2. 给一个标签设置相同的样式，样式会层叠覆盖，最终写在最后的样式生效

> 注意：当样式冲突时，只有当选择器优先级相同时，才能通过层叠性判断结果

#### 选择器的分组和继承

- 选择器的分组

让多个选择器（元素）具有相同的样式，一般用于设置公共样式。

- 选择器的继承

子元素可以继承父元素的样式，反之不可以。

#### 样式权重

!important(10000)>内联样式(1000)>id选择器(100)>类、伪类和伪元素选择器(10)>标签选择器(1)

样式权重之间不能进位（实质上可以，但并非十进制）

#### CSS的一般书写顺序：

1. 浮动
2. 盒子模型：margin border padding 宽度高度背景色
3. 文字样式

> 注意：该书写顺序非必要，但采用该书写顺序可以提高浏览器的执行效率

### CSS使用方式

#### CSS的4种使用方式

CSS的四种使用方式为行间样式、内部样式、外部样式、导入外部样式。

1. 行间样式

行间样式即直接在标签上书写样式。

2. 内部样式

内部样式即在文件内部的<style>标签中书写样式。

3. 外部样式

外部样式即用link标签引入CSS文件

4. 导入外部样式

导入外部样式即在style标签中用import导入CSS文件

#### 四种CSS使用方式的区别

四种引用方式的区别主要在于作用域不同

- 行间样式只作用于当前标签

- 内部样式作用于当前文件
- 外部样式可以被多个HTML文件引用。

> 在实际项目开发中，最好使用外部样式。

#### link引入与import引入的区别

1. link是XHTML标签，除了加载CSS外，还可以定义RSS等其他事务；@import属于CSS范畴，只能加载CSS。

2. link引用CSS时，在页面载入时同时加载；@import需要页面网页完全载入以后加载。

3. link是XHTML标签，无兼容问题；@import是在CSS2.1提出的，低版本的浏览器不支持。

4. link支持使用Javascript控制DOM去改变样式；而@import不支持。

### CSS伪元素概念

#### CSS伪元素与伪类区别

1. css引入伪类和伪元素概念是为了格式化文档树以外的信息。即伪类和伪元素是用来修饰不在文档树中的部分

2. 伪类用于当已有元素处于的某个状态时，为其添加对应的样式，这个状态是根据用户行为而动态变化的。

3. 它只有处于dom树无法描述的状态下才能为元素添加样式，所以将其称为伪类。

4. 伪元素用于创建一些不在文档树中的元素，并为其添加样式。

> 比如说，我们可以通过:before来在一个元素前增加一些文本，并为这些文本添加样式。
>
> 虽然用户可以看到这些文本，但是这些文本实际上不在文档树中。

#### 伪元素&伪类的特点

1. 伪元素和伪类都不会出现在源文档或者文档树中
2. 伪类允许出现在选择器的任何位置，而一个伪元素只能跟在选择器的最后一个简单选择器后面
3. 伪元素名和伪类名都是大小写不敏感的
4. 有些伪类是互斥的，而其它的可以同时用在一个元素上。

> 在规则冲突的情况下，常规层叠顺序决定结果

#### 伪元素注意事项

`:before、:after、:first-letter、:first-line` 前面可以是1个冒号也可以是双冒号

`::selection、::placeholder、::backdrop` :	前面只能是双冒号

## CSS选择器

### 基本选择器

#### 通配符选择器（即*选择器）

- 定义

通配符选择器用于匹配html中或指定标签中所有元素

- 样例

```
* {} 
或 
div *{}// 匹配div下面的所有元素
```

- 权重

0

> 注意：*选择器的性能极差，因为它要匹配所有元素，所以在开发时不建议使用

#### 元素选择器

- 定义

元素选择器用于选择指定类型的HTML元素，如div、ul、li等

- 样例

```
div {}
```

- 权重

10

#### 类选择器

- 定义

类选择器用于选择指定类名的标签

- 样例

`.demo{} 或 p.demo{}`

- 权重

100

#### ID选择器

- 定义

​	ID选择器用于选择指定id名的标签

- 样例

```
#id {}
```

#### 群组选择器

- 定义

将具有相同样式的元素分组在一起，每个选择器之间使用逗号“,”隔开

- 样例

```
.first, .last {}
```

### 层次选择器（关系选择器）

#### 后代选择器

* 定义

选择匹配的 F 元素，且匹配的 F 元素被包含在匹配的 E 元素内。

这里 F 不管是 E 元素的子元素或者是孙元素，都将被选中。

* 样例

```
.demo li {}
```

2、子元素选择器

* 定义

选择匹配的 F 元素，且匹配的 F 元素是所匹配的 E 元素的子元素

* 样例

```
.demo > li {}
```

#### 相邻兄弟选择器

* 定义

选择匹配的 F 元素，且匹配的 F 元素是紧接在匹配的 E 元素的后面

* 样例

`li + li {}`

#### 通用兄弟选择器

* 定义

兄弟选择符，位置无须紧邻，只须同层级

如A~B表示 选择A元素之后所有同层级B元素

* 样例

```
p ~ span {}
```

### 属性选择器

#### [属性名]

* 定义

用于选取带有指定元素的标签，可连续使用多个

* 样例

```
.demo a[href][title] {}
```

#### [属性名=属性值]

* 定义

用于选取带有指定属性和值的元素，可连续使用多个

* 样例

```
.demo a[id="first"][title] {}
```

#### [属性名~=属性值]

* 定义

用于选取属性值中包含指定词汇的元素。只要属性值中有 value 就相匹配。

* 样例

```
a[class~="links"] {}
```

#### [属性名^=属性值]

* 定义

匹配属性值以指定 value 值开头的每个元素。

* 样例

```
a[href^="mailto:"] {}
```

#### [属性名$=属性值]

* 定义

匹配属性值以指定 value 值结尾的每个元素

* 样例

```
a[href$="png"] {}
```

#### [属性名*=属性值]

* 定义

匹配属性值中包含指定 value 值的每个元素。

* 样例

```
a[title*="site"] {}
```

#### [attr|=value]

* 定义

这个选择器会选择 attr 属性值等于 value 或以 value- 开头的所有元素

### 表单选择器

```
:input
:button
:submit
:text
:password
```

### 过滤选择器（难点）

#### 简单过滤选择器

```
:first或first()  第一个元素
:last或last()最后一个元素
:not(selector)  除selector之外的元素
:even  偶数元素
:odd	奇数元素
:eq(index)  第n个元素
:gt(index)  大于第n个后的元素
:lt(index)  小于第n个后的元素
:header	 选择h1-h6所有标题元素
```

#### 内容过滤选择器

```
:contains(text) 获取包含指定文本内容的元素
:empty  获取不包含子元素或文本内容的元素
:has(selector)  获取含有选择器所匹配的元素
:parent 获取含有子元素或文本的元素
```

#### 可见性过滤选择器

```
:hidden	选择display:none或隐藏文本域(hidden)的元素
:visible	选择display:block的元素
```

### 动态伪类选择器

#### 伪类

以下四个伪类的设置是有先后顺序的。

他们遵守爱恨原则 LoVe/HAte,也就是 Link--visited--hover--active。

* 样例

```
a:link {color:gray;} /*链接没有被访问时前景色为灰色*/
a:visited{color:yellow;} /*链接被访问过后前景色为黄色*/
a:hover{color:green;} /*鼠标悬浮在链接上时前景色为绿色*/
a:active{color:blue;} /*鼠标点中激活链接那一下前景色为蓝色*/
```

### UI元素状态伪类（仅需了解）

```
:unchecked	未选中
:checked	选中，只在Opera浏览器中有效
:disabled	不可写状态
:enabled	可写状态
```

### 结构伪类选择器

```
:first-child	选择父元素的第一个子元素
:last-child	选择父元素的最后一个子元素
:nth-child(n)选择父元素的第n个子元素
:nth-last-child(n)选择父元素的倒数第n个子元素
:nth-of-type(n)选择父元素内具有指定类型的第n个子元素
:nth-last-of-type(n)选择父元素内具有指定类型的倒数第n个子元素
:only-child
:only-of-type
:empty	选择没有子元素的元素，且该元素不包含任何节点
```

### 否定伪类和目标伪类选择器（仅需了解）

- 否定伪类选择器

```
:not()
```

- 目标伪类选择器

```
:target
```

### 伪元素选择器

```
::first-line	选择元素第一行
::first-letter	选择文本块的第一个字母
::before和::after	 这两个主要用来给元素的前面或后面插入内容
::selection	用来改变浏览网页选中文的默认效果。
::selection 只能设置两个属性： background和color 
```

## CSS字体

```
font-size	字号(px/%)
font-family	字体
font-style	文字样式(normal/italic/oblique)
font-weight	文字加粗(normal/bold/bolder/lighter/100-900)
line-height	行高(px/数字/em等)
color	文字的颜色(颜色的单词/rgb()/16进制)
text-decoration	文字修饰(none/underline/overline/line-through)
text-align	文本对齐方式(left/right/center)
text-transform	字母大小写(capitalize/uppercase/lowercase/none)
text-indent	文本缩进(px/em/%/pt等)
```

- font复合属性

```
font:font-style font-variant font-weight font-size/line-height font-family;
```

- 注意点

1. 属性值的位置顺序
2. 除了font-size和font-family之外，其它任何一个属性值都可以省略
3. font-variant：normal/small-caps（让大写字母变得小一些）

## 背景

### CSS背景

```
background-color	背景色(transparent/color)
background-image	背景图(none/url)
background-repeat	背景图像铺排方式(repeat/no-repeat/repeat-x/repeat-y)
background-position	设置对象的背景图像位置
属性值
({x-number|top|center|bottom},{y-number|left|center|right})
background-attachment	背景图像滚动位置(scroll/fixed)

背景的复合写法
background: color image repeat attachment position
```



### CSS3背景

- 多重背景


```
background: 背景色1 背景图片1 平铺方式1 位置1,背景色2 背景图片2 平铺方式2 位置2,...
```

- 设定背景图像的尺寸


```
background-size: 固定长度|百分比值|cover|contain;
```

- 指定背景图像的位置区域


```
background-origin: padding-box|border-box|content-box;
```

- 设定背景的绘制区域


```
background-clip: border-box|padding-box|content-box;
```

- 渐变背景


```
background-image: linear-gradient(渐变方向,颜色1 [颜色1占比],颜色2 [颜色2占比],...); | radial-gradient(shape size at position, start-color, ..., last-color);
```

> 第一个渐变为线性渐变，第二个渐变为径向渐变
>
> 渐变方向有：
>
> 1. to left | to right | to top | to bottom
> 2. to bottom left | to top left | ...
> 3. 角度，即 `数值deg`，正上方为0deg位置，角度方向为顺时针方向
>
> 颜色既可以使用#ffffff的形式，也可以使用rgb()和rgba()函数

## display属性

display属性用于设置元素的显示方式

- 属性值


```
none	不显示元素
block	块显示，在元素前后设置换行符。
目的：将行级标签转换为块级标签（使得行级标签能像块级标签一样设置宽高）
inline	行内显示，将块级标签转换为行级标签。
inline-block	将块级或行级标签转换为行内块级标签。
```

## table样式

> table样式现在一般不用来布局，而是用来格式化数据。

- 属性

```
width	宽度
height	高度
border-collapse:collapse; 单线边框
border	边框线
```

- td,tr属性

```css
width	宽度
height	高度
border	边框线
text-align	文本左右对齐(left(默认)/center/right)
vertical-align	文本垂直对齐(top/middle(默认)/bottom/baseline)
```



### 列表样式

```
list-style-image	用图像表示标识
list-style-position	列表标识的位置
属性值：
	inside
	outside	默认属性
list-style-type	标识类型
属性值：
无序：disc(默认)/circle/square
有序：
	decimal	默认
                            decimal-leading-zero
                            lower-roman
                            upper-roman
                            lower-alpha
                            upper-alpha
                            lower-greek
                            lower-latin
                            upper-latin
```

- 样式简写


	list-style:list-style-image list-style-position list-style-type;

> 注意：list-style的值可以按任意顺序列出，而且可以任意省略，只要提供其中一个值，其它的都自动默认。

## 隐藏

### 占位隐藏

visibility:hide

### 不占位隐藏

display:none

### 显示隐藏元素的常用写法

利用父节点的伪类来实现显示隐藏元素

```html
<style>
    .box1:hover .box1_2{
        display:block;
    }
</style>
<div class=”box1”>
<div>显示元素</div>
<div class=”box1_2“ style=”display:none”>这是被隐藏的元素</div>
</div>
```

## 浮动

### 浮动基础

- 什么是浮动

浮动指的是让块级标签不独占一行

- 浮动目的

把块级标签元素可以排在一行上

- 原理


浮动的原理就是让元素脱离文档流，不占用标准流

- 浮动的作用


早期作用：图文环绕

现在作用：网页布局

- 浮动的特点


1. 浮动元素会脱离标准流（简称：脱标），在标准流中不占位置

2. 浮动元素比标准流高半个级别，可以覆盖标准流中的元素

3. 下一个浮动元素会在上一个浮动元素后面左右浮动

4. 浮动元素有特殊的显示效果：一行可以显示多个且可以设置宽高

- 注意点


浮动的元素不能通过`text-align:center`和`margin:0 auto`设置居中

- 浮动的语法

```css
选择器 {
	float: left | right | none;
}
```

> left	   左浮动
>
> right	右浮动
>
> none	默认值，不浮动
>

> 浮动后，后面的元素不管是块级还是行级元素，不会显示在下一行。
>

### 清除浮动

- 清除浮动的目的

让后面的元素自动掉到下一行。

- 方法


1. 添加空标签，并根据需要设置如下样式

```css
clear:left;  清除左浮动
clear:right; 清除右浮动
clear:both;  清除左右浮动
clear:none;  左右浮动都不清除
```

2. 在浮动节点的父节点添加样式如下样式

```css
overflow:hidden;  作用为使超出部分隐藏，也可以用来实现清除浮动。
```

3. 在浮动元素的父级添加伪元素，并设定如下样式

```css
父元素:after{
    content:"";
    display: block;
    clear:both;
}
```

> 在实际项目开发中，我们优先使用第2、3种方案，不推荐第一种方案
>

## 盒子模型

### 基础知识

1. 每个元素都是一个盒子，一个盒子由一下四部分组成
   1. margin  外边距
   2. border  边框线
   3. padding  内边距
   4. content  内容

2. 盒子的content由padding和content组成

3. 区别外边距和内边距是以边框为参照

4. 系统默认外边距为**8px**

### 盒子模型样式

#### 外边距(margin)

外边距指元素边框线之外的距离

- 可选写法

```css
margin、margin-left、margin-right、margin-top、margin-bottom
```

其中margin可用来设置任意一个边的边距，可以带1至4个参数

参数数量对应的写法如下

```
1个参数上下左右外边距均为apx
2个参数上下外边距为apx，左右外边距为bpx
3个参数上外边距为apx，下外边距为cpx，左右外边距为bpx
4个参数四个参数依次对应上、右、下、左外边距
```

#### 内边距（padding）

内边距指元素的文本内容与边框之间的距离，用法与margin完全一样

#### 边框(border)

```css
border-width:边框线宽度;
border-style:边框线样式;
border-color:边框线颜色;
```

- 复合写法（简写）


```css
border:border-width border-style border-color;
```

> 注意：三个参数可以不按照顺序写
>

#### 盒子的真实尺寸

盒子宽度 =  width + padding左右 + border左右

盒子高度 = height + padding上下 + border上下

## 定位(position)

#### 定位的作用

定位可以设定元素在文档中的位置

> 注意：定位会将标签转换为块级标签

#### 定位的属性

- static:静态定位

默认值，没有定位，不能设置偏移值(left/top/right/bottom)，占用标准流（文档流）

- relative:相对定位


占用标准流（文档流），它会出现在文档流中它该出现的位置。可以通过设置偏移值改变其位置。它相对于自身所占的位置做偏移。

- absolute:绝对定位


脱离文档流，相对于由relative定义的父元素做偏移，如无则默认为body标签。

绝对定位一般与相对定位结合使用，它相对第一个由relative定义的祖先元素做偏移，

> 在项目开发中，一般用relative+absolute结合使用。

- fixed:固定定位


脱离文档流，相对于浏览器窗口左上角（0，0）做偏移，它跟父级的定位没有任何关系

> 该属性一般在开发中用来固定导航栏。
>

#### z-index

当多个元素添加**绝对定位**时，如果位置相同，各个标签将会叠加在一起，此时可以使用z-index样式设置元素显示的层次

> 文档流默认的z-index的值为0。
>
> z-index属性对使用static、relative和fixed定位的标签无效，其只对absolute定位的标签有效
>

## 多列（分栏）

- column-count 
  - 规定元素应该被分隔的列数（栏数）

```
column-count: number|auto;
```

- column-gap
  - 设置栏间距

```
column-gap: length|normal;
```

- column-rule

  - 设置栏间分隔线

  - column-rule-style：设置线型。

    - 属性值


    - ```css
      none	没有分隔线
      hidden	隐藏线
      dotted	点线
      dashed	虚线
      solid	实线
      double	双线
      groove	3D沟槽效果
      ridge	3D脊状效果
      inset	3D左上角阴影效果
      outset	3D右下角阴影效果
      ```

    - 注意：3D线型在分栏中没有3D效果，会当做实线处理

  - column-rule-width
    - 设置线宽
  - column-rule-color
    - 设置分隔线颜色。

  - 复合写法：`column-rule:width style color;`


- column-width
  - 设置栏宽

```
column-width: length|auto;
```

- columns
  - column-width 和 column-count 的简写方式。

```
columns: width count;
```

## CSS3

### 新属性

1. 增加了选择器

2. 阴影

3. 增加了形状转换（2D <-> 3D）

4. 增加了变形效果

5. 动画（过渡动画、帧动画）

6. 边框

7. 多重背景

8. 反射

9. 文字

10. 颜色函数（rgba/hsl/hsla）

11. 滤镜（filter）

12. 弹性布局

13. 多列布局

14. 栅格布局

15. 盒模型

16. Web字体

17. 媒体查询


### 兼容处理

CSS3不是属于浏览器或同一浏览器的不同版本都支持，所以需要兼容处理，通常的做法就是加厂商前缀。

```
IE	-ms-
Chrome&Safari	-webkit-
FireFox	-moz-
Opera	-o-
```

可以进入`www.caniuse.com`网站中查询HTML和CSS的兼容性处理问题

### CSS3文本

#### 文本阴影

```css
text-shadow:水平偏移距离 垂直偏移距离 [模糊距离] [阴影的尺寸] [颜色] [inset];
```

#### 文本自动换行

```
word-wrap: normal|break-word;
```

#### 单词拆分

```
word-break: normal|break-all|keep-all;
```

#### 文本拆分

```
text-wrap: normal|none|unrestricted|suppress;
```

#### 文本溢出

- 单行文本溢出


```
text-overflow: clip|ellipsis|string;
```

实际应用示例

```css
选择器 {
    width: px/%/em/rem...;
    white-space: nowrap; /* 为允许折行 */
    -ms-text-overflow: ellipsis; /* 处理IE兼容 */
    text-overflow: ellipsis;
    overflow: hidden;
}
```

- 多行文本溢出


```css
选择器 {
	width: px/%/em/rem...;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 行数;
    overflow: hidden;
}
```

### CSS3边框

#### 圆角边框

```
border-radius: 1-4个length|% / 1-4 length|%;
```

> 每个半径的四个值的顺序是：左上角，右上角，右下角，左下角。

### 边框阴影

```
box-shadow: 水平偏移距离 垂直偏移距离 [模糊距离] [阴影的尺寸] [颜色] [inset];
```

### 边框图片

```
border-image：图片 向内偏移距离 宽度 图像区域超出边框的距离 重复效果;
```

> 重复效果：round/strech/repeat
>

### 颜色函数

#### RGBA

```
rgba(r,g,b,a)
```

```
r:红色取值范围：0-255/0-100%
g:绿色取值范围：0-255/0-100%
b:蓝色取值范围：0-255/0-100%
a:不透明度数  取值范围：0-1的一个小数
```

#### HSL

```
hsl(h,s,l)
```

```
h:色调 取值范围：0-360
s:饱和度    取值范围：0-100%
l:亮度 取值范围：0-100%
```

#### HSLA

```
hsla(h,s,l,a)
```

```
h:色调  取值范围：0-360
s:饱和度 取值范围：0-100%
l:亮度  取值范围：0-100%
a:不透明度取值范围：0-1的一个小数
```

### opacity

调整元素的不透明度，大多数情况下用于做元素的遮罩效果。

取值范围：0-1的一个小数

​	IE8及8以下版本不支持opacity，处理兼容的方式，再添加一行代码来处理不透明度：

​	filter:alpha(opacity=数值）数值的范围：0-100

### 渐变

渐变主要用来设置背景或制作三维图。

#### 线性渐变

```
background: linear-gradient(方向或角度, 颜色1 百分比, 颜色2 百分比, ...);
```

- 方向


```
to left:从右向左渐变
to right:从左向右渐变
to top:从下向上渐变
to bottom:从上向下渐变
to top left:从右下角向左上角渐变
to top right:从左下角向右上角渐变
to bottom left:从右上角向左下角渐变
to bottom right:从左上角向右下角渐变
```

- 角度


例如45度角表示为：45deg

- 颜色取值


1. 表示颜色的单词

2. 16进制颜色
3. 表示颜色的函数（`rgb()/rgba()/hsl()/hsla()...`)


#### 径向渐变

径向渐变即沿半径方向渐变

```
background: radial-gradient(形状 渐变大小 at 位置,颜色1 百分比, ..., 颜色n 百分比);
```

- 形状


```
ellipse	椭圆径向渐变（默认）
circle	圆径向渐变
```

- 渐变大小


```
farthest-corner	渐变的半径长度为从圆心到离圆心最远的角（默认）
closest-side	渐变的半径长度为从圆心到离圆心最近的边
closest-corner	渐变的半径长度为从圆心到离圆心最近的角
farthest-side	渐变的半径长度为从圆心到离圆心最远的边
```

- 位置


```
center	设置圆心在中心位置（默认）
top	设置圆心在顶部位置
bottom	设置圆心在底部位置
at 圆心橫坐标 圆心纵坐标设定圆心的位置在指定的（橫坐标，纵坐标）处
```

#### 文字渐变

文字渐变不是一种样式，而是一种组合写法

- 示例

```
选择器 {
    background-image: 线性渐变或径向渐变;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}
```

### box-sizing

该样式允许你以某种方式定义某些盒子模型，以适应指定的区域。

```
box-sizing: content-box/border-box
```

> 火狐和谷歌低版本需要厂商前缀
>

## flex弹性布局

### 什么是flex布局

flex布局也叫弹性布局或者CSS3弹性盒，是浏览器提倡的布局模型

- 好处

1. flex布局能够使网页布局更简单、更灵活
2. flex布局能够避免浮动脱标的问题，可以在当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。

- 作用


1. 提供一种有效的方式对一个容器中的子元素进行排列、对齐和分配空白空间

2. flex能够精确灵活地控制块级盒子的布局方式，避免标签脱离文档流的现象发生

3. flex布局非常适合结构化布局


### flex布局的组成部分

弹性容器添加display:flex的元素，即父元素

弹性盒子子元素

主轴默认主轴在水平方向

侧轴（交叉轴）默认侧轴在垂直方向

### flex布局的语法

- flex-direction

修改主轴方向

参数

```
row	横向从左到右排列（左对齐），默认的排列方式
row-reverse	反转横向排列（右对齐，从后往前排，最后一项排在最前面
column	纵向排列
column-reverse	反转纵向排列，从后往前排，最后一项排在最上面
```

- justify-content

调整主轴对齐方式

参数

```css
flex-start	起点开始依次排列（左对齐）（默认值）
flex-end	终点开始依次排列（右对齐）
center	沿主轴居中排列
space-between	除了第1个和最后1个子元素外，其它子元素等分空白区域
space-around	所有子元素等分空白区域
space-evenly	弹性盒子沿主轴均匀排列，弹性盒子与容器之间间距相等 
```

- align-content 调整侧轴对齐方式

参数

```
flex-start	起点开始依次排列（左对齐）（默认值）
flex-end	终点开始依次排列（右对齐）
center		沿主轴居中排列
space-between	除了第1个和最后1个子元素外，其它子元素等分空白区域
space-around	所有子元素等分空白区域
```

- align-items、align-self

规定弹性盒子在侧轴的对齐方式

参数

```
flex-start	沿纵轴顶端对齐（默认值）
flex-end	沿纵轴底端对齐
center		沿纵轴垂直居中对齐
baseline	沿纵轴基线对齐
stretch		纵向拉伸对齐
```

- flex-grow

规定子元素的放大比例（应用于子元素）

参数

number，默认为0，即如果存在剩余空间，也不放大。

- flex

规定弹性盒子空间分配（应用于子元素）

> 注意：flex可以带1-3个参数。
>
> 1. 带1个参数
>    - 如果该参数无单位，这个数值会被当作flex-grow（放大）的值
>    - 如果该参数带单位，这个数值会被当作flex-basis（基本宽度）的值
>    - auto（自动宽度）|initial（初始宽度）|none（无）
> 2. 带2个参数
>    1. 第1个参数必须是一个无单位的数值，它会被当作flex-grow的值。
>    2. 第2个参数：
>       - 无单位，这个数值会被当作flex-shrink（收缩比率）的值
>       - 带单位，这个数值会被当作flex-basis（基本宽度）的值
> 3. 带3个参数
>    - 第1个参数必须是一个无单位的数值，它会被当作flex-grow的值。
>    - 第2个参数必须是一个无单位的数值，它会被当作flex-shrink(收缩比率)的值
>    - 第3个参数必须是一个有效的宽度值（带单位），它会被当作flex-basis（默认基准宽度值）的值

参数

```
auto	等价于 1 1 auto。
initial	等价于 0 1 auto。 
none	等价于 0 0 auto。
inherit	从父元素继承
```

- flex-wrap

规定弹性盒子是否换行

参数

```
nowrap	不换行，默认值
wrap	换行
wrap-reverse	以相反的顺序换行
```

## CSS动画

### 变形(transform）

1. 位移效果(translate)


```
translate(x,y) 	定义 2D 转换，沿着 X 和 Y 轴移动元素
translateX(n) 	定义 2D 转换，沿着 X 轴移动元素
translateY(n) 	定义 2D 转换，沿着 Y 轴移动元素
```

2. 缩放效果(scale)

```
scale(x,y) 定义 2D 缩放转换，改变元素的宽度和高度
scaleX(n) 定义 2D 缩放转换，改变元素的宽度
scaleY(n) 定义 2D 缩放转换，改变元素的高度
```

3. 旋转效果(rotate)

```
rotate(angle,angle) 定义 2D 旋转，在参数中规定角度（-360deg - 360deg）。
rotateX(angle)
rotateY(angle)
```

4. 变形效果(skew)

```
skew(x-angle,y-angle) 定义 2D 倾斜转换，沿着 X 和 Y 轴。  
skewX(angle) 定义 2D 倾斜转换，沿着 X 轴。
skewY(angle) 定义 2D 倾斜转换，沿着 Y 轴。
```

5. 矩阵形式变形（仅需了解）

matrix(a,b,c,d,e,f)  定义 2D变形，使用了6个值的矩阵

6个值的矩阵关系如下：

```
a  c  e
b  d  f
0  0  1
```

matrix用一个3*3的矩阵表示，a和b列表示x轴，c和d列表示y轴，e和f列表示z轴

- a和d表示缩放（如果没有缩放，值设为1）

- b和c表示扭曲（如果没有扭曲，值为0）

- e和f表示位移（如果没有位移，值为0）


如果旋转角度为θ,它会影响到a,b,c,d的值，即

- a = cosθ

- b = sinθ

- c = -sinθ

- d = cosθ


如果扭曲skew(θ1,θ2)，会影响到b和c的值：

- b = tanθ1

- c = tanθ2 


每次旋转和扭曲都会产生一个新矩阵，最终形成的多个矩阵要做乘法运算。

如果对一个元素同时有旋转、扭曲、缩放和位移，这里需要用到多个矩阵相乘，要优先考虑旋转和缩放！！！

### transform-origin

调整元素的基点

```
transform-origin: x-axis y-axis z-axis;
```

属性值

```
x-axis	定义视图在X轴的位置
		可选值：left，center，right，length，%
y-axis	定义视图在Y轴的位置
		可选值：top，center，bottom，length，%
z-axis	定义视图在Z轴的位置
		可选值：length。
```

### perspective

让子元素获得透视效果

```
perspective:length|none;
```

### transform-style

在3D空间中呈现被嵌套的元素(必须与 transform 属性一同使用)。

```
transform-style: flat|preserve-3d;
```

### rotateZ

 沿着Z轴的方向顺指针旋转，需要配合perspective样式使用

### transition

过渡动画

1. 常规写法


```
transition-property
transition-duration
transition-timing-function
transition-delay
```

2. 复合写法

```
transition: property-name-list|all duration timing-function delay;
```

- transition-property可选值


1. 颜色


```
color background-color border-color outline-color
```

2. 位置

```
background-position left right top bottom
```

3. 长度

```
max-height min-height max-width min-width height width
border-width margin padding outline-width outline-offset
font-size line-height text-indent vertical-align
border-spacing letter-spacing word-spacing
```

4. 数字

```
opacity visibility z-index font-weight zoom
```

5. 组合

```
text-shadow transform box-shadow clip
```

6. 其它

```
gradient	自定义关键帧动画
```

- transition-duration

动画持续时间，一般以秒(s)或毫秒(ms)为单位

- transition-timing-function

动画函数

可选值：

1. linear:匀速
2. ease:变速（先慢后快，最后再慢）
3. ease-in:变速（由慢到快）

4. ease-out:变速（由快到慢）

5. ease-in-out:变速（慢速开始，慢速结束）

6. cubic-bezier(n,n,n,n):自行设定变速，n的值在0-1之间

7. delay:动画延时时间，一般以秒(s)或毫秒(ms)为单位


### 关键帧动画

#### 设置关键帧

1. 如果只有两个关键帧


```
@keyframes 动画名 {
	0%:{样式表}
	100%:{样式表}
}
或
@keyframes 动画名 {
	from:{样式表}
	to:{样式表}
}
```

2. 如果是多个关键帧

```
@keyframes 动画名 {
    0%:{样式表}
    25%:{样式表}
    60%:{样式表}
    ...
    100%:{样式表}
}
```

> 注意：这里的百分比可以是0%-100%之间的做任意值，一般为升序，也支持倒序
>

#### 实施动画

- 常规用法


```
animation-name		来自于@keyframes定义的动画名
animation-duration	动画持续时间，一般以秒(s)或毫秒(ms)为单位（默认为0）
animation-timing-function	动画函数
                inear	匀速（默认值）
                ease	变速（先慢后快，最后再慢）
                ease-in	变速（由慢到快）
                ease-out	变速（由快到慢）
                ease-in-out	变速（慢速开始，慢速结束）
				cubic-bezier(n,n,n,n):自行设定变速，n的值在0-1之间
animation-delay		动画延时时间，一般以秒(s)或毫秒(ms)为单位
animation-iteration-count	动画循环播放的次数
				number	按设定次数循环播放（默认次数为1次）
				infinite	一直循环播放
animation-direction		动画播放完后是否反向播放
				normal	不反向（默认值）
				alternate	反向
animation-play-state	动画播放或停止播放
				paused	停止播放
				running	播放（默认值）
```

- 简洁用法


```
animation:name duration timing-function delay iteration-count direction;
```

## iconfont图标字体

由阿里巴巴提供的一种图标字体。

网址：http://iconfont.cn

- 使用方法

1. 下载iconfont文件，解压后，将部分文件复制到我的网页项目中
2. 使用字体图标前，先引入iconfont.css文件

3. 使用字体图标方法
   1. 用类名
      - `<div class="iconfont icongerenzhongxin"></div>`
   2. 用unicode值（微信小程序开发不支持这种写法）
      - `<div class="iconfont"></div>`


## CSS速查表(待补充)
