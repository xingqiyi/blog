

数据的改变发生通常是通过用户交互行为或者浏览器行为（如路由跳转等）触发的，

当此类行为会改变数据的时候可以通过 dispatch 发起一个 action，

如果是同步行为会直接通过 Reducers 改变 State ，

如果是异步行为（副作用）会先触发 Effects 然后流向 Reducers 最终改变 State，
 
<img src="https://zos.alipayobjects.com/rmsportal/PPrerEAKbIoDZYr.png" width="807" />


### 组件定义

React Component 有 3 种定义方式 
React.createClass, class 和 Stateless Functional Component。

推荐尽量使用最后一种，保持简洁和无状态。

这是函数，不是 Object，没有 this 作用域，是 pure function。
```js
function App(props) {
  function handleClick() {
    props.dispatch({ type: 'app/create' });
  }
  return <div onClick={handleClick}>${props.name}</div>
}
//等同于：

class App extends React.Component {
  handleClick() {
    this.props.dispatch({ type: 'app/create' });
  }
  render() {
    return <div onClick={this.handleClick.bind(this)}>${this.props.name}</div>
  }
}
```




### 定义全局 CSS
CSS Modules 默认是局部作用域的，想要声明一个全局规则，可用 :global 语法。
 
 ```css
.title {
  color: red;
}
:global(.title) {
  color: green;
}
/* 然后在引用的时候： */
<App className={styles.title} />   /* red */  
<App className="title" />          /* green */  
```


### classnames Package
在一些复杂的场景中，一个元素可能对应多个 className，而每个 className 又基于一些条件来决定是否出现。这时，classnames 这个库就非常有用。

```jsx
import classnames from 'classnames';
const App = (props) => {
  const cls = classnames({
    btn: true,
    btnLarge: props.type === 'submit',
    btnSmall: props.type === 'edit',
  });
  return <div className={ cls } />;
}
// 这样，传入不同的 type 给 App 组件，就会返回不同的 className 组合：

<App type="submit" /> // btn btnLarge
<App type="edit" />   // btn btnSmall
```


### 1. Reducer 
reducer 是一个函数，接受 state 和 action，返回新的 state 。
即：(state, action) => state

### 2. Effect

示例:
```jsx
app.model({
  namespace: 'todos',
  effects: {
    *addRemote({ payload: todo }, { put, call }) {
      yield call(addTodo, todo);
      yield put({ type: 'add', payload: todo });
    },
  },
});
```




- put  用来发起一条action
- call 以异步的方式调用函数
- select 从state中获取相关的数据
- take 获取发送的数据

### 3. Subscription
用于订阅一个数据源，然后根据需要 dispatch 相应的 action。

示例: 当用户进入 /users 页面时，触发 action users/fetch 加载用户数据。
```jsx
app.model({
  subscriptions: {
    setup({ dispatch, history }) {
      history.listen(({ pathname }) => {
        if (pathname === '/users') {
          dispatch({
            type: 'users/fetch',
          });
        }
      });
    },
  },
});

```