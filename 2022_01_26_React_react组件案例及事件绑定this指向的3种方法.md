## React 基本组件--发表评论及边界处理

```js
class App extends React.Component {
  constructor() {
    super();
    this.state = {
      comments: [
        { id: 1, name: "jerry", content: "你好" },
        { id: 2, name: "Anzo", content: "新年" },
        { id: 3, name: "Spire", content: "快乐" },
      ],
      userName: "",
      userContent: "",
    };
  }

  renderList = () => {
    // 方法2： if条件表达式
    if (this.state.comments.length === 0) {
      return <div className="no-comment">暂无评论，快去评论吧~</div>;
    }
    return (
      <ul>
        {this.state.comments.map((item) => (
          <li id={item.id}>
            <h3>评论人:{item.name}</h3>
            <p>评论内容:{item.content}</p>
          </li>
        ))}
      </ul>
    );
  };

  handleForm = (e) => {
    const { name, value } = e.target;
    this.setState({
      [name]: value,
    });
  };

  addComment = () => {
    const { comments, userName, userContent } = this.state;
    console.log(comments);

    //非空验证
    if (userName.trim() === "" || userContent.trim() === "") {
      alert("请输入评论人和评论内容~");
      //这个return是为了防止继续执行下面的代码，渲染空的userName和userContent到评论列表里
      return;
    }

    const newComments = [
      {
        id: Math.random(),
        name: userName,
        content: userContent,
      },
      ...comments,
    ];
    // 这里是清空两个输入框里的数据
    this.setState({
      comments: newComments,
      userName: "",
      userContent: "",
    });
  };

  render() {
    const { userName, userContent } = this.state;
    return (
      <div className="app">
        <div>
          <input
            className="user"
            type="text"
            placeholder="请输入评论人"
            name="userName"
            value={userName}
            onChange={this.handleForm}
          />
          <br />
          <textarea
            className="content"
            cols="30"
            rows="10"
            placeholder="请输入评论内容"
            name="userContent"
            value={userContent}
            onChange={this.handleForm}
          />
          <br />
          <button onClick={this.addComment}>发表评论</button>
        </div>
        {this.renderList()}
      </div>
    );
  }
}
ReactDOM.render(<App />, document.getElementById("root"));
```

## 事件绑定 this 指向的 3 种用法

1.  定义事件时使用箭头函数

```js
class App extends React.Component{
  addComment =()=>{
    ...
  }

  render(){
    return (
      <div>
        <button onClick={this.addComment}></button>
      </div>
    )
  }

}
```

2.  通过 bind()方法绑定事件

```js
class App extends React.Component{

  constructor(){
    super()
    this.state={
      }
      this.addComment = this.addComment.bind(this)
  }

  addComment()=>{
    ...
  }

  render(){
    return (
      <div>
        <button onClick={this.addComment} />
      </div>
    )
  }

}
```

3.  绑定事件时使用箭头函数

```js
class App extends React.Component{
  addComment(){
    ...
  }

  render(){
    return (
      <div>
        <button onClick={()=> this.addComment()} />
      </div>
    )
  }

}
```
