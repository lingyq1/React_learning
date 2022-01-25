## React 基本组件--渲染及获取评论

```js
class App extends React.Component {
  state = {
    comments: [
      { id: 1, name: "jerry", content: "你好" },
      { id: 2, name: "Anzo", content: "新年" },
      { id: 3, name: "Spire", content: "快乐" },
    ],
    userName:'',
    userContent:''
  };

  renderList() {
    /// 方法1： 三元表达式
    // return this.state.comments.length === 0 ? (
    //   <div className="no-comment">暂无评论，快去评论吧~</div>
    // ) : (
    //   <ul>
    //     {this.state.comments.map((item) => (
    //       <li id={item.id}>
    //         <h3>评论人:{item.name}</h3>
    //         <p>评论内容:{item.content}</p>
    //       </li>
    //     ))}
    //   </ul>
    // )

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
  }
 
 // 这里获取评论数据
  handleForm = (e)=>{
    const {name,value} = e.target
    this.setState({
      [name]:value
    })
  }

  render() {

    
    const { userName,userContent} = this.state;
    return (
      <div className="app">
        <div>
          <input className="user" type="text" placeholder="请输入评论人" name="userName" value={userName}  onChange={this.handleForm}/>
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
          <button>发表评论</button>
        </div>
        {this.renderList()}
      </div>
    );
  }
}

ReactDOM.render(<App />, document.getElementById("root"));
```