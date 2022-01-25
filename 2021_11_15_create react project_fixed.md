### 关于之前运行react project的错误：
  #### 1）react 的logo图片显示不出来；
  #### 2）index.html文件 链接不了 index.css，以致样式加载不出来，明天再去研究下。

### 以上问题得到解决通过峰哥的帮助：
#### 1）我所用的这个脚手架的素材是放在“public”文件夹内的，且路径是网页路径，public文件夹内的文件均处于根目录下，即pubilc/logo192.png的路径为：“http://localhost:3000/logo192.png”；
#### 我发现如在public外的塑造，如“img/logo192.png”,可做相对路径，如“../img/logo192.png”

![public外素材路径](./img/img_path.png)

#### 2) 必须在 自定义组件处引入css文件，而不是在 index.html处引入:
#### import "../index.css"

![navbar.js文件头部引入](./img/import_index_css.png)

### 1. build an react info site

#### index.html

```
<html>
    <head>
        <link rel="stylesheet" href="index.css">
    </head>
    <body>
        <div id="test"></div>
        <script src="index.pack.js"></script>
    </body>
</html>

```

#### index.js

```
import React from "react"
import ReactDOM from "react-dom"

import App from "./App"

ReactDOM.render(<App />, document.getElementById("test"))
```

#### App.js

```
import React from "react"
import Navbar from "./component/Navbar.js"
import Main from "./component/Main.js"

export default function App() {
    return (
        <div className="container">
            <Navbar />
            <Main />
        </div>
    )
}
```

#### style.css

```
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Inter, sans-serif;
    height: 100vh;
    background-color: #282D35;
}

/* 虚拟组件 Dom 可以直接当做一个元素来定义Css 样式 */
nav { 
    display: flex;
    align-items: center;
    background-color: #21222A;
    height: 90px;
    padding: 30px 25px;
}

.nav--logo_text, .nav--title {
    margin: 0;
}

.nav--logo_text {
    margin-right: auto;
    color: #61DAFB;
    font-weight: 700;
    font-size: 22px;
}

.nav--title {
    color: #DEEBF8;
    font-weight: 600;
}

.nav--icon {
    height: 30px;
    margin-right: 7px;
}

main {
    padding: 57px 27px;
    color: white;
    background-image: url(./images/react-icon-large.png);
    background-repeat: no-repeat;
    background-position: right 75%;
}

.main--title {
    margin: 0;
    font-size: 39px;
    letter-spacing: -0.05em;
}

.main--facts {
    margin-top: 46px;
    max-width: 400px;
}

.main--facts > li {
    line-height: 19px;
    padding-block: 10px;
}

.main--facts > li::marker {
    font-size: 1.4rem;
    color: #61DAFB;
}
```

#### Main.js
```
import React from "react";
import "../index.css" /* 必须在 自定义组件处引入css文件，而不是在 index.html处引入 */

export default function Main (){
    return(
        <div>
        <h1 >Hello guys~ What's your favorate fruit?</h1>
        <ul>
            <li>orange</li>
            <li>apple</li>
            <li>banana</li>
            <li>watermelon</li>
        </ul>
        </div>
    )
}
```

#### Navbar.js
```
import React from "react";

export default function Navbar (){
  return(
      /*Nav这里不一定要定义className的属性给它 */
      <nav >  
          <img src="logo192.png" className="nav--icon" alt="dd"/>
          <h3 className="nav--logo_text">ReactFact</h3>
            <h4 className="nav--title">React Course - Project 1</h4>
      </nav>
  )
}
```
### 页面效果：
![img ](./img/normal_project_result.png)
