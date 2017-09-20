
###   export  import





### 数组的解构赋值
```js
let [a, b, c] = [1, 2, 3];
```

### 对象的解构赋值

```js
let { foo, bar } = { foo: "aaa", bar: "bbb" };
```


### ...

```js
var todo = {id: 0, text: "sdfasdf", completed: false};
var b = {...todo, completed: !todo.completed}
```

### Object.assign()  合并对象

```js
Object.assign(target, source1, source2);
```

### Object.keys(), Object.values(), Object.entries()

```js
var obj = { foo: 'bar', baz: 42 };
Object.keys(obj)
// ["foo", "baz"]
```

```js
let {keys, values, entries} = Object;
let obj = { a: 1, b: 2, c: 3 };

for (let key of keys(obj)) {
  console.log(key); // 'a', 'b', 'c'
}

for (let value of values(obj)) {
  console.log(value); // 1, 2, 3
}

for (let [key, value] of entries(obj)) {
  console.log([key, value]); // ['a', 1], ['b', 2], ['c', 3]
}```



### Date
```js
//在ES5之中，如果日期采用连词线（-）格式分隔，且具有前导0，JavaScript会认为这是一个ISO格式的日期字符串，导致返回的时间是以UTC时区计算的。
new Date('2014-01-01')
// Wed Jan 01 2014 08:00:00 GMT+0800 (CST)
new Date('2014-1-1')
// Wed Jan 01 2014 00:00:00 GMT+0800 (CST)


但是，ES6改变了这种做法，规定凡是没有指定时区的日期字符串，一律认定用户处于本地时区。

总之，对于YYYY-MM-DD形式的字符串，JavaScript引擎可能会将其当作ISO格式来解析，采用格林尼治时区作为计时标准；而对于其他格式的日期字符串，一律视为非ISO格式，采用本地时区作为计时标准。

new Date('2014-12-11')
// Thu Dec 11 2014 08:00:00 GMT+0800 (CST)
new Date('2014/12/11')
// Thu Dec 11 2014 00:00:00 GMT+0800 (CST)
```