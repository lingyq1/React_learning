## 1. React with css classes
### definition: create the css style in react
#### App.js
```
    import React from "react"
    import Header from ""./Header.js"

    function App(){
        return(
            <div>
            <header />
            </div>
        )}
    
    export default App
```
#### index.html
```
<html>
  <head>
   <link rel="stylesheet" href="style.css">
  </head>
 <body>
  <div id="title"></div>
  <script src="index.pack.js"></script>
 </body>
</html>
```
#### index.js
```
import React from "react"
import ReactDOM from "react-dom"

import App from "./App"

ReactDOM.render(<App />, document.getElementById("title"))
```
#### Header.js
```
import React from "react"

function Header() {
    return (
        <header className="title">This is the title</header>
    )
}

export default Header
```
#### style.css
```
.title {
    height:150px;
    background-color: grey;
    color:white;
    text-align:center;
    font-size:40px;
    display: flex;
    justify-content: center;
    align-items: center;
}
```