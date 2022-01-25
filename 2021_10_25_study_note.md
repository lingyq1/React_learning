### 1. React state practice

#### definition:how to translate the state in React

#### index.html

```
<html>
    <head>
        <link rel="stylesheet" href="style.css">
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
import React,{Component} from "react"

class App extends Component {
    
        constructor () {
            super()
            this.state = {
                name:"Anzo",
                age:"25"
            }
        }
      render (){  
        return(
            <div>
              <h1>{this.state.name}</h1>
              <h3> {this.state.age} years old</h3>
            </div>
        )
    }
}
export default App
```

#### style.css
```
body { }
```