## 1.React ToDoList app
### definition:here's a todolist case

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

import ToDoList from "./App.js"

ReactDOM.render(<ToDoList />,document.getElementById("test"))
 ```

 #### App.js
 ```
 import React from "react"

function ToDoList(){
    return ( <div>
        <input type="checkbox"/>
       <p> Hi Eveyone</p>
        <input type="checkbox" />
       <p> Hi Eveyone</p>
        <input type="checkbox" />
       <p> Hi Eveyone</p>
    </div>
    )    
}

 export default ToDoList
 ```

 