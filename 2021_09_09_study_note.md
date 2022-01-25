## 1. move component into separate files

### definition: can make your program more modular

#### country.js

```
    import React from "react"

    function country(){
        return(
            <div>
            <h1>Anzo Ling</h1>
            <p>There are some countries  I want to go below</p>
             <ul>
               <li>Switzerland</li>
               <li>Japan</li>
               <li>Russia</li>
             </ul>
            </div>
        )}

    export default country
```

#### index.html

```
<html>
  <head>
   <link rel="stylesheet" href="style.css">
  </head>
 <body>
  <div id="main"></div>
  <script src="index.pack.js"></script>
 </body>
</html>
```

#### index.js

```
import React from "react"
import ReactDOM from "react-dom"

import country from "./components/country"

ReactDOM.render(<country />, document.getElementById("main"))
```


#### style.css

```
.main {
    
}
```
