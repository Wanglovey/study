## React基础

### React概述

#### React是什么

React是一个用于构建用户界面的JavaScript库

> 用户界面即HTML页面(前端)

如果从MVC的角度来看，React仅仅是视图层(V)，也就是只负责视图的渲染，而并非是提供了完整的M和C的功能

#### React特点

- 声明式
  - 你只需要描述UI(HTML)看起来是什么样，就跟写HTML一样
- 基于组件
  - 组件是React最重要的内容
  - 组件表示页面中的部分内容
  - 组合、复用多个组件，可以实现完整的页面功能
- 学习一次，随处使用
  - 使用React可以开发Web应用
  - 使用React可以开发移动端原生应用(react-native)
  - 使用React可以开发VR应用(react 360)

### React的基本使用

#### React的安装

安装命令

```
npm i react react-dom
```

- react 包是核心，提供创建元素、组件等功能
- react-dom包提供DOM相关功能

#### React的使用

1. 引入react和react-dom两个js文件

```html
<script src="./node_modules/react/umd/react.development.js"></script>
<script src="./node_modules/react-dom/umd/react-dom.development.js"></script>
```

2. 创建React元素
3. 渲染React元素到页面中

```html
<div id="root"></div>
<script>
    // 创建react元素
    // 参数一：元素名称
    // 参数二：元素属性
    // 参数三及其之后参数：元素的子节点
    const title = React.createElement('h1', null ,'Hello React')
    
    // 渲染react元素
    // 参数一：要渲染的 react 元素
    // 参数二：挂载点
    ReactDOM.render(title, document.getElementById('root'))
</script>
```

#### 方法说明

1. React.createElement()
   - 返回值: React元素
   - 第一个参数：要创建的React元素名称
   - 第二个参数：该React元素的属性
   - 第三个及其以后的参数：该React元素的子节点
   - 注意：这个方法仅需了解即可，JSX可以替代此方法
2. ReactDOM.render()
   - 第一个参数：要渲染的 react 元素，也可以是组件元素
   - 第二个参数：DOM对象，用于指定渲染到页面中的位置

### React脚手架的使用

#### React脚手架意义

1. 脚手架是开发现代Web应用的必备
2. 充分利用Webpack、Babel、ESLint等工具辅助项目开发
3. 零配置，无需手动配置繁琐的工具即可使用
4. 关注业务，而不是工具配置

#### 使用React脚手架初始化项目

1. 初始化项目

```
npx create-react-app my-app		// 推荐使用
// 或
npm init react-app my-app
// 或
yarn create react-app my-app
```

2. 启动项目，在项目根目录执行命令

```
npm start
```

> 注意，要在项目根目录执行

##### npx命令介绍

npx是npm v5.2.0引入的一条命令，目的是提升包内提供的命令行工具的使用体验

即原来需要先全局安装脚手架，然后再使用这个包中提供的命令，而有了npx后无需安装脚手架包就可以直接使用这个包提供的命令

##### yarn

- yarn是Facebook发布的包管理器，可以看做是npm的替代品，功能与npm相同

- yarn具有快速、可靠和安全的特点
- 初始化新项目 `yarn init`
- 安装包 `yarn add 包名称`
- 安装项目依赖项 `yarn`
- 其他命令请参考yarn文档

#### 在脚手架中使用React

1. 在index.js文件中导入react和react-domo两个包

```
import React from 'react'
import ReactDOM from 'react-dom'
```

2. 调用React.createElement()方法创建react元素

```
const title = React.createElement('h1', null, 'Hello React')
```

3. 调用ReactDOM.render()方法渲染react元素到页面中
   - 注意：ReactDOM是Web应用才导入的，如果做移动端应用应该导入其他包

```
ReactDOM.render(title, document.getElementById('root'))
```

## JSX

### JSX的基本使用

#### createElement()的问题

1. 繁琐不简洁
2. 不直观
3. 不优雅，用户体验不好

#### JSX简介

JSX是JavaScript XML的简写，表示在JavaScript代码中写XML(HTML)格式的代码

优势：声明式语法更加直观、与HTML结构相同，降低学习成本、提升开发效率

==JSX是React的核心内容==，React完全利用JS语言自身的能力来编写UI，而不是造轮子增强HTML功能

#### 使用步骤

1. 使用JSX语法创建react元素

```html
// 使用JSX语法创建react元素
const title = <h1>Hello JSX</h1>
```

2. 使用ReactDOM.render()方法渲染react元素到页面中

```
// 渲染创建好的React元素
ReactDOM.render(title, document.getElementById('root'))
```

#### 为什么脚手架中可以使用JSX语法

1. JSX不是标准的ECMAScript语法，它是ECMAScript的语法拓展
2. 需要使用babel编译处理后才能在浏览器环境中使用
3. create-react-app脚手架中已经默认有babel配置，无需手动配置
4. 编译JSX语法的包为 `@babel/preset-react` 

#### 注意点

1. React元素的属性名使用驼峰命名法
2. 特殊属性名： class -> className 、 for -> htmlFor 、 tabindex -> tabIndex
3. 没有子节点的React元素可以用 `/>` 结束
4. 推荐使用小括号包裹JSX，从而避免JS中的自动插入分号陷阱

```jsx
const title = (
	<h1>Hello JSX</h1>
)
```

### JSX中使用Javascript表达式

#### 嵌入JS表达式

- 数据是存储在JS中的
- 语法：`{ JavaScript表达式 }`
- 注意：
  1. 该表达式的语法是单大括号，而不是双大括号(插值表达式)
  2. 单大括号中可以使用任意的JavaScript表达式
     - JS中的对象是一个例外，对象一般只会出现在style属性中
     - 不能出现语句(例如：if/for等)，但是可以用函数代替
  3. ==JSX自身==也是JS表达式

```jsx
const name = 'Jason'
const title = <h1>Hello, {name}</h1>
ReactDOM.render(title, document.getElementById('root'))
```

### JSX的条件渲染

#### 什么是条件渲染

条件渲染即根据条件渲染特定的JSX结构

```jsx
let isLoading = true
const loadData = () => {
	if(isLoading) {
		return <div>数据加载中，请稍后...</div>
	}
    return <div>数据加载完成，此处显示加载后的数据</div>
}

const dv = (
	<div>
    	{ loadData() }
    </div>
)
```

可以使用 `if/else` 或 `三元运算符` 或 `逻辑与运算符` 来实现

```jsx
let isLoading = true
const loadData = () => {
    return isLoading && <div>数据加载完成，此处显示加载后的数据</div>
}

const dv = (
	<div>
    	{ loadData() }
    </div>
)
```

### JSX的列表渲染

- 在JSX中如果要渲染一组数据应该是用数组的map()方法
- 注意：渲染列表时应该添加key属性，key属性的值要保证唯一
- 原则：map()遍历谁，就给谁添加key属性
- 注意：尽量避免使用索引号作为key

```jsx
const songs = [
  { id: 1, name: 'test1' },
  { id: 2, name: 'test2' },
  { id: 3, name: 'test3' }
]

const list = (
  <ul>
    { songs.map(item => (
      <li>{item.name}</li>
    )) }
  </ul>
)
```

### JSX的样式处理

1. 行内样式——style

   - ```jsx
     <h1 style={ { color: 'red', backgroundColor: 'skyblue'} }>
     	JSX的样式处理
     </h1>
     ```

2. 类名——className( 推荐 )

   - 引入CSS文件
   - 在标签中使用className

## React组件基础

### React组件介绍

- 组件是React的一等公民，使用React就是在使用组件
- 组件表示页面中的部分功能
- 组合多个组件实现完整的页面功能
- 特点
  - 可复用
  - 独立性
  - 可组合

### React组件的两种创建方式

#### 使用函数创建组件

##### 函数组件

- 使用JS的函数(或箭头函数)创建的组件

- 约定1：函数名称必须以大写字母开头，React据此区分 组件 和 普通React元素

- 约定2：函数组件==必须有返回值==，表示该组件的结构
- 如果返回值为 `null` ，表示不渲染任何内容

```jsx
function Hello() {
	return (
		<div>这是一个函数组件</div>
	)
}
// 或
const Hello = () => <div>这是一个函数组件</div>
```

##### 渲染函数组件

- 使用==函数名==作为组件标签名即可渲染函数组件
- 组件标签可以是单标签也可以是双标签

```
ReactDOM.render(<Hello />, documnet.getElementById('root'))
```

#### 使用类创建组件

- 类组件：使用ES6的class 创建的组件
- 约定1：类名称也必须以大写字母开头
- 约定2：类组件应该继承 `React.Component` 父类，从而可以使用父类中提供的方法或属性
- 约定3：类组件必须提供 `render()` 方法
- 约定4：`render()` 方法必须有返回值，表示该组件的结构

```jsx
class Hello extends React.Component {
	render() {
		return <div>Hello Class Component!</div>
	}
}
ReactDOM.render(<Hello />, root)
```

##### 将组件抽离为独立JS文件

组件作为一个独立的个体，一般都会放到一个独立的JS文件中

1. 创建Hello.js
2. 在Hello.js中导入React
3. 创建组件(函数 或 类)
4. 在Hello.js中导出该组件
5. 在index.js中导入Hello组件

```jsx
// Hello.js
import React from 'react'
class Hello extends React.Component {
    render () {
        return <div>Hello Class Component</div>
    }
}
// 导出Hello组件
export default Hello
```

### React事件处理

#### 事件绑定

- React事件绑定语法与DOM事件语法相似，直接在标签上绑定事件即可
- 语法： `on+事件名称={事件处理函数}` ，例如： `onClick={() => {}}`
- 注意：React事件采用==驼峰命名法==，例如： onMouseEnter、onFocus
- 在函数组件中绑定事件

```jsx
const Myevent = () => {
  function handleClick() {
    console.log('单击事件被触发了')
  }

  return <button onClick={handleClick}>test</button>
}
```

> 注意：如果是在类组件中进行绑定，则需要使用this进行指向

#### 事件对象

- 可以通过事件处理程序的参数获取到事件对象
- React中的事件对象叫做：合成事件(对象)
- 合成事件: 兼容所有浏览器，无需担心跨浏览器兼容性问题
- 

```jsx
const Myevent = e => {
  function handleClick() {
    console.log('单击事件被触发了', e)
  }

  return <button onClick={handleClick}>test</button>
}
```

### 有状态组件和无状态组件

- 函数组件又叫做无状态组件，类组件叫做有状态组件
- 状态(state)即数据
- 函数组件没有自己的状态，只负责数据展示(静态数据展示)
- 类组件有自己的状态，负责更新UI，让页面动起来

### 组件中的 `state` 和 `setState()`

#### state的基本使用

- 状态(state)即数据，是主键内部的==私有==数据，只能在组件内部使用
- state的值是对象，表示一个组件中可以有多个数据
- 获取状态 `this.state.具体数据名` 
- 可以使用setState()修改状态
  - 状态是可变的
  - 语法：this.setState({要修改的数据})
  - 注意：不要直接修改state中的值
  - setState()作用：
    1. 修改state
    2. 更新UI
  - 思想：数据驱动视图

```jsx
class Hello extends React.Component {
  constructor() {
    super() // ES6中class要求必须要有super()
    // 初始化state
    this.state = {
      count: 0
    }
  }
  render() {
    return (
      <div>
        <div>计数器：{this.state.count}</div>
        <button
          onClick={() => {
            this.setState({
              count: this.state.count + 1
            })
          }}
        ></button>
      </div>
    )
  }
}
// 或者
class Hello extends React.Component {
    // 简化语法
	state = {
        count: 0
    }
    render() {
        return (
        	<div>计数器：{this.state.count}</div>
            <button onClick={()=>{
                    this.setState({
                        count: this.state.count + 1
                    })
                }}></button>
        )
    }
}
```

#### 从JSX中抽离事件处理程序

- JSX中掺杂过多的JS逻辑代码会显得非常混乱
- 推荐将逻辑抽离到单独的方法中，保证JSX结构清晰
- 注意：将事件处理程序抽离出来后this的指向会改变，指向当前所属的函数(注意箭头函数不会修改this指向)，因此需要对this的指向进行处理
- 我们希望this指向组件实例(render方法中的this即为组件实例)

### 事件绑定this指向

#### 箭头函数

- 利用箭头函数自身不绑定this的特点，外部环境中的this是谁，箭头函数中的this就是谁
- 由于render()方法中的this为组件实例，因此在render()方法中使用箭头函数可以直接使用this获取setState()

#### Function.prototype.bind()

- 利用ES5中的bind方法，将事件处理程序中的this与组件实例绑定到一起

```jsx
class Hello extends React.Component {
  constructor() {
    super()

    this.onIncrement = this.onIncrement.bind(this) // 将当前的this绑定到事件内部的this中
    this.state = {
      count: 0
    }
  }

  onIncrement(e) {
    this.setState({
      count: this.state.count + 1
    })
  }
  render() {
    return (
      <div>
        <div>计数器：{this.state.count}</div>
        <button onClick={this.onIncrement}>test</button>	// 注意此种写法调用函数时，函数不能有括号，否则会报错
      </div>
    )
  }
}
```

#### class的实例方法(推荐使用)

- 利用箭头函数形式的class实例方法
- 注意：该语法是实验性语法，但是由于babel的存在可以直接使用

```
class Hello extends React.Component {
  constructor() {
    super()
    this.state = {
      count: 0
    }
  }

  onIncrement = (e) => {
    this.setState({
      count: this.state.count + 1
    })
  }
  render() {
    return (
      <div>
        <div>计数器：{this.state.count}</div>
        <button onClick={this.onIncrement}>test</button>	// 注意此种写法调用函数时，函数不能有括号，否则会报错
      </div>
    )
  }
}
```

### 表单处理

#### 受控组件

##### 什么是受控组件

- 受控组件即其值受到React控制的表单元素
- HTML中的元素是可输入的，也就是有自己的可变状态
- 但React中可变状态通常保存在state中，并且只能通过setState()方法来修改
- React将state与表单元素value绑定到一起，由state的值来控制表单元素的值

##### 使用步骤

1. 在state中添加一个状态，作为表单元素的value值(控制表单元素值的来源)
2. 给表单元素绑定change事件，将表单元素的值设置为state的值(控制表单元素值的变化)

##### 多表单元素优化步骤

1. 给表单元素添加name属性，名称与state相同
2. 根据表单元素类型获取对应值
   - 此处主要判断是否为复选框
3. 在change事件处理程序中通过[name]来修改对应的state

```jsx
class Hello extends React.Component {
  constructor() {
    super()
    this.state = {
      txt1: '',
      txt2: '',
      city: 'bj',
      isChecked: false
    }
  }
  handleForm = e => {
    // 获取当前DOM对象
    const target = e.target

    // 根据类型获取值
    const value = target.type === 'checkbox' ? target.checked : target.value
    const name = target.name
    console.log(name)
    console.log(value)
    this.setState({
      [name]: value
    })
  }
  render() {
    return (
      <div>
        <input type="text" name="txt1" value={this.state.txt1} onChange={this.handleForm} />
        <textarea type="text" name="txt2" value={this.state.txt2} onChange={this.handleForm} />

        <select name="city" value={this.state.city} onChange={this.handleForm}>
          <option value="sh">上海</option>
          <option value="bj">北京</option>
          <option value="hz">杭州</option>
        </select>

        <input type="checkbox" name="isChecked" checked={this.state.isChecked} onChange={this.handleForm} />
      </div>
    )
  }
}
```

#### 非受控组件(不推荐)

##### 使用步骤

1. 调用React.createRef()方法创建一个ref对象

```jsx
constructor () {
	super()
    this.txtRef = React.createRef()
}
```

2. 将创建好的ref对象添加到文本框中

```jsx
<input type="text" ref={this.txtRef}></input>
```

3. 通过ref对象获取到文本框的值

```jsx
console.log(this.txtRef.current.value)
```

## React组件进阶

### 组件通讯介绍

组件是独立且封闭的单元，默认情况下，组件只能使用自身的数据，而在组件化过程中，我们将一个完整的功能拆分成多个组件以更好地完成整个应用的功能，在这个过程中，多个组件之间不可避免的要共享某些数据。

为了实现这些功能，就要打破组件的独立封闭性，让其与外界沟通，这个过程就是组件通讯

### 组件的props

- 组件是封闭的，要接收外部数据应该通过props来实现
- props的作用：接收传递给组件的数据
- 传递数据：给组件标签添加属性
- 接收数据：函数组件通过参数props接收数据，类组件通过this.props接收数据

```jsx
<Hello name="jack" age={19} />
```

```jsx
function Hello(props) {
    console.log(props)
    return (
    	<div>接收到数据: {props.name}</div>
    )
}
```

```jsx
class Hello extends React.Component {
    render() {
        return (
        	<div>接收到数据: {this.props.age}</div>
        )
    }
}
```

#### 特点

1. 可以给组件传递任意类型的数据

   - 包括函数

2. props是只读的对象，只能读取属性的值，无法修改对象

   - 如果修改，react会直接报错

3. 注意：使用类组件时，如果写了构造函数，应该将props传递给super()，否则无法在构造函数中获取到props

   - ```jsx
     class Hello extends React.Component {
         constructor(props) {
             // 将props传递给父类构造函数
             super(props)
             // 如果没有将props传递给父组件，而是直接在构造函数中写this.props
             // 则会返回undefined
             // 注意：这种情况只会影响构造函数，而不会影响其他函数
         }
         render () {
             return <div>接收到的数据：{this.props.age}</div>
         }
     }
     ```

### 组件通讯的三种方式

#### 父组件传递数据给子组件

1. 父组件提供要传递的state数据
2. 给子组件标签添加属性，值为state中的数据
3. 子组件中通过props接收父组件中传递的数据

#### 子组件传递数据给父组件

1. 父组件提供一个回调函数(用于接收数据)
2. 将该函数作为属性的值传递给子组件
3. 子组件通过props调用回调函数
4. 将子组件的数据作为参数传递给回调函数

#### 兄弟组件之间的通讯

- 将共享状态提升到最近的公共父组件中，由公共父组件管理这个状态
- 实现：状态提升
- 公共父组件职责：
  1. 提供共享状态
  2. 提供操作共享状态的方法
- 要通讯的子组件只需通过props接收状态或操作状态的方法

```jsx
import React from 'react'
import ReactDOM from 'react-dom'

class Father extends React.Component {
  state = {
    count: 0
  }
  changeCount = step => {
    this.setState({
      count: this.state.count + step
    })
  }
  render() {
    return (
      <div>
        <Child2 count={this.state.count} />
        <Child1 fn={this.changeCount} />
      </div>
    )
  }
}

class Child1 extends React.Component {
  state = {
    count: 1
  }
  changeCount = e => {
    this.setState({
      count: Number(e.target.value)
    })
  }
  render() {
    return (
      <div>
        <input type={'text'} value={this.state.count} onChange={e => this.changeCount(e)}></input>
        <button onClick={() => this.props.fn(this.state.count)}>+{this.state.count}</button>
      </div>
    )
  }
}

class Child2 extends React.Component {
  render() {
    return (
      <div>
        <div>计数器：{this.props.count}</div>
      </div>
    )
  }
}

ReactDOM.render(<Father />, document.getElementById('root'))
```

### Context

如果要跨组件传递数据，可以使用Context

##### 使用步骤

1. 调用React.createContext()创建Provider(提供数据)和Consumer(消费数据)两个组件

```jsx
const { Provider, Consumer } = React.createContext()
```

2. 使用Provider组件作为==父节点==

3. 设置value属性，表示要传递的数据

```jsx
<Provider value="这是要传递的数据">
	<div className="App">
    	<Child1 />
    </div>
</Provider>
```

4. 调用Consumer组件接收数据

```jsx
<Consumer>
	{data => <span>data参数表示接收到的数据 -- {data}</span>}
</Consumer>
```

##### Context综合演示

```jsx
import React from 'react'
import ReactDOM from 'react-dom'

const { Provider, Consumer } = React.createContext()

class App extends React.Component {
  render() {
    return (
      <Provider value="这是要被传递的数据">
        <div>
          <Node />
        </div>
      </Provider>
    )
  }
}

class Node extends React.Component {
  render() {
    return (
      <div>
        <SubNode />
      </div>
    )
  }
}

class SubNode extends React.Component {
  render() {
    return (
      <div>
        <Child />
      </div>
    )
  }
}

class Child extends React.Component {
  render() {
    return (
      <div>
        <Consumer>{data => <span>这是data数据中的内容：{data}</span>}</Consumer>
        <div>这是一个子节点</div>
      </div>
    )
  }
}

ReactDOM.render(<App />, document.getElementById('root'))
```

### props深入

#### children属性

- children属性表示组件标签的==子节点==，当组件标签有子节点时，props就会有该属性
- children属性与普通的props一样，值可以是任意值(文本React元素、组件甚至函数)

> 子节点为`<组件名></组件名>`中包裹的内容

#### props校验

- 对于组件来说，props是外来的，无法保证组件使用者传入什么格式的数据，如果传入的数据格式不对，可能会导致组件内部报错，最关键的是：报错时，组件的使用者不知道明确的错误原因
- props校验允许在创建组件的时候制定props的类型、格式等
- 作用：捕获使用组件时因为props导致的错误，给出明确的错误提示，增加组件的健壮性

```jsx
// 
App.propTypes = {
	colors :PropTypes.array	// 此处表示组件的colors属性需要传入一个数组类型的值
}
```

##### 使用步骤

1. 安装包 `prop-types` (`yarn add prop-types` / `npm i prop-types`)
2. 导入`prop-types`包
3. 使用 `组件名.propTypes = {}` 来给组件的props添加校验规则
4. 校验规则通过`PropTypes`对象来制定
5. 注意：组件校验仅仅只是将传入类型错误的信息提示到控制台，而并非直接报错

```jsx
import React from 'react'
import ReactDOM from 'react-dom'
import PropTypes from 'prop-types'

class App extends React.Component {
  render() {
    return <div>{this.props.count}</div>
  }
}

App.propTypes = {
  count: PropTypes.array
}

ReactDOM.render(<App count="test" />, document.getElementById('root'))
```

##### 约束规则

1. 常见类型：array、bool、func、number、object、string
2. React元素类型：element
3. 必填项：isRequired
4. 指定特定结构的对象：`shape({ })`
5. 还有更多的类型请参考prop-types的官方文档

```jsx
// 常见类型
App.propTypes = {
  optionalFunc: PropTypes.func,
  requiredFunc: PropTypes.func.isRequired,
  optionalObjectWithShape: PropTypes.shape({
    color: PropTypes.string,
    fontSize: PropTypes.number
  })
}
```

#### props的默认值

```jsx
组件名.defaultProps = {
	参数名: 默认值
}
```

### 组件的生命周期

#### 组件的生命周期概述

- 意义：组件的生命周期有助于理解组件的运行方式、完成更复杂的组件功能、分析组件错误原因等
- 组件的生命周期：组件从被创建到挂载到页面中运行，再到组件不用时卸载的过程
- 生命周期的每个阶段总是伴随着一些方法调用，这些方法就是生命周期的==钩子函数==
- 钩子函数的作用：为开发人员在不同阶段操作组件提供了时机
- ==只有类组件才有生命周期==

#### 生命周期的三个阶段

##### 创建时(挂载阶段)

- 执行时机：组件创建时(页面加载时)
- 执行顺序：constructor() -> render() -> componentDidMount()

| 钩子函数          | 触发时机                | 可执行操作                                         |
| ----------------- | ----------------------- | -------------------------------------------------- |
| constructor       | 创建组件时，最先执行    | 初始化state并为事件处理程序绑定this                |
| render            | 每次组件渲染都会触发    | 渲染UI(注意：不要调用setState，否则会无限递归报错) |
| componentDidMount | 组件挂载(完成DOM渲染)后 | 发送网络请求和DOM操作                              |

##### 更新时(更新阶段)

- 执行时机
  1. `setState()`
  2. `forceUpdate()`
  3. 组件接收到新的props
- 以上三者任意一种变化，组件就会重新渲染
- 执行顺序：render() -> componentDidUpdate()

| 钩子函数           | 触发时机                | 可执行操作                                                   |
| ------------------ | ----------------------- | ------------------------------------------------------------ |
| render             | 每次组件渲染都会触发    | 渲染UI(与挂载阶段是同一个render)                             |
| componentDidUpdate | 组件更新(完成DOM渲染)后 | 发送网络请求和DOM操作<br/>注意：如果要setState()必须放在一个if条件里面，否则会无限递归报错 |

```
componentDidUpdate(prevProps) {
	if(prevProps.count != this.props.count)	// 比较更新前后的props是否相同
	{
		this.setState({ })
	}
}
```

##### 卸载时(卸载阶段)

- 执行时机：组件从页面中消失

| 钩子函数             | 触发时机               | 可执行操作                       |
| -------------------- | ---------------------- | -------------------------------- |
| componentWillUnmount | 组件卸载(从页面中消失) | 执行清理工作(例如：清理定时器等) |

#### 不常用钩子函数介绍

- React中还有几个不常用的钩子函数，具体参看官方文档

### render-props和高阶组件

#### React组件复用概述

- React组件应该遵循复用相似功能的原则
- 复用什么？
  1. state
  2. 操作state的方式(组件状态逻辑)
- 组件复用的两种方式
  1. render props模式
  2. 高阶组件(HOC)
- 注意：这两种方式不是新的API，而是利用React自身特点的编码技巧演化而成的固定写法

#### render-props模式

##### 思路分析

- 将要复用的state和操作state的方法封装到一个组件中
- 如何拿到组件中复用的state
  - 在使用组件时，添加一个值为函数的prop，通过函数参数来获取复用的state(需要组件内实现)
- 如何渲染任意UI
  - 使用该函数的返回值作为要渲染的UI内容

##### 使用步骤

1. 创建Mouse组件，在组件中提供复用的状态逻辑代码(1. 状态  2. 操作状态的方法)
2. 将要复用的状态作为props.render(state)方法的参数暴露到组件外部
3. 使用props.render()的返回值作为要渲染的内容

```jsx
class Mouse extends React.Component {
  state = {
    x: 0,
    y: 0
  }
  handleMouseMove = e => {
    this.setState({
      x: e.clientX,
      y: e.clientY
    })
    console.log(this.state.x, this.state.y)
  }
  componentDidMount() {
    window.addEventListener('mousemove', this.handleMouseMove)
  }
  render() {
    // 注意：这里返回的是传递进来的参数中的内容，一般是一个函数
    return this.props.render(this.state)
  }
}
ReactDOM.render(
  // 注意：这里的render是一个函数，这个函数会在Mouse组件内部被调用
  // 此处的state是一个形参
  <Mouse
    render={state => (		
      <p>
        鼠标位置：{state.x} {state.y}
      </p>
    )}
  />,
  document.getElementById('root')
)
```

##### 使用children代替render属性

- 注意：并不是该模式叫render props就必须使用名为render的prop，实际上可以使用任意名称的prop
- 把prop是一个函数并且告诉组件要渲染什么内容的技术叫做`render props`模式
- 在实际使用时推荐使用children属性代替render属性
- 因此上方的代码可以改写成

```jsx
class Mouse extends React.Component {
  state = {
    x: 0,
    y: 0
  }
  handleMouseMove = e => {
    this.setState({
      x: e.clientX,
      y: e.clientY
    })
    console.log(this.state.x, this.state.y)
  }
  componentDidMount() {
    window.addEventListener('mousemove', this.handleMouseMove)
  }
  render() {
    // 注意：这里返回的是传递进来的参数中的内容，一般是一个函数
    return this.props.children(this.state)
  }
}
ReactDOM.render(
  // 注意：这里的render是一个函数，这个函数会在Mouse组件内部被调用
  // 此处的state是一个形参
  <Mouse>
    {({ x, y }) => (
      <div>
        鼠标的位置是{x} {y}
      </div>
    )}
  </Mouse>,
  document.getElementById('root')
)
```

##### 代码优化

1. 推荐给render props模式添加props校验
2. 应该在组件卸载时接触mousemove事件绑定

```jsx
class Mouse extends React.Component {
  state = {
    x: 0,
    y: 0
  }
  handleMouseMove = e => {
    this.setState({
      x: e.clientX,
      y: e.clientY
    })
    console.log(this.state.x, this.state.y)
  }
  componentDidMount() {
    window.addEventListener('mousemove', this.handleMouseMove)
  }
  componentWillUnmount() {
    window.removeEventListener('mousemove', this.handleMouseMove)
  }
  render() {
    // 注意：这里返回的是传递进来的参数中的内容，一般是一个函数
    return this.props.children(this.state)
  }
}

Mouse.propTypes = {
  children: PropTypes.func
}
Mouse.defaultProps = {
  children: ({ x, y }) => (
    <div>
      鼠标的位置是 {x} {y}
    </div>
  )
}

ReactDOM.render(
  // 注意：这里的render是一个函数，这个函数会在Mouse组件内部被调用
  // 此处的state是一个形参
  <Mouse>
    {({ x, y }) => (
      <div>
        test鼠标的位置是{x} {y}
      </div>
    )}
  </Mouse>,
  document.getElementById('root')
)
```

#### 高阶组件

##### 概述

- 目的：实现状态逻辑复用
- 高阶组件采用包装(装饰)模式，通过包装组件增强组件功能

##### 思路分析

- 高阶组件(HOC, Higher-Order Component)是一个==函数==，接收要包装的组件，返回增强后的组件
- 高阶组件内部创建一个类组件，在这个类组件中提供复用的状态逻辑代码，通过prop将复用的状态传递给被包装组件 WrappedComponent

```jsx
const EnhanceComponent = withHOC(WrappedComponnet)
```

```jsx
// 高阶组件内部创建的类组件
class Mouse extends React.Component {
    render() {
        return <WrappedComponent {...this.state} /}
    }
}
```

##### 使用步骤

1. 创建一个函数，名称约定以with开头
2. 指定函数参数，参数应该以大写字母开头(作为要渲染的组件)
3. 在函数内部创建一个类组件，提供复用的状态逻辑代码，并返回
4. 在该组件中渲染参数组件，同时将状态通过prop传递给参数组件
5. 调用该高阶组件，传入要增强的组件，通过返回值拿到增强的组件并将其渲染到页面中

##### 设置displayName

- 使用高阶组件存在的问题：复用高阶组件得到的所有组件的名称都会相同，不利于调试
- 原因：默认情况下，React使用组件名称作为displayName
- 解决方式：为高阶组件设置displayName，便于调试时区分不同的组件
- displayName的作用：用于设置调试信息
- 设置方式：

```jsx
Mouse.displayName = `WithMouse${getDisplayName(WrappedComponent)}`

function getDisplayName(WrappedComponent) {
    return WrappedComponent.displayName || WrappedComponent.name || 'Component'
}
```

##### 传递props

- 问题：如果没有传递props，则会造成props丢失
- 原因：高阶组件没有往下传递props
- 解决方式：渲染WrappedComponent时，将state和this.props一起传递给组件
- 传递方式：

```jsx
<WrappedComponent {...this.state} {...this.props} />
```

##### 综合示例

```jsx
// 这是将要被渲染的组件UI
const WrappedComponent = props => (
  <p>
    鼠标当前位置：(x:{props.x}, y:{props.y})
  </p>
)

// 这是用于封装高阶组件的函数
function withMouse(WrappedComponent) {
  // 这是用于封装功能的类组件
  class Mouse extends React.Component {
    state = {
      x: 0,
      y: 0
    }
    handleMouseMove = e => {
      this.setState({
        x: e.clientX,
        y: e.clientY
      })
    }

    componentDidMount() {
      window.addEventListener('mousemove', this.handleMouseMove)
    }
    componentWillUnmount() {
      window.removeEventListener('mousemove', this.handleMouseMove)
    }
    render() {
      // 注意：直接将传入参数作为组件调用
      // 将类组件的state和传入的props展开并传入到组件的参数中
      return <WrappedComponent {...this.state} {..this.props}></WrappedComponent>
    }
  }
  // 将封装好的整个高阶组件返回
  return Mouse
}


// 正式渲染高高阶组件
const Result = withMouse(WrappedComponent)

ReactDOM.render(
  <Result />,
  document.getElementById('root')
)
```

## React原理揭秘

### setState()的说明

#### 更新数据

- setState()是==异步==更新数据的
  - 因此在使用该语法时，后面的setState()不要依赖于前面的setState()
- 可以在同时调用多次setState()，但是只会触发一次重新渲染
  - render()也是只会被触发一次

#### 推荐语法

- 推荐：使用`setState({(state, props) => {}})` 语法
- 参数state表示==最新==的state
- 参数props表示==最新==的props
- 返回值即最终要更新的状态
- 注意：该语法仍然是异步更新的
- 例如：

```jsx
this.setState((state, props) => {
    return {
        count: state.count+1
    }
})
```

#### setState()的第二个参数

- setState()的第二个参数是一个回调函数，用于在状态更新(页面完成重新渲染)后立即执行某个操作
- 语法：`setState(updater[, callback])`

```jsx
this.setState(
    (state,props) => {},
    () => {console.log('这个回调函数会在状态更新后立即执行')}
)
```

### JSX语法的转化过程

- JSX仅仅是React.createElement()方法的语法糖(简化语法)
- JSX语法最终会被@babel/preset-react插件编译为createElement()方法
- React元素是一个对象，用来描述你希望在屏幕上看到的内容

### 组件更新机制

- setState()的两个作用
  1. 修改state
  2. 更新组件
- 过程
  - 父组件重新渲染时，也会重新渲染子组件，但是只会渲染当前组件子树(当前组件及其所有子组件)

### 组件性能优化

#### 减轻state

- 减轻state：**只存储**与组件渲染相关的数据
- 注意：不用做渲染的数据不要放在state中，比如定时器id等
- 对于这种需要在多个方法中用到的数据应该放在this中而不是this.state中

#### 避免不必要的重新渲染

- 组件更新机制：父组件更新会引起子组件更新
- 如何避免不必要的重新渲染？
  - 解决方式：使用钩子函数 `shouldComponentUpdate(nextProps,nextState)`
    - 参数nextProps表示最新的props
    - 参数nextState表示最新的state
  - 作用：通过该钩子函数的==返回值==决定该组件是否重新渲染，返回true表示重新渲染，false表示不重新渲染
  - 触发时机：该钩子函数是更新阶段的钩子函数，组件重新渲染前执行，即先执行该函数，再执行render()函数

#### 纯组件

- 纯组件(`React.PureComponent`)与`React.Component`功能相似

```jsx
class Hello extends React.PureComponent {
    render() {
        return {
            <div>这是一个纯组件</div>
        }
    }
}
```

- 区别：PureComponent内部==自动实现==了`shouldComponentUpdate`钩子，不需要手动进行比较
- 原理：纯组件内部通过分别对比前后两次props和state的值来决定是否重新渲染组件
- 说明：纯组件内部对比的方式是`shallow compare`(浅层对比)
  - 即如果state中存在对象，则只是简单地比较地址，而非比较其值
  - 注意：如果state或者props中属性值为引用类型时，应该==创建新数据==，而不要直接修改原数据

```jsx
const newObj = {...state.obj, number: 2}
setState({obj:newObj})

// 不要用数组的push/unshift等直接修改当前数组的方法
// 而应该用concat或slice等这些返回新数组的方法
thi.setState({
    list: [...this.state.list, {新数据}]
})
```

### 虚拟DOM和Diff算法

- React更新视图思想
  - 只要state变化就重新渲染视图
  - 特点：思路非常清晰
- 注意：如果组件中只有一个DOM元素需要更新时，并不需要把整个组件的内容重新渲染，而仅仅只是==部分更新==，只更新变化了的地方
- React是如何做到部分更新的
  - 虚拟DOM配合Diff算法