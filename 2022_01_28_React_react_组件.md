## React 组件间数据传递

1. 关于 Context 的用法:

<App> > <Node> > <SubNode> > {Child}
Context 可以直接从<App>到<Child>

```js
const { Provider, Consumer } = React.createContext();
class App extends React.Component {
  render() {
    return (
      <Provider value={"Anzo"}>
        <div className="app">
          <Node />
        </div>
      </Provider>
    );
  }
}
const Node = (props) => {
  return (
    <div className="node">
      <SubNode />
    </div>
  );
};

const SubNode = (props) => {
  return (
    <div className="node">
      <Child />
    </div>
  );
};
const Child = (props) => {
  return (
    <div className="child">
      <Consumer>{(data) => <span>我是子节点:{data}</span>}</Consumer>
    </div>
  );
};
```
