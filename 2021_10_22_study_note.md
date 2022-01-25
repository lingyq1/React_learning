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
import React, {Component} from "react"
import ReactDOM from "react-dom"

// #1
class App extends React.Component {
    render() {
        return (
            <div>
                <Header username="Anzo"/>
                <Greeting />
            </div>
        )    
    }
}

// #2
class Header extends React.Component {
    render() {
        return (
            <header>
                <p>Welcome, {this.props.username}!</p>
            </header>
        )    
    }
}

// #3
class Greeting extends Component {
    render() {
        const date = new Date();
        let days = new Array();
        days[0]="Sunday";
        days[1]="Monday";
        days[2]="Tuesday";
        days[3]="Wednesday";
        days[4]="Thursday";
        days[5]="Friday";
        days[6]="Saturday";
        let a = days[date.getDay()]

        return (
            <h1>Today is {a} ,have a good day~</h1>
        )
    }
}

ReactDOM.render(<App />, document.getElementById("test"))
```