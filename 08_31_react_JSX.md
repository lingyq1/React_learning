## 1. React JSX
### definition: JSX is used to declare elements in React
###  注：JSX可以生成React元素，不是采用标记与逻辑人为分离的形式，而是将两者共同存放在“组件”这种松散耦合单元里。
#### 1）简单的例子
```
    const element = <h1 className="foo">Hello, world</h1>;
	ReactDOM.render(element, document.getElementById('root'));
```
#### 2）在JSX中嵌入表达式
```
   const name = "Anzo";
   const element = <h1>hello, {name}</h1>

   ReactDom.render(element,document.getElementById("test"));
```

#### 3) JSX自身作为一个表达式
```
  function getGreeting(user){
      if(user){
          return <h1>Hello,{formatName(user)}!</h1>
      }
      return <h1>hello, Stranger</h1>
  }
```
#### 4)JSX中指定属性
  ```
    const element = <div tabIndex="0"></div>;  //通过引号引入

    const element = <img src={user.avatarUrl}></img>;  // 通过大括号引入
  ```

#### 5）使用JSX指定子元素
```
   const element = {
       <div>
         <h1>Hello!</h1>
         <h2>How are you?</h2>
       </div>
   }
```

## 2. react component
### definition: use component to output messages easily
```
function HelloMessage(props) {
    return <h1>Hello World!</h1>;
}
```
## 3.react parent/child component
### definition: Components can be separated out and easier to write
#### main.js:
```
function App() {
    return (
        <div>
            <nav>
                <h1>Hello a third time!</h1>
                <ul>
                    <li>Thing 1</li>
                </ul>
            </nav>
            <footer />
        </div>
    )
}

export default App
 ```
 #### footer.js
 ```
 function Footer() {
    return (
        <footer>
            <h3>This is my footer element</h3>
        </footer>
    )
}

export default Footer
 ```
## 4. react todo App 
### definition: can create a new todo list app
#### index.js
```
import React from "react"
import ReactDOM from "react-dom"

import App from "./App"

ReactDOM.render(<App />, document.getElementById("root"))
```
#### App.js
```
function App() {
    return (
        <div>
            <input type="checkbox" />
            <p>Placeholder text here</p>   

            <input type="checkbox" />
            <p>Placeholder text here</p>
        </div>
    )
}

export default App
```
#### index.js
```
  <body>
        <div id="root"></div>
        <script src="index.js"></script>
    </body>
```