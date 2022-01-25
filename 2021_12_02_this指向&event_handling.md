# 关于 JS 中 this 指向转换

- call()、apply()、bind() 都是用来重定义 this 这个对象的。
- 相同点：这三个函数的第一个参数都是 this 的指向对象
- 不同点：

1. call()的第二个至第 n 个参数，直接放进去，用","相隔。

2. apply()的第二个至第 n 个参数，全部放进一个数组。

3. bind()除了返回是函数外，其他参数用法和 call 一样。

```js
var name = "小王";
age = 22;
var obj = {
  name: "小张",
  objAge: this.age,
  myFun: function (fm, t) {
    console.log(this.name + "年龄" + this.age, "来自" + fm + "去往" + t);
  },
};

var db = {
  name: "德玛",
  age: 25,
};

obj.myFun.call(db, "成都", "上海");
obj.myFun.apply(db, ["成都", "上海"]);
obj.myFun.bind(db, "成都", "上海")();

/* 结果如下：
      德玛年龄25 来自成都去往上海
      德玛年龄25 来自成都去往上海
      德玛年龄25 来自成都去往上海
*/
```

## 关于 React 事件的渲染

- react 事件命名采用 camelCase,而不是纯小写

- 传入是整个函数，而不是字符串

```js
/* 给 setState 传递一个函数，而不是一个对象，就可以确保每次的调用都 是使用最新版的 state 
    - setState(updater,[callback])
    - 带有形参的updater():  (state,props) =>stateChange
 */

class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isLogIn: true,
    };
     /* 一定别忘了给自定义函数绑定this的指向*/
    this.hancleClick = this.hancleClick.bind(this);
  }

  hancleClick() {
    this.setState((state) => ({ isLogIn: !state.isLogIn }));
  }

  render() {
    return (
      <div>
        <button onClick={this.hancleClick}>
          {this.state.isLogIn ? "on" : "off"}{" "}
        </button>
      </div>
    );
  }
}

ReactDOM.render(<Toggle />, document.getElementById("root"));
```

效果：
alt[toggle_log.png](./img/toggle_log.gif)