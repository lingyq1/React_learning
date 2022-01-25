### 1. React Props and styling practice

#### definition:setup more complex property of react

#### index.html

```
<html>
    <head>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div id="root"></div>
        <script src="index.pack.js"></script>
    </body>
</html>
```

#### index.js

```
import React from "react"
import  ReactDom from "react-dom"

import App from "./App.js"

ReactDom.render(<App />,document.getElementById("root"));
```

#### App.js

```
import React from "react";
import Jake from "./Jake.js";
import JakeData from "./jakeData";

function App(){
   const jakeComponent = JakeData.map( jake => <jake key={jake.id} question={jake.question} punchline={jake.punchline}  /> )

    return(
        <div>
          {jakeComponents}
      </ div>
    )
}

export default App;
```

#### Jake.js

```
import React from "react";
 
 function Jake(props){
     console.log(props.question);
     return (
        
       <div className="border">
         <h3 style={{display: !props.question && "none"}}>Answer: {props.question}</h3>
         <h3 style={{color: !props.question && "blue"}}>Question: {props.punchline}</h3>
       </ div>
     )
 }
 
 export default Jake 
```
#### JakeData.js

```
 
const JakeData = [
  {
      id:1,
      punchline:"green"
  },
  {
      id:2,
      question:"what's you favarate color?",
      punchline:"green"
  },
  {
      id:3,
      question:"what's you favarate animal?"
      punchline:"dog"
  },
  {
      id:4,
      question="what's you favarate place?"
      punchline:"Tibet"
  },
  {
      id:5,
      question="what's you favarate food?"
      punchline:"ice-cream"
  },
  {
      id:6,
      question="what's you favarate fruit?"
      punchline:"watermelon"
  },

]
 
 export default Jake 
```

#### style.css

```
body { }

.border {
    border-bottom: greenyellow 2px solid
    ;
}
```