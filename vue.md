# vue篇

## webpack

### 前端工程化

#### 实际工作中的前端开发

模块化（js的模块化、css的模块化、资源的模块化）

组件化（复用现有的UI结构、样式、行为）

规范化（目录结构的划分、编码规范化、接口规范化、文档规范化、Git分支管理）

自动化（自动化构建、自动部署、自动化测试）

#### 前端工程化

前端工程化指的是在企业级的前端项目开发中，把前端开发所需的工具、技术、流程、经验等进行规范化、标准化。

企业中的vue项目和react项目都是基于工程化的方式进行开发的

前端工程化的好处：前端开发自成体系，有一套标准的开发方案和流程

#### 前端工程化的解决方案

早期的前端工程化解决方案（了解即可）

grunt、gulp

目前主流的前端工程化解决方案

webpack（https://www.webpackjs.com）

parcet（https://zh.parcetjs.org）

### webpack的基本使用

#### 什么是webpack

webpack是前端项目工程化的具体解决方案

主要功能：提供了友好前端模块化开发支持以及代码压缩混淆、处理浏览器端JavaScript的兼容性、性能优化等功能

好处：让程序员将工作中心放到具体功能的实现上，提高了前端开发效率和项目的可维护性

注意：目前vue、react等前端项目，基本都是基于webpack进行工程化开发的

#### 项目初始化步骤

1、新建项目空白目录，运行npm init -y命令，初始化包管理配置文件package.json

2、新建src源代码目录

3、在src中新建index.html和index.js文件

4、初始化首页基本的结构

5、运行npm i jquery -s命令，安装jQuery（-s即--save表示明确告诉npm需要将包的参数记录到package.json文件中）

6、通过ES6模块化的方式导入jq，实现列表隔行变色

ES6方法：import $ from ‘jquery’

##### webpack安装以及配置

###### 安装webpack

在终端中运行如下命令，安装webpack相关的两个包

npm install [webpack@5.42.1](mailto:webpack@5.42.1) [webpack-cli@4.7.2](mailto:webpack-cli@4.7.2) -D

```
npm install webpack@5.42.1 webpack-cli@4.9.0 -D
```

-D是--save-dev的缩写，表示将包记录到devDependencies节点中（即只在开发阶段用到的包）

-S是--save的缩写，表示将包记录到Dependencies节点中（在开发和部署阶段用到的包）

###### 在项目中配置webpack

1）在项目根目录中，创建名为`webpack.config.js`的webpack配置文件，并初始化如下的基本配置：

```
modul.exports = {
	mode:'development'	// mode 用来指定构建模式
}
```

> mode的可选值有两个，分别是：
>
> 1. development
>    - 开发环境
>    - 不会对打包生成的文件进行代码压缩和性能优化
>    - 打包速度快，适合在开发阶段使用
> 2. production
>    - 生产环境
>    - 会对打包生成的文件进行代码压缩和性能优化
>    - 打包速度很慢，仅适合在项目发布阶段使用
>
> 因此一定要视情况选择mode的值

> webpack.config.js是webpack的配置文件。webpack在真正开始打包构建之前，会先读取这个配置文件，从而基于给定的配置对项目进行打包
>
> 由于webpack是基于node.js开发出来的打包工具，因此在它的配置文件中，支持使用node.js相关的语法和模块进行webpack的个性化配置

2）在pack.json的scripts节点下，新增dev脚本如下：

```
“scripts":{
	"dev":"webpack"	// script节点下的脚本可以通过npm run执行，例如npm run dev，dev只是一个代码，可以更改，但是后面的webpack字符串不能改，因为运行这串代码即表示你利用webpack打包
}
```

使用`npm run dev`后在根目录下就会生成相关的文件，生成的文件既包含了源文件，还包含了被导入的包的内容

###### 自定义webpack打包的入口与出口

> 在webpack 4.x 和 5.x 的版本中，有如下的默认约定
>
> 1. 默认的打包入口文件为 src->index.js
> 2. 默认的输出文件路径为 dist->main.js
>
> 如果webpack找不到打包入口文件则会报错
>
> 可以在webpack.config.js中修改打包的默认约定

在webpack.config.js配置文件中，通过entry节点指定打包的入口。通过output节点指定打包的出口

```javascript
const path = require('path')

module.exports = {
	entry: path.join(__dirname, './src/入口文件名.js'),
	output: {
		path:path.join(__dirname, './dist'),	// 指定输出文件的存放路径
        // 一般将该文件保存到dist文件夹下的js文件夹中
		filename: './js/输出文件的名称.js'
	}
}
```

### 安装webpack中的插件

通过安装和配置第三方的插件，可以拓展webpack的能力，从而让webpack用起来更方便。最常用的webpack插件有如下两个：

1. webpack-dev-server
   - 类似于node.js阶段用到的nodemon工具
   - 每当修改了源代码，webpack会自动进行项目的打包和构建
2. html-webpack-plugin
   - webpack中的html插件（类似于一个模板引擎插件）
   - 可以通过此插件复制index.html到一个新的地址
3. clean-webpack-plugin
   - 该插件能够使webpack在每次打包的时候自动清理调dist目录中的旧文件
   - webpack5可以直接设置clean: true

##### webpack-dev-server

- 安装webpack-dev-server

运行如下命令，即可在项目中安装插件：

```
npm install webpack-dev-server@3.11.2 -D 
```

- 配置webpack-dev-server

1. 修改package.json -> scripts 中的dev命令如下

```
"scripts": {
	"dev": "webpack serve"
}
```

2. 再次运行`npm run dev`命令，重新进行项目的打包
3. 在浏览器中访问`http://localhost:8080`地址，然后进入src文件夹可以查看js的自动打包对网页造成的效果

> 打开网页中的文件夹会默认进入该文件夹中的index.html页面

> webpack-dev-server会在根目录生成一个输出文件，但是该文件是被存放在内存中的，便于修改，也避免频繁读写磁盘对磁盘造成损坏，并不会直接显示在文件夹或者网页中，但是你可以通过`http://localhost:8080/输出文件名.js`的url查看该文件

> webpack-dev-server并不是在本地打包，而是启动一个实时打包的http服务器在内存中进行模拟打包

- devServer节点

在webpack.config.js配置文件中，可以通过devServer节点对webpack-dev-server插件进行更多的配置

```
devServer: {
	open: true,	// 初次打包完成后，自动打开浏览器
	host: '127.0.0.1',	// 实时打包所使用的的主机地址
	port: 8080,	// 实时打包所使用的的端口号
}
```

> 该节点还是写在module.exports对象中
>
> 凡是修改了webpack.config.js配置文件或者package.json配置文件，必须重启实时打包的服务器，否则最新的配置文件无法生效

##### html-webpack-plugin

- 安装html-webpack-plugin

运行如下命令，即可在项目中安装插件：

```
npm install html-webpack-plugin@5.3.2 -D 
```

- 配置html-webpack-plugin

在webpack.config.js中配置如下信息

```
// 导入HTML插件，得到一个构造函数
const HtmlPlugin = require('html-webpack-plugin')

// 创建HTML插件的实例对象
const htmlPlugin = new HtmlPlugin({
	template: './src/index.html',// 指定源文件的存放路径
	filename: './index.html'	// 指定生成文件的存放路径
})

module.exports = {
	mode: 'development',
	plugins:[htmlPlugin]	// 通过plugins节点使htmlPlugin插件生效，注意这个节点中的p是小写的，最后有s，否则会报错
}
```

> 这个插件也是将复制的页面存到内存中的，并不会真实复制

该插件既会帮我们复制页面，也会帮我们自动引入内存中的输出文件（上个插件输出的）

##### clear-webpack-pilugin

- 安装clean-webpack-plugin

```
npm i clean-webpack-plugin@3.0.0 -D
```

- 在webpack.config.js中配置插件

```
// 导入插件，得到一个构造函数
const {CleanWebpackPlugin} = require('clean-webpack-plugin')

// 创建HTML插件的实例对象
const cleanPlugin = new CleanWebpackPlugin()

module.exports = {
	mode: 'development',
	plugins:[cleanPlugin]	// 通过plugins节点使插件生效
}
```

### webpack中的loader

#### loader概述

- 背景

在实际开发过程中，webpack默认只能打包处理以.js后缀名结尾的模块。其他的非.js后缀名结尾的模块，webpack默认处理不了，需要调用loader加载器才可以正常打包，否则会报错

- loader的作用

协助webpack打包处理特定的文件模块，例如

1. css-loader可以打包处理.css相关的文件
2. less-loader可以打包处理.less相关的文件
3. babel-loader可以打包处理webpack无法处理的高级JS语法
4. url-loader可以打包处理样式表中与url路径相关的文件（例如jpg、png、gif）

![image-20220406212112873](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20220406212112873.png)

> 注意：在webpack中，一切皆模块，都可以通过ES6导入语法进行导入和使用，因此我们可以在js文件中使用`import './css/index.css'`语句导入样式，也可以使用`import logo from './logo.jpg'`语句引入图片，这里logo的值是图片路径
>
> 注意：当在js中引入css样式后，如果直接使用webpack打包该js会报错，需要使用css-loader进行加载

#### 如何使用loader

- 安装loader

```
// 安装css加载器，注意，一共有两个，style-loader和css-loader
npm i style-loader@3.0.0 css-loader@5.2.6 -D

// 安装less加载器，注意，之所以安装后面的less是因为less加载器依赖于less运行的，所以必须先加载该环境
npm i less-loader@10.0.1 less@4.1.1 -D

// 安装url路径相关加载器，file-loader也是一个内置依赖项，在下面也不需要导入
npm i url-loader@4.1.1 file-loader@6.2.0 -D

// 安装高级js加载器，注意后两个是依赖
npm i babel-loader@8.2.2 @babel/core@7.14.6 @babel/plugin-proposal-decorators@7.14.5 -D
```

- 配置loader

在webpack.config.js的module.exports->module->rule数组中，添加loader规则如下

> webpack会在处理不了文件时查看该数组判断是否配置了对应的loader加载器

```
module.exports = {
	module:{
        rules:[	// 文件后缀名的匹配规则
            {
                test: /\.css$/,
                use: [
                	// css加载器
                    'style-loader',
                    'css-loader',
                ]
            },
            {
                test: /\.less$/,
                use: [
                	// 注意此处三个加载器都必须运行，因为less会转化成css，还需要css加载器进行解析
                    'style-loader',
                    'css-loader',
                    'less-loader'
                ]
            },
            {
            	// 除了下面三种类型，还可以是其他的图片类型
                test: /\.jpg|png|gif$/,
                use: ['url-loader'],
                // options中的内容也可以在use中改为查询字符串的形式，例如use: ['url-loader?limit=22229&outputPath=images']
                options:{
                	// 限定图片转化大小，单位是字节，只有大小不大于这个限制的才会被转化为base64格式
                	limit=22229,
                	// 指定图片文件的输出路径，此时该路径为dist/image/
                	outputPath:'images'
                }
            },
            {
                test: /\.js$/,
                use: ['babel-loader'],
                // 注意：必须使用exclude指定排除项，因为node_modules目录下的第三方包不需要被打包且兼容性不需要我们关心
                exclude: /node_modules/
            }
        ]
    }
}
```

> 注意rules是写在module.exports->module中！！！不是写在module.exports或者module中！！！
>
> test表示匹配的文件类型，use表示对应要调用的loader
>
> url-loader加载器的原理是将图片文件转化成base64字符串
>
> 注意：base64一般会比原图片大，因此只推荐小图片使用，大图片不推荐使用，可以用limit进行限制
>
> 注意：
>
> 1. use数组中指定的loader顺序是固定的
> 2. 多个loader的调用顺序是**从后往前**调用
> 3. 每个loader处理完文件后，会将文件转交给下一个loader
> 4. 当所有文件都被处理好后，webpack会把style-loader处理的结果合并到输出文件中，最终生成打包好的文件

- 配置babel-loader

在项目根目录下创建名为babel.config.js的配置文件，定义babel的配置项如下：

```
module.exports = {
	plugins:[['@babel/plugin-proposal-decorators',{legacy:true}]]
}
```

### 打包发布

#### 为什么要打包发布

项目开发完成后，需要使用webpack对项目进行打包发布，主要原因如下：

1. 开发环境下，打包生成的文件存放于内存中，无法获取到最终打包生成的文件
2. 开发环境下，打包生成的文件不会进行代码压缩和性能优化

为了让项目能够在生产环境中高性能的运行，因此需要对项目进行打包发布

#### 配置webpack的打包发布

在packagejson文件的scripts节点下，新增build命令如下

```
"scripts": {
    // 开发环境中执行dev命令即可
    "dev": "webpack serve",
    // 项目发布时运行build命令
    "build": "webpack --mode production"
},
```

> --mode是一个参数项，用来指定webpack的运行模式。production代表生产环境，会对打包生成的文件进行代码压缩和性能优化
>
> 注意：通过--mode 指定的参数项，会覆盖webpack.config.js中的mode选项

#### 企业级项目的打包发布

企业级项目的打包发布流程为：

1. 生成打包报告，根据报告分析具体的优化方案
2. Tree-Shaking
3. 为第三方库启用CDN加载
4. 配置组件的按需加载
5. 开启路由懒加载
6. 自定制首页内容

> 更多的内容见项目

### Source Map

#### 什么是Source Map

Source Map就是一个信息文件，里面储存着位置信息，也就是说Source Map文件中存储这压缩混淆后的代码所对应的转换前的位置

有了它，在出错的时候出错工具将直接显示原始代码，而不是转化后的代码，能够极大的方便后期的调试

#### 默认Source Map的问题

开发环境下默认生成的Source Map，记录的是生成后代码的位置，会导致运行时报错的行数与源代码的行数不一致的问题

#### 解决默认Source Map的问题

开发环境下，推荐在webpack.config.js中添加如下的配置，即可保证运行时报错的行数与源代码的行数保持一致

```
module.exports = {
	mode: 'development',
	devtool: 'eval-source-map'
}
```

> 注意：在发布项目的时候处于安全考虑要关掉该选项

在生产环境下，如果只想定位报错的具体行数而不暴露源码。此时可以将devtool的值设置为`nosources-source-map`

> 采用此选项后：应该将服务器配置为不允许普通用户访问source map文件



在生产环境下，如果定位报错的具体行数且暴露源码。此时可以将devtool的值设置为`source-map`

### 小拓展

建议使用@符号表示src源代码目录，从外往里查找，不要使用../从里往外查找

> 注意：虽然@好用，但是必须先在webpack.config.js中配置，配置方式见下

```
module.exports = {
	resolve: {
        alias: {
        	// 告诉webpack，程序员写的代码中@符号表示src这一层目录
            '@': path.join(__dirname, './src')
        }
    }
}
```

### 实际开发中不需要自己配置webpack！！！

- 实际开发中会使用命令行工具意见生成带有webpack的项目
- 该项目开箱即用，所有的webpack配置项都是现成的
- 但是我们还是需要了解webpack中的基本概念

### 在chrome中安装vue-devtools调试工具

#### 安装vue-devtools

直接翻墙到谷歌商店里面下载吧，其他地方的经常报错

#### 配置插件

在插件中详情面板中（通过拓展管理进入），打开允许访问文件网址，即配置完成

## vue2.0

### vue简介

#### 什么是vue

vue是一套用于构建用户界面的前端框架

> 构建用户界面即用vue往html页面中填充数据，非常方便
>
> 框架是一套现成的解决方案，程序员只能遵守框架的规范去编写自己的业务功能，学习vue就是在学习vue框架中规定的语法

#### vue的特性

1. 数据驱动视图
   1. 在使用了vue的页面中，vue会监听数据的变化，从而自动重新渲染页面的结构
   2. 好处：当页面数据发生变化时，页面会自动重新渲染
   3. 注意：数据驱动视图时单向的数据绑定
2. 双向数据绑定
   1. 在填写表单时，双向数据绑定可以辅助开发者在不操作DOM的前提下，自动把用户填写的内容同步到数据源中
   2. 好处：开发者不再需要手动操作DOM元素来获取表单元素最新的值

#### MVVM

MVVM是vue实现数据驱动视图和双向数据绑定的核心原理

MVVM指的是Model、View和ViewModel，它把每个HTML页面都拆分成了这三个部分

在MVVM概念中：

Model表示当前页面渲染时所依赖的数据源

View表示当前页面所渲染的DOM结构

ViewModal表示vue的实例，它是MVVM的核心

#### MVVM的工作原理

ViewModel作为MVVM的核心，是它把当前页面的数据源（Modal）和页面的结构（View）连接在了一起

当数据源发生变化时，会被ViewModal监听到，VM会根据罪行的数据源自动更新页面的结构

当表单元素的值发生变化时，也会被VM监听到，VM会把变化过后最新的值自动同步到Model数据源中

### vue的基本使用

#### 基本使用步骤

1. 导入vue.js的script脚本文件
2. 在页面中声明一个将要被vue所控制的DOM区域
3. 创建vm实例对象

实例

```html
<body>
    <!--2、在页面中声明一个将要被vue所控制的DOM区域-->
    <div id="app">
        {{username}}
    </div>
    <script src="./vue路径"></script>
    <script>
        // 3、创建vm实例对象
    	const vm = new Vue({
            // 3.1、指定当前vm实例要控制页面的哪个区域，el属性是固定的写法，表示当前vm实例要控制页面上的哪一个区域，接受的值是一个选择器
            el: '#app',
            // 3.2、指定Model数据源，data对象就是要渲染到页面上的数据
            data: {
                username: 'zs'
            }
        })
    </script>
</body>
```



### vue的调试工具

略

### vue的指令与过滤器

#### 指令

##### 指令的概念

指令是vue为开发者提供的模板语法，用于辅助开发者渲染页面的基本结构

vue中的指令按照不同的用途可以分为如下6大类

1. 内容渲染指令
2. 属性绑定指令
3. 事件绑定指令
4. 双向绑定指令
5. 条件渲染指令
6. 列表渲染指令

> 指令是vue开发中最基础、最常用、最简单的知识点

##### 内容渲染指令

内容渲染指令是用来辅助开发者渲染DOM元素的文本内容的

常用的内容渲染指令有如下3个

- v-text
- {{}}
- v-html

###### v-text

- 用法示例

```vue
<div id="app">
    <p v-text="username"></p>
    <!--下方的性别会被覆盖-->
    <p v-text="gender">性别</p>
</div>

...	<!--其余配置见上-->
```

> v-text会将标签中原本的内容覆盖
>
> v-text无法渲染html标签，而是会直接渲染成普通字符串

###### {{}}

> vue提供的{{}}语法是专门用来解决v-text会覆盖默认文本内容的指令
>
> {{}}也无法渲染html标签，而是会直接渲染成普通字符串
>
> 插值表达式只能用于内容节点中，不能用于属性节点

这种{{}}语法的专业名称是**插值表达式**（Mustache）

使用方法略

###### v-html

> v-html指令是专门用来解决v-text指令和插值表达式只能渲染纯文本内容，无法渲染html标签的问题的

- 用法示例

```html
<div id="app">
    <p v-html="discription"></p>
</div>

<script src="..."></script>
<script>
	const vm = new Vue({
        el: "#app",	// 这个vm示例只会控制第一个匹配的标签
        data:{
            description:"<a>这是一个超链接</a>"
        }
    })
</script>
```

##### 属性绑定指令

如果需要为元素的属性动态绑定属性值，则需要使用`v-bind`属性绑定指令

> vue规定v-bind指令可以简写为:即可

- 用法示例

```html
<div id="app">
    <!--下面两种写法都允许，推荐第一种写法，更简洁-->
	<input type="text" :placeholder="tips"/>
	<input type="text" v-bind:placeholder="tips"/>
</div>
<script src="./lib/vue.js"></script>
<script>
	const vm = new Vue({
        el: "#app",	// 这个vm示例只会控制第一个匹配的标签
        data:{
            tips:"请输入"
        }
    })
</script>
```

> 指令除了直接使用外，还支持在指令中进行简单的运算或者使用JavaScript表达式的运算
>
> 例如：
>
> {{number+1}}、message.split('')、v-bind id="'list' + id"

##### 事件绑定指令

> vue提供了v-on:事件绑定指令，用来辅助程序员为DOM元素绑定事件监听
>
> v-on:可以简写为@

- 修改对象属性

在被绑定的事件中，可以使用`this.属性名`或者`vue对象名.属性名`的的方式查看或修改变量内容，其中第二种方式不推荐

- 事件传参

可以使用函数名(值)的形式传递参数

其中，如果没有传参的时候，函数默认有一个参数e，e中存放的是触发当前事件的dom元素，但如果传参了，则会覆盖e参数

> 如果不传参一定要写成add的形式，不能写成add()

可以在html中使用`$event`作为参数传入事件中，`$event`是vue提供的原生的DOM的事件对象

> $event在实际开发中并不是很常用

- 事件修饰符

vue提供了事件修饰符来使程序员更方便的对事件的触发进行控制

使用语法： `@事件名.prevent="需要绑定的函数"`

例如： `@click.prevent="add"`

常用的5个事件修饰符

| 事件修饰符 |                        说明                        |
| :--------: | :------------------------------------------------: |
|  .prevent  |    阻止默认行为(例如a标签的跳转，表单的提交等)     |
|   .stop    |                    阻止事件冒泡                    |
|  .capture  |          以捕获模式触发当前的事件处理函数          |
|   .once    |                绑定的事件只触发1次                 |
|   .self    | 只有在event.target是当前元素自身时触发事件处理函数 |

- 按键修饰符

vue提供了按键修饰符来监听键盘事件，使得我们不需要判断详细的按键

语法：`@keyup.esc="函数名"`表示用户输入了esc键时才触发该事件

> 连续使用多个按键修饰符为组合键功能

- 用法示例

```html
<div id="app">
    <p>
        count的值是：{{count}}
    </p>
    <!-- 不传参，一定要写成如下形式才有e参数，如果写成add()则不会有该参数-->
    <button @click="add(2,$event)">+1</button>
    <!--
	还可以写成如下形式
	<button v-on:click="add(2)">+1</button>
	-->
</div>


<script src="./lib/vue-2.6.12.js"></script>
<script>
	const vm = new Vue({
        el: "#app",	// 这个vm示例只会控制第一个匹配的标签
        data:{
            count:0
        },
        // methods的作用就是定义事件处理函数
        methods:{
            add:function(n, e){
                console.log(e)
                this.count+=n
                // vm.count+=n // 此方法不推荐
            }
            /*
            在ES6中还可以写成：
            add(n)
        	{
        		this.count+=n
    		}
    		*/
        }
    })
</script>
```

##### 双向绑定指令

vue提供了`v-model`双向数据绑定指令，用来辅助开发者在不操作DOM的前提下，快速获取表单的数据

> 注意：只有在表单元素中才能使用双向绑定
>
> 注意：select标签也是表单元素，双向绑定指令要绑定在select标签中，而不是绑定在option标签中，其值为option中value的值

- 修饰符

为方便对用户输入的内容进行处理，vue为v-model指令提供了3个修饰符，分别是

| 修饰符  |              作用              |
| :-----: | :----------------------------: |
| .number | 自动将用户的输入值转为字符类型 |
|  .trim  | 自动过滤用户输入的首位空白字符 |
|  .lazy  | 在“change"时而非"input"时更新  |

- 用法示例

```html
<div id="app">
    <p>用户的名字是：{{usename}}</p>
	<input type="text" v-model="username"/>
</div>
<script src="./lib/vue.js"></script>
<script>
	const vm = new Vue({
        el: "#app",	// 这个vm示例只会控制第一个匹配的标签
        data:{
            username:"张三"
        }
    })
</script>
```

##### 条件渲染指令

条件渲染指令用来辅助开发者按需控制DOM元素的显示与隐藏。条件渲染指令有如下两个：

1. v-if
2. v-show

v-if具有配套指令`v-else-if`和`v-else`，具体用法略

> v-show的原理是动态为元素添加display：none样式来实现元素的显示和隐藏
>
> v-if的原理是每次动态创建或移除元素，来实现元素的显示和隐藏
>
> 如果要频繁切换元素的显示状态用v-show更好
>
> 如果刚进入页面的时候，某些元素默认不需要被展示，而且后期这个元素很可能也不需要被展示，此时v-if性能更好

- 用法示例

```html
<div id="app">
    <p v-if="test === 200">显示</p>
	<p v-show="test === 200">显示</p>
</div>
<script src="./lib/vue.js"></script>
<script>
	const vm = new Vue({
        el: "#app",	// 这个vm示例只会控制第一个匹配的标签
        data:{
            test: 200
        }
    })
</script>
```

##### 列表渲染指令

vue提供了v-for列表渲染指令，用来辅助开发者基于一个数组来循环渲染一个列表结构

v-for指令需要使用item in items形式的特殊语法，其中

1. items是待循环的数组
2. item是被循环的每一项

> v-for指令还支持一个可选的第二个参数，即当前项的索引项，语法为(item, index) in items
>
> 注意index是从0开始的
>
> item和index还可以在属性中使用

> 官方建议：只要用到了v-for指令，那么一定要绑定一个`:key`属性，而且尽量把id作为key的值

- key值的注意事项

1. key的值只能是字符串或数字类型
2. key的值必须具有唯一性
3. 建议把数据项id属性的值作为key值（因为id属性值具有唯一性）
4. 使用index的值当做key没有任何意义（因为index的值不具有唯一性，唯一性指的不是不重复，而是值和内容有一个强制绑定关系）
5. 使用v-for指令时一定要指定key的值（既能提升性能，又能防止列表状态紊乱（主要在于状态更新的时候能够绑定更新状态）

- 用法示例

```html
<ul id="app">
    <li v-for="(item, index) in list" :key="item.id">第{{index}}个名字是{{item.name}}</li>
</ul>
<script src="./lib/vue.js"></script>
<script>
	const vm = new Vue({
        el: "#app",	// 这个vm示例只会控制第一个匹配的标签
        data:{
            list: [
            {
                id:1,
                name:"zs"
            },{
                id:2,
                name:"ls"
            },{
                id:3,
                name:"ww"
            }]
        }
    })
</script>
```

