# HTML篇

## 基础知识

### 认识HTML和超文本标记

#### HTML

HTML即超文本标记语言。它是一种标记语言，而非编程语言，不能使用逻辑运算。	HTML通过标签将网络上的文档格式进行统一，使分散网络资源链接为一个逻辑整体，	即HTML使用标签来描述网页内容

#### 超文本

超文本是一种组织信息的方法，通过超级链接将多种媒介关联起来

#### 静态网页

静态网页即代码写完后页面内容不会再发生任何改变的网页

注意：幻灯片效果、文字滚动效果等动画也属于静态网页

#### 动态网页

动态网页即页面代码没有变，但显示的内容可以随着时间、环境或者数据库操作的结果而发生改变的网页

#### 标记

标记即标签，是用<>包裹的具有一定含义的内容

标记语言就是一套标记标签

6、块级元素和行级元素

1）块级元素：

块级元素在浏览器中会单独占一行，宽度自动填满其父元素宽度，块级元素可以设置width，height属性

2）行内元素

行内元素在浏览器中不会单独占一行，相邻的行内元素会排列在同一行，直到一行	排不下才会换行

行内元素的宽度随元素的内容而变化，对行内元素设置width和height无效

行内元素一般用在网站内容之中的某些细节或部位，用以强调，如<strong>标签等

7、W3C标准

万维网联盟（W3C）标准不是某一个标准，而是一系列标准的集合。

W3C标准规定了网页主要由三部分组成：

结构（Structure）、表现（Presentation）和行为（Behavior）。

结构即HTML结构，表现即CSS，行为即JS

8、HTML基本结构：详见文档

 

### **1.1.2.** ***\*HTML5\****

1、HTML5由W3C和WHAT组织机构共同研发出来的，于2014年正式发布。

2、HTML5成为了新一代网页开发标准。

3、HTML5的特性

简易性、可拓展性、平台无关性、通用性

4、HTML5新功能（面试）

​	1）增加了audio和video音频播放，抛弃了Flash

​	2）新增了canvas画布（绘画，制作动画（如小游戏开发等））

​	3）地理定位

​	4）增加了离线缓存

​	5）硬件加速

​	6）Web Socket（全双工通信）

​	7）增加了本地存储

​	8）新增了一些语义化标签

 

### **1.1.3.** ***\*浏览器及其内核\****

1、五大主流浏览器

IE（edge）、Firefox、Chrome、Opera、safari

2、浏览器内核的组成

浏览器内核由渲染引擎和JS引擎两部分组成

3、五大浏览器内核

1）Trident内核

代表产品为IE，又称IE内核

2）Gecko内核

著名浏览器为Firefox，该内核开源，但使用人数很少，启动速度较慢

3）webKit内核

主要用于Mac OS，代表产品为Safari、2013年前的Chrome、iPhone/ipad，也是安卓4.4版本及之前所采用的的内核

4）Presto内核

代表产品为OperaPresto，13年后弃用（可不计）

5）Blink内核

2013年发布，现在Chrome和Opera内核都是Blink，安卓4.4之后使用该内核

注：

国内大多数浏览器采用双核驱动

### **1.1.4.** ***\*几种常用开发工具\****

1）Dcloud HBuilder

拥有完整的语法提示和代码输入法，编写代码速度更加快捷，默认添加emmet语法	插件。轻量级开发软件，无需安装

2）Sublime Text 3

轻量级软件，功能强大，可以写很多文件，还可跨平台使用

3）VS code

轻量级软件，功能强大

4）webstorm

重量级软件，HTML5编辑工具，支持代码格式化，推荐前端工程师使用，占用内存		和CPU高

5）notepad++

轻量级软件

### **1.1.5.** ***\*SEO\****

1、什么是SEO

SEO(Search Engine Optimization)即搜索引擎优化

2、为什么我们需要SEO

我们可以根据SEO规则优化自己的网站，让自己的网站在搜索引擎中的排名更靠前

3、提升SEO的常见方法：

1.竞价排名

2.将网页制作成html后缀

3.标签语义化

4.......

4、SEO三大标签

SEO三大标签即对SEO最有用的三种标签

1.title：网页标题标签

2.description：网页描述标签

3.keywords：网页关键词标签

 

## 1.2. 标签

### **1.2.1.** ***\*认识标签\****

1、标签由标签名、标签属性和文本内容三部分组成（注意：单标签没有文本内容）。

2、基本标签

<div>、<hx>、<p>、<br />、<hr />、<a>、<img>、<span>、<ul>、<il>

### **1.2.2.** ***\*标签属性\****

标签属性是对标签的一种描述方式，标签属性分通用属性、自有属性和自定义属性。

1、通用属性

1）通用属性是所有标签都具有的属性（除<br />标签外）。

2）通用属性有：

id：用来给标签取一个唯一的名称。id名称在一个网页必须是唯一的。

class：用来给标签取一个类名。	

style：用来设置该标签的行内样式。

title：当鼠标移到该标签，所显示的提示内容。

2、自有属性

自有属性是每个标签自己拥有的特殊属性

3、自定义属性

自定义属性是用户自定义的标签属性，该属性通常用来传值或用于图片懒加载等

格式：

data-*

Js获取自定义属性的方式：

兼容性获取：

dom.getAttribute(自定义属性名)

H5新增（IE11以上支持）

dom.dataset.* 或 dom.dataset[‘*’]

自定义属性样例：

<img data-src="图片名" alt="提示文本"/>

## 1.3. 表格

### **1.3.1.** ***\*表格标签\****

caption	标题

thead	表头

tbody	表体

tfoot	表尾

tr		行

th		标题列

td		普通列

### **1.3.2.** ***\*表格属性（大部分已被淘汰）\****

​	border		表格边框，默认单位为px，已被淘汰

​	width		表格宽度，默认单位是像素

​	align		表格对齐方式（left（默认）/center/right）

​	cellpadding	单元格文本与边框的距离

​	cellspacing	单元格边框间距

rowspan		跨行

​	colspan		跨列

 

### **1.3.3.** ***\*表格样例\****

<table>

<caption>表格名称</caption>

<thead>

<tr>

<th>名称</th>

<th>年龄</th>

</thead>

<tbody>

...

</tbody>

<tfoot>

...

</tfoot>

</table>

## 1.4. form表单元素

### **1.4.1.** ***\*form表单标签\****

form表单标签是所有标签最核心标签之一。它是用来实现前后端交互的一个重要标签。

常用属性：

​	name	表单名称

​	action	表单数据提交的地方，通常为#、后台文件名或网址。

若为#，则表示提交到当前文件下。

​	method	前端提交数据到后端的方法，get后者post，get为默认值

### **1.4.2.** ***\*表单元素的分类\****

1、input类

input类主要用来输入，选择或发出指令。

 

type常用属性

1）text	

type="text"，单行文本输入框，type="text"可以不写，为默认值。

​		常用属性：

placeholder	提示

name	命名

minlength	最少输入的字符个数

maxlength	最多输入的字符个数

disabled		失效

readonly		只读

 			value		默认值

pattern		正则匹配	

autocomplete	组织表单的默认填充行为（新属性）

autocomplete可选值：

on	启用自动完成行为（默认值）

off	禁用自动完成行为

 2）password	

type="password"，密码输入框，常用属性与text一样

  3）radio

​	type="radio"，单选按，通常为两项以上，需要配合name属性实现单选功能。

常用属性：

name	名称，必须要有

value	上传时显示的选项值

checked		选中

disabled		失效

readonly		只读

样例：

<input type=”radio” name=”sex” value=”男”/>男

<input type=”radio” name=”sex” value=”女”/>女

4）checkbox

​	复选框，可以用来选择0项、1项或多项。

​	常用属性：

name	必须要有

value	上传时显示的选项值

checked		默认选中

disabled		失效

readonly		只读

样例：

<input type="checkbox" name="sex" value="男">男
					<input type="checkbox" name="sex" value="女">女
					<input type="checkbox" name="sex" value="未知">未知

  5）file	

文件上传按钮，用来上传文件

常用属性：

name		名称，必须有

multiple		多选文件

样例：

<input type="file" name="file">

 

  6）button	

普通按钮，通常用它去调用脚本代码。

  	常用属性：

value		按钮的标题

disabled		失效

  7）image

​		图片提交按钮，与submit功能，能够提交表单

自有属性：

src		用来加载提示图片，用它替换value

  8）submit

提交按钮，用来将表单数据提交到后台。

  	常用属性：

value	按钮的标题

disabled		失效

​	9）reset

重置按钮，将表单所有组件输入的内容全部清空，还原为初始状态。

​		常用属性：

value		按钮的标题

disabled		失效

2、textarea类

​	文本域（也可以叫多行文本框），主要用于输入大批量的文本内容。

​	常用属性：

name	名称

id

cols		文本域列数

rows	文本域行数

placeholder

minlength	最小长度

maxlength	最大长度

required		必须输入

value

3、select类

​	下拉列表框，默认用于单项选择。用option呈现每个选项。

常用属性

​	multiple		表示可以多选，这时的下拉列表框变成了列表框

​		size		最多显示的选项数

样例：

<select name="num">
  	<option value="1">1</option>
  	<option value="2">2</option>
  	<option value="3">3</option>
	</select>

4、button类

​	普通按钮，具有提交功能。可以单独使用，不写在form元素中；如果写在form中，	有提交功能。

## 1.5. iframe框架集（尽量避免使用）

iframe:框架集，是用来将多个网页文件组合成一个文件。

​	常用属性：

​		name:框架名

​		src:引入的外部html文件

​		scrolling:滚动条(yes/no/auto)

​		width:宽度(%/px)

​		height:高度(%/px)

​		frameborder:是否有边框(1/0)

​		marginheight:框架离顶部和底端的距离(%/px)

​		marginwidth:框架离左右的距离(%/px)

注意：

在实际开发，尽量减少使用iframe，因为它破坏了前进和后退功能，且不利于SEO。

## 1.6. 文本格式化标签

文本格式化标签是用来美化文本的一类

<b>			粗体字
	<strong>	粗体字，与b不同的是strong表示强调，强调主要用于SEO引擎优化时				便于提取关键字，外观表现与b标签相同
	<i>			斜体字
	<em>		斜体字，同时也表示强调
	<pre>		定义预格式化的文本，被包含在pre标签元素中的文本通常会保留空格和				换行符，文本也会呈现为等宽字体
	<small>		小型文本
	<sub>		定义下标文本
	<sup>		定义上标文本

## 1.7. 转义字符

<		小于号
	>		大于号
	&	&号
	 空格
	©	版权符号 
	×	乘号（叉号）
	÷	除号

## 1.8. 网页布局标签

​	header:页首

​	nav:导航栏

​	aside:侧边栏

​	main:主体

​	section:区块

​	article:文章

​	footer:页尾

## 1.9. HTML5语义化标签

​	mark		高亮显示(行级)

​	details		描述标签，一般用于名词解释或用于封装一个区块等

summary	摘要标签，需要在details标签中才能使用

​	meter		能够度量给定范围内的数据比例，类似进度条，但不应作为进度条使用

​				属性：value/min/max

​	progress		进度条标签

​				属性：value/min/max

​	dialog		在网页中央显示一个对话框或窗口，兼容性较差

属性：open

​	figure		用于对元素进行组合（一般用来组合一张图的标题、图片和图片描述等）

## 1.10. HTML5多媒体标签

1、audio

​		播放音乐或音频。IE9以下的版本不支持。

​		1）支持的格式

​			.mp3/.ogg/.wav

​		2）属性

​			src:文件路径

​			autoplay:自动播放

​			loop:循环

​			controls:控制条

​			muted:静音

​			preload:预加载（当使用autoplay时，preload自动失效）

2、video

​		加载视频。IE9以下的版本不支持。

​		1）支持的格式

​			.mp4/.ogg/.webm

​		2）属性

​			src:文件路径

​			autoplay:自动播放

​			loop:循环

​			controls:控制条

​			muted:静音

​			preload:预加载（当使用autoplay时，preload自动失效）

​			width:宽度

​			height:高度

​			poster:海报

3、embed

​		嵌入内容或加载插件。

​		属性:

​			src:文件路径

​			width:宽度

​			height:高度

​			type:类型

4、canvas

​		画布标签，本质上是一个容器元素。

​		注意：

​			1）单独使用canvas没有什么意义，它必须结合Javascript使用。它的具体功能体			现是通过Javascript体现现来的。

​			2）canvas的宽高最好不要通过css实现，而是直接使用标签属性width和height			实现。

 

## 1.11. HTML5常用属性

1、contentEditable

​		将标签转换为可编辑状态。可用于所有标签。

属性值：true/false。

2、hidden

​		对元素进行隐藏。一般用来传值或当某个条件成立，执行内容显示。默认值为hidden。

3、data-*

​		自定义属性，一般用于传值。

4、multiple

​		规定输入域中可选择多个内容。用于表单元素中，如file/select。

5、required

​		约束表单元互在提交前必须输入值。用于表单组件中，需要结合提交按钮使用。

6、pattern

​		用于验证输入字段的模式。用于表单组件中，需要结合提交按钮使用。

## 1.12. HTML5表单

### **1.12.1.** ***\*input新属性\****

​	1、autocomplete:自动完成

​		用来帮助用户输入，每一次输入的内容，浏览器是否保存输入的值，以备将来使用。		属性值：on/off，默认为on。

​		为了保护敏感数据（如用户帐号、密码等），避免本地浏览器对它们不安全存储，一		般需要关闭。

​	2、autofocus:自动获焦

​	3、step:步长

​	4、multiple:多选

​	5、pattern:正则匹配

​	6、placeholder:输入提示

​	7、required:必须输入

 

### **1.12.2.** ***\*input新增type属性\****

​	1、color	拾色器

​	2、email	输入邮箱

​	3、tel		输入电话号码

​	4、url		输入网址

​	5、number	数字

​	6、range	范围

​	7、search	搜索

​	8、date		选择日期

​	9、datetime	选择日期时间

​	10、datetime-local	本地日期时间

​	11、year	选择年份

​	12、month	选择月份

​	13、time	选择时间

### **1.12.3.** ***\*表单属性\****

​	1、formaction:修改action数据提交的地方

​	2、formenctype:修改表单请求的类型

​	3、formmethod:修改数据提交的方法

​	4、form:设置表单元素属于哪个表单

​	5、novalidate:不验证

## 1.13. 代码规范

### **1.13.1.** ***\*常见规范\****

1、定义语言编码
		<meta charset=”utf-8”/>
	2、JavaScript定义
		<script language=”javascript” type=”text/javascript”>
			脚本代码...
		</script>
	3、css定义
		<style type=”text/css”>
			样式设置...
		</style>
		为保证各个浏览器的兼容性，在写css时请带上单位
	4、不要在注释内容中使用“--”
	5、所有的标签和属性的名字都必须用小写
	6、所有的属性值必须用双引号引起来
	7、如果文档中要输出<,>和&等，请使用实体转义符实现
	8、属性要么不写，要么就要给所有的属性赋一个值，否则如果没赋值，默认它的值就是		属性名本身
	9、所有的标签都必须要有一个相应的结束标记（标签必须要闭合），尤其是单标签
	10、所有的标签必须合理嵌套，不能出现嵌套交叉情况
	11、图片要添加有意义的alt属性
	12、在form表单中增加label标签，增加用户的体验度

 

### **1.13.2.** ***\*标签嵌套规则\****

1、块级元素可以包含内联元素和某些块级元素，但内联元素却不能包含块级元素，它只		能包含其他内联元素

2、块级元素禁止放入p标签内

3、有几个特殊的块级元素只能包含内联元素，不能再包含块级元素

这几个特殊的标签是：hx类标签，p标签、dt标签 

4、块级元素与块级元素并列，行内元素与行内元素并列，不允许块元素和行元素并列

 

### **1.13.3.** ***\*块级元素和行级元素列表\****

块级元素：

div、p、hx、ul、ol、dl、li、dd、table、hr、blockquote、address、menu、pre、header、section、aside、footer

行内元素：

span、img、a、label、input、abbr（缩写）、button、em等格式化标签...

img实际上属于行级块标签，相当于执行了display:inline-block

 

### **1.13.4.** ***\*HTML语义化标签\****

含义：明白每个标签的用途

优点：

1、更容易被搜索引擎收录

2、更容易让屏幕阅读器读出网页内容

3、能够更好的体现页面的主题

4、兼容性更好，支持更多的网络设备

类型：

<a>		超链接，可以用title属性显示提示内容	<p>		文章段落	<hx>	文章标题	<strong>和<em>		强调，em斜体，strong粗体	<q>		引用，浏览器会对q标签引用内容自动添加双引号	<address>	为网页加入地址信息或者联系方式等	<ul>	无序列表

<ol>	有序列表
	<caption>	为表格添加标题和摘要，摘要的内容不会再浏览器中呈现，作用是增加表格的可读性（语义化）

## 1.14. 项目结构搭建

### **1.14.1.** ***\*文件和目录准备（以小兔鲜为例）\****

1.新建项目文件夹xtx-pc-client，在编辑器中打开

注意：

在实际开发中，项目文件夹不建议使用中文

所有项目相关文件都保存在xtx-pc-clien目录中

2.复制favicon.ico到xtx-pc-client目录

注意：一般习惯将ico图标放在项目根目录

3.复制images、uploads和lib目录到xtx-pc-clien目录中

注意：

images：存放网站固定使用的图片素材，如logo、样式修饰图片等

uploads：存放网站非固定使用的图片素材，如：商品图片、宣传图片等

lib：存放网站使用的模板或者引入的外部文件、框架、库等

4.新建index.html在根目录

5.新建css文件夹保存网站样式，并新建以下css文件：

base.css：基础公共样式，里面保存着默认样式

common.css：该网站中多个网页相同模块的重复样式，如头部、底部

index.css：首页样式

### **1.14.2.** ***\*企业官网文件命名规范\****

项目开发时，项目中文件或目录名中不能出现汉字和空格之类的其他字符，文件和目录名一般以字母或下划线开头，其后可以出现字母数字或者下划线，切记不可出现空格

几种常用目录名：

产品目录	xxxxx(产品名)pro

图片文件目录	images/img/pic

视频	video

音频	music

文件工程	file

几种常用文件名

首页	index.html（必须是这个）

订单页 order.html

公司介绍 about.html

新闻列表 news.html

新闻详情页news_details.html

产品列表 product.html

产品详情页pro_details.html

联系我们 contact.html

 

## 1.15. web字体引入

​	开发者引入外部字体。

​	语法：

​		@font-face {

​			font-family: 字体名;

​			src: url("字体文件.ttf") format("字体文件格式以处理浏览器兼容"),url(字体文件.woff) format(...),...;

​		}

​	说明：

​		可以同时引入多个字体文件，字体一样，文件的扩展名不一样，目的是为了处理浏览器兼容。