# 如何正确使用React setState()

  1. 不直接改变state,而是调用setState(),构造函数是唯一一个可给this.state赋值的地方

```js
  /*incorrect */
  this.state.name = "Ling";
  /*correct */
  this.setState({
     name:"Ling"
  })
```

  2. 调用setState(）是异步的，调用setState()不会立刻影射新的this.state的值，所以如果无需更新state，需要传递一个函数而不是一个具体的对象

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

### 以上结果为1

## 例子2

```js
/*箭头函数*/
count(){
  this.setState(
    (state)=> return {
      count:state.count + 1
    }
  )
}

/*正常函数*/
count(){
  this.setState(
    function(state){
        return{
          count:state.count + 1
        }
    }
  )
}

click(){
  this.count();
  this.count();
  this.count();
}
```

### 现在结果为3了

3.数据是向下传递的，组件可以选择把它的 state 作为 props 向下传递到它的子组件中

```js
 <FormattedDate date={this.state.date} />
```

### FormattedDate组件在他的的props属性中接受date参数，但组件本身不知道这是来自父组件的props还是state，还是手动输入的

```js
 function FormattedDate (props){
   return <h1>It is {props.date.toLocaleString()}</h1>
 }
```
