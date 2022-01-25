## 1.React parent/child component 
### definition:Communication between parent and child components

#### index.html
```
<html>
<body>
  <div div="test"></div>
  <script src="index.js"></script>
</body>
</html>
```
#### index.js
 ```
 import React from "React"
 import ReactDOM from "ReactDOM"

 import app from "./app"

 ReactDOM.render(<app />,document.getElementById("test"))
 ```

 #### app.js
 ```
  import React from "React"

  import first from "./component/first"
  import second from "./component/second"
  import third from "./component/third"

 function app(){
    return(
      <div>
        <first />
        <second />
        <third />
      </div>
    )
 }

 export default app 

 ```

 #### first.js
```
  import React from "React"
   function first(){
     return(
       <header> first </header>
     )
   }

   export default first
 ```

  #### second.js
```
  import React from "React"
   function second(){
     return(
       <header> second </header>
     )
   }

   export default second
 ```

 #### third.js
```
  import React from "React"
   function third(){
     return(
       <header> third </header>
     )
   }

   export default third
 ```