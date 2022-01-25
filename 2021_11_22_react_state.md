# 关于React state笔记

  1. react 的 state 是可变的， props 是不可变的。
  
  2. 关于运用state的例子如下：

## Clock.js

 ```js
   import React from "react";
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date() };
  }

  render() {
    return (
      <div>
        <h1>hello World~</h1>
        <h2>now the time is :{this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
export default Clock;

 ```
 ![current_time](./img/current_time.png)

3.  State Hook 是react 16.8 新增的特性，可以在不编写 class情况下使用state及其他react特性。

## Count.js

```js
import React, { useState } from "react";

function Count() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>you click{count} times</p>
      <button onClick={() => setCount(count + 1)}>CLick me</button>
    </div>
  );
}
export default Count;

```

![Click_times](./img/Click_times.png)