## React 组件间数据传递

1. 父组件传给子组件

```js
class Parent extends React.Component {
  state = {
    myName: "Anzo",
  };
  render() {
    return (
      <div className="parent">
        父组件：
        <Child name={this.state.myName} />
      </div>
    );
  }
}
//子组件
const Child = (props) => {
  return (
    <div className="child">
      <p>子组件，接收到父组件的数据:{props.name}</p>
    </div>
  );
};
```

2. 子组件传给父组件

```js
class Parent extends React.Component {
  state = {
    parentMsg: "",
  };
  //提供回调函数
  getChildMsg = (data) => {
    console.log("接收到子组件中传递过来的数据:", data);
    // 传值到父函数的state
    this.setState({
      parentMsg: data,
    });
  };
  render() {
    return (
      <div className="parent">
        父组件: {this.state.parentMsg}
        <Child getMsg={this.getChildMsg} />
      </div>
    );
  }
}
//子组件
class Child extends React.Component {
  state = {
    msg: "刷抖音",
  };
  handleClick = () => {
    //子组件调用父组件中传递过来的回调函数
    this.props.getMsg(this.state.msg);
  };
  render() {
    return (
      <div className="child">
        子组件：
        <button onClick={this.handleClick}>点我，给父组件传递数据</button>
      </div>
    );
  }
}
ReactDOM.render(<Parent />, document.getElementById("root"));
```

3. 兄弟组件

- 将共享状态提升到最近的公共父组件中，由公共父组件管理这个状态

```js
class Parent extends React.Component {
  state = {
    number: 0,
  };

  handleCilck = () => {
    this.setState({
      number: this.state.number + 1,
    });
  };
  render() {
    return (
      <div>
        <Child1 updatedNumber={this.state.number} />
        <Child2 click={this.handleCilck} />
      </div>
    );
  }
}
//子组件
const Child1 = (props) => {
  return <h2>计数器:{props.updatedNumber}</h2>;
};
const Child2 = (props) => {
  return <button onClick={props.click}>+1</button>;
};
```
