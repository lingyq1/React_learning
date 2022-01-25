
 ### 1. some caveats
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

import title from "./App.js"

ReactDOM.render(<title />,document.getElementById("test"))
 ```

 #### App.js
 ```
 import React from "react"

const title = ()=>{
    <h1>Hello guys,I'm Anzo~</h1>
}

 export default title
 ```

 