# 如何正确使用 React constructor()和 super()

1. constructor()：react class 組件的默任方法，如沒有添加，系統會默认生成

2. super(): 在 constructor()里用于继承父类，因为子类是没有自己的 this 的，需要从父类继承，所以 super()是子类继承父类的方法

```js
/*incorrect */
class Test extends React.component {
  state = { name: "Anzo" };
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
}

function App() {
  return <Test />;
}

ReactDOM.render(<App />, document.getElementById("root"));
```

## 上面的 test 组件等价于下面的写法

```js
class test extends React.component{
  constructor(){
    super();
    this.state ={ name:"Anzo"};
  }

   render(){
     return (
        <div><h1>{this.state.name}<h1/></div>
     )
   }

}
```

## 一般很少在组件里直接给 state 赋初始值,而是在 state 统一放在 constructor()方法里

```js
 class test extends React.component{
   constructor(){
     super();
     console.log(this.state);
     this.state={number:"123"};
     console.log(this.state);
   }
   state = {number:"456";
 }
   /* result:
      456
      123
   */
```

> 关于 super()与 super(props)，如果你用到了 constructor 就必须写 super()，是用来初始化 this 的，可以绑定事件到 this 上，如果你在 constructor 中要使用 this.props，就必须给 super 加参数：super(props)，无论有没有 constructor，在 render 中 this.props 都是可以使用的，这是 react 自动附带的

```js
class test extends React.component{
   constructor(props){
   super(props);
   this.props.Fruit = "apple";
   this.props.color = "green";
   this.state ={
     arr = [],
     number = "6"
   }
 }
}
```

> 如需要定义 props 属性，如:Fruit="apple"，则需要用 super(props),如果只定义状态 this.state,则可直接 super()

> this.props 必须要是一个对象，才能在它下面定义属性，而 constructor(props){}传入的参数 props 为对象，所以 super(props)的作用在父类的构造函数中给 props 赋值一个对象 this.props= props,这样就能在它的下面定义你要用的属性了，然而其他的由于没有传参就直接赋值为 undefined。由于 state 下面没有属性，如只定义 state 可直接 super()
