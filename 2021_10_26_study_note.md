### 1. React state practice 2

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
import React form "react"

class App extends React.Component {
    constructor(){
        super()
        this.state = {
            isLoggedIn : false
        }
    }

    render(){
        let Display
        if(this.state.isLoggedIn){
            Display = "in"
        }else {
            Display = "out"
        }
        return (
            <div>
              <h1>You have logged {Display} now~</h1>
            </div>
        )
    }
}

export fault App
```

#### style.css

```
body { }
```

### 2.React Todo App:Phrase 4

#### definition: Change the <App /> component into a stateful class component and load the imported `todosData` into state.

#### index.html

```
<html>
<head>
   <link rel="stylesheet" href="style.css">
   <body>
    <div id="test"></div>
    <script src="index.pack.js" ></script>
   </body>
</head>

</html>

```

#### todoData.js

```
const todosData = [
    {
        id: 1,
        text: "Take out the trash",
        completed: true
    },
    {
        id: 2,
        text: "Grocery shopping",
        completed: false
    },
    {
        id: 3,
        text: "Clean gecko tank",
        completed: false
    },
    {
        id: 4,
        text: "Mow lawn",
        completed: true
    },
    {
        id: 5,
        text: "Catch up on Arrested Development",
        completed: false
    }
]

export default todosData
```

#### TodoItem.js

```
import React from "react"

function TodoItem (props){
    return(
       <div className="todo-item" >
         <input type="checkbox" checked={props.item.completed} OnChange={
             ()=> console.log("changed!")
         } />
         <p>{props.item.text}</p>
       </div>
   )
}

export default TodoItem

```

#### App.js

```
import React from "react"
import TodoItem from "./TodoItem"
import todosData from "./todosData"

class  App extends React.Component{
    constructor (){
        super()
        this.state={
            todos:todosData
        }
    }
     render(){


    const todoitems = this.state.todos.map( item =>  <TodoItem key={item.id} item={item}/> )
    return(
        <div className= "todo-list" >
         {todoitems}
        </div>
    )
}
}
export default App
```

### 3.handling Events in React

#### index.js

```
import React from "react"
import ReactDom from "react-dom"
import App from "./App"

ReactDom.render(<App />,getElelementById("test"));
```

#### index.html

```
<html>
  <head>
  <link rel="stylesheet" href="style.css"/>
 </head>
 <body>
  <div id="test"></div>
  <script src="index.pack.js"></script>
 </body>
</html>
```

#### App.js

```
import React from "react"
function handleClick (){
    console.log("I was clicked~")
}

function App (){
    return (
        <div>
         <img onMouseOver={ ()=>console.log("Hovered!") } src="https://www.fillmurray.com/200/100" />
         <br/>
         <br/>
         <button OnClick={handleClick }>Click me</button>
        </div>
    )
}

```
