### createSagaMiddleware(...sagas)

创建一个 Redux 中间件，将 Sagas 与 Redux Store 建立连接。

sagas: Array - Generator 函数列表


### middleware.run(saga, ...args)

动态执行 saga。用于 applyMiddleware 阶段之后执行 Sagas。

saga: Function: 一个 Generator 函数
args: Array: 提供给 saga 的参数 (除了 Store 的 getState 方法)
这个方法返回一个 Task 描述对象



## Effect 创建器
以下每个函数都会返回一个 plain Javascript object (纯文本 Javascript 对象) 并且不会执行任何其它的操作。 执行是由 middleware 在上述迭代过程中进行的。 middleware 检查每个 Effect 的信息，并进行相应的操作。

### take(pattern)

创建一条 Effect 描述信息，指示 middleware 等待 Store 上指定的 action。 Generator 会暂停，直到一个与 pattern 匹配的 action 被发起。


### put(action)

创建一条 Effect 描述信息，指示 middleware 发起一个 action 到 Store。

### call(fn, ...args)

创建一条 Effect 描述信息，指示 middleware 调用 fn 函数并以 args 为参数。

fn: Function - 一个 Generator 函数, 或者返回 Promise 的普通函数

args: Array - 一个数组，作为 fn 的参数


### call([context, fn], ...args)

类似 call(fn, ...args)，但支持为 fn 指定 this 上下文。用于调用对象的方法。


### apply(context, fn, args)

类似 call([context, fn], ...args)


### fork(fn, ...args)

创建一条 Effect 描述信息，指示 middleware 以 无阻塞调用 方式执行 fn。

参数

fn: Function - 一个 Generator 函数, 或者返回 Promise 的普通函数

args: Array - 一个数组，作为 fn 的参数


### 


### 


### 


### 



### takeEvery 

takeEvery 允许处理并发的 action（译注：即同时触发相同的 action）
takeEvery 不会对多个任务的响应返回进行排序，并且也无法保证任务将会按照启动的顺序结束。如果要对响应进行排序，可以关注以下的 takeLatest。

### takeLatest

在发起的 action 与 pattern 匹配时派生指定的 saga。并且自动取消之前启动的所有 saga 任务（如果在执行中）。

