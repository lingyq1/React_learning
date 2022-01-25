
 ### 1. JSX to javaScript and back
 #### definition:I think this case display the different type of react component

#### index.html
```
<html>
    <head></head>
    <body>
        <div id="test"></div>
        <script src="./index.pack.js"></script>
    </body>
</html>
```
#### index.js
 ```
import React from "react"
import ReactDOM from "react-dom"

function title (){
    const firstName = "Anzo";
    const LastName = "Ling";

    return (
        <h2>Welcome! {`${firstName} ${LastName}`}</h2>
    )
}



ReactDOM.render(<title />,document.getElementById("test"))
 ```

 ### 2.Regular expression
 #### definition: more config

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
      <h1> 现在是 {text}！</h1>
  )
}
ReactDom.render(<test />,document.getElementById("title"));
```