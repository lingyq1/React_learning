### 1. React Pros

#### definition:setup the property of react

#### index.html

```
<html>
    <head>
      <link rel= "stylesheet" href="style.css">
    </head>
  <body>
     <div id ="test"></div>
     <script src="./index.pack.js"></script>
  </body>
</html>
```

#### index.js

```
import React from "react"
import ReactDM from "react_dom"

import App from "./App.js"

ReactDom.render(<App />,getElementById("test"));
```

#### App.js

```
import React from "react"
import Card form "./Card.js"

function App(){
  return(
     <div className="Content">
      <Card
       content={{name: "Mr. Whiskerson", imgUrl: "http://placekitten.com/300/200", phone: "(212) 555-1234", email: "mr.whiskaz@catnap.meow"}}
      />

      <Card
                content={{name: "Fluffykins", imgUrl: "http://placekitten.com/400/200", phone: "(212) 555-2345", email: "fluff@me.com"}}
            />

            <Card
                content={{name: "Destroyer", imgUrl: "http://placekitten.com/400/300", phone: "(212) 555-3456", email: "ofworlds@yahoo.com"}}
            />

            <Card
                content={{name: "Felix", imgUrl: "http://placekitten.com/200/100", phone: "(212) 555-4567", email: "thecat@hotmail.com"}}
            />

     </div>

  )
}

 export default App
```

#### Card.js

```
import React from "react"
  function Card (props){
    return(
       <div className = "ContentCard">
          <img src={props.content.imgUrl}/>
          <h3>{props.content.name}</h3>
          <p>{props.content.phone}</p>
          <p>{props.content.email}</p>
       </div>
    )
  }
```

#### style.css

```
body {
  margin:0
}

.Content {
  display:flex;
  flex-wrap: wrap;
}

.ContentCard {
 flex-basis:40%;
 margin:2px;
}

.ContentCard > img {
   width: 100%;
   height:auto;
}

.ContentCard >h3 {
  text-align:center;
}

.ContentCard > p {
  font-size: 12px;
}

```