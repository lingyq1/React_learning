### 1. React Props and styling practice

#### definition:setup more complex property of react

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
import  ReactDom from "react-dom"

import App from "./App.js" 

ReactDom.render(<App />,document.getElementById("test"));
```

#### App.js

```
import React from "react"
import TodoItem from "./TodoItem"
import todosData from "./todosData"

function App() {
    const todoComponent = todosData.map( item => <TodoItem key={item.id} item={item}  /> )
    
    return (
        <div className="todo-list">
           {todoCompon  ent}
        </div>
    )
}

export default App
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

#### style.css

```
body { }

.border {
    border-bottom: greenyellow 2px solid
    ;
}
```
#### TodoItems.js
```
 import React from "react"

function TodoItem(props) {
    return (
        <div className="todo-item">
            <input type="checkbox" checked={props.item.completed}/>
            <p>{props.item.text}</p>
        </div>
    )
}

export default TodoItem
```