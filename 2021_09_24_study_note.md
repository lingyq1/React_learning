 ### 1. React Inline Styles with the Style Property
 #### definition:setup the css style from the jsx

#### index.html
```
<html>
    <head></head>
  <body>
     <div></div>
     <script src="./index.pack.js"></script>
  </body>
</html>
```

#### index.js
```
import React from "react"
import ReactDM from "react_dom"

function test (){
  const date = new Date(); 
  let text; 
  if(date<16>){
  text = "上半旬";
  }else{
      text = "下半旬";
  }

  return (
      <h1 style={{color:"yellow",background:"red"}}> 现在是 {text}！</h1>
  )
}
ReactDom.render(<test />,document.getElementById("title"));
```

#### or index.js
```
import React from "react"
import ReactDM from "react_dom"

function test (){
  const date = new Date(); 
  let text; 
   const CssStyles = {
    fontSize:"50px"
  };

  if(date<16>){
  text = "上半旬";
  CssStyles.color = "red"
  }else{
      text = "下半旬";
      CssStyles.color = "blue"
  }
 
  return (
      <h1 style={CssStyles}> 现在是 {text}！</h1>
  )
}
ReactDom.render(<test />,document.getElementById("title"));
```

### 2.TodoList
#### definition: setup some list containing style

#### index.js
```
 import React from "react"
 import ReactDom from "react-dom"
 
 import App from "./App.js"
 ReactDom.render(<App />, document.getElementById("test")); 
```

#### App.js
```
 import React from "react"
 import todoItem from "./todoItem.js"

 function App (){
     return (
         <div className = "todoList">
          <todoItem />
          <todoItem />
          <todoItem />
         </div>
     )
 }

export default App 
```

#### todoItem.js
```
  import React from "react"

 function todoList(){
     return (
         <div>
           <input type="checkbox"/>
           <p> Hi,please editor here</p>         
         </div>
     )
 }

  export default todoList 
```

#### todoList.css
.todoList {
    background: grey;
    margin: auto;
    width: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
}
#### index.html
```
 <html>
  <head>
    <link rel= "stylesheet" href="style.css">
    <body>
     <div id="test" >
     <script src="./index.pack.js"></script>
    </body>
   </head>
 </html>
```
