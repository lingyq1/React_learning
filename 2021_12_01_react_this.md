# 关于react组件的this

- JavaScript函数中的this不是在函数声明的时候，而是在函数运行的时候定义的；
- 同样，React组件也遵循JavaScript的这种特性，所以组件方法的‘调用者’不同会导致this的不同（这里的 “调用者” 指的是函数执行时的当前对象）
- react.createClass有一个内置的魔法，可以自动绑定所用的方法，使得其this指向组件的实例化对象，但是其他JavaScript类没有这种特性。
- 故React团队决定不再React组件类中实现自动绑定，把上下文转换的自由权交给开发者；
- 我们通常在构造函数中绑定方法的this指向。

```js
import React from "react";

const STR = '被调用，this指向：';

class App extends React.Component{
  constructor(){
    super();
  /* 手动将this.handler()绑定为组件实例
      this.handler = this.handler.bind(this);
  */

  }

  /*测试函数*/
  handler(){
    console.log(`handler ${STR}`,this);
  }

   render(){
        console.log(`render ${STR}`,this);

        this.handler();
        window.handler = this.handler;
        window.handler();

        return(

            <div>
                <h1>hello World</h1>
                <label htmlFor = 'btn'>单击打印函数handler中this的指向</label>
                <input id = "btn" type="button" value = '单击' onClick = {this.handler}/>
            </div>        
        )
}
}

export default App;
```

## 关于this的指向

1. render()以及componentDIdMount()、componentDIdUpdate()等其他生命周期函数中的this都是组件实例 App；
2. this.handler()的调用者，为render（）中的this，所以打印组件实例 App；
3. window.handler()的“调用者”，为window，所以打印window；

4. 关于 onClick={this.handler}

> 没手动绑定，会指向 undefined,因为onClick={this.handler}的“调用者”为事件绑定，来源多样，这里打印undefined。

alt[no_bind](./img/no_bind.png)

> 手动绑定的结果：

alt[bind](./img/bind.png)
