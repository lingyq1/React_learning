# 关于 React props 属性

1. 官方定义：当 React 元素为用户自定义组件时，它会将 JSX 所接收的属性（attributes）以及子组件（children）转换为单个对象传递给组件，这个对象被称之为 “props”。

2.组件无论是使用函数声明还是通过 class 声明，都决不能修改自身的 props。
所有 React 组件都必须像纯函数一样保护它们的 props 不被更改。所以有了 state 这个特性，允许 react 组件随用户操作或其他响应而动态改变数据。

## 关于react提取组件的案例,我认为是组件间的关系的属性关系是相对的，即只需要知道子组件相对父组件的属性继承关系即可，而不用全局地考虑数据不同组件间的关系

## 初始条件： comment 数据和渲染代码

```js
 const comment = {
  text: 'I hope you enjoy learning React!',
  author: {
    name: 'Hello Kitty',
    avatarUrl: 'https://placekitten.com/g/64/64',
  },
};

ReactDom.render(){
  <Comment
     text={comment.text}
     author={comment.author}
  />
}
```

##

## 组件没分离时

```js
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img
          className="Avatar"
          src="props.author.avatarUrl"
          alt="props.author.name"
        />
        <div className="UserInfo-name">{props.author.name}</div>
      </div>
      <div className="Comment-text">{props.text}</div>
    </div>
  );
}
```

## 提取组件后，组件如下

```js
function Comment(props) {
  return (
    <div className="Comment">
      <userInfo user="props.author" />
      <div className="Comment-text">{props.text}</div>
    </div>
  );
}

/* 在Avatar组件这里忘记加自定义属性：user="props.user"  */

function userInfo(props) {
  return (
    <div className="userInfo">
      <Avatar user="props.user" />  
      <div className="userInfo-name">{props.user.name}</div>
    </div>
  );
}

function Avatar(props) {
  return (
    <img
      className="userInfo-Avatar"
      src="props.user.avatarUrl"
      alt="props.user.name"
    />
  );
}
```
