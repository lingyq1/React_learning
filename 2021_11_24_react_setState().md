# 关于React setState()

  1. setState() 会对一个组件的 state 对象安排一次更新。当 state 改变了，该组件就会重新渲染。

  2. 调用setState(）是异步的，调用setState()不会立刻影射新的this.state的值，所以如果无需更新state，需要传递一个函数而不是一个具体的对象。

## 例子1

```js
/* 假设this.state.count为0 */
 count(){  
   this.setState({count: this.state.count + 1});
 }

 click(){
   this.count();
   this.count();
   this.count();
 }
```

## 以上结果为1

## 例子2

```js
count(){
  this.setState(
    (state)=> return {
      count:state.count + 1
    }
  )
}

click(){
  this.count();
  this.count();
  this.count();
}
```

## 现在结果为3了
