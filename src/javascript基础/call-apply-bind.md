# call apply bind 三者的异同

- 三者都是函数原型特有的方法，可以改变this指向
- this 默认指向运行时的对象，如果没有就是window
- call 和 apply 会立即执行
- call 可以有很多个参数
- apply 最多两个参数，且第二个参数是数组
- bind 不会立即执行，会返回一个新函数，创建一个新函数


### 使用场景和好处

- 改变this指向
- 复用对象的逻辑，对象之间有相同属性，以及相同操作属性的方法
- 便捷传参

```javascript
// Math.max(arg1, arg2 , arg3, ...)

const arr = [2, 6, 1, 3, 2]
Math.max.apply(null, arr)

```

- bind改变对象运行时的this指向
    - react类组件方法
        - 为什么需要bind
        - this.handleClick.bind(this) 两个this分别指什么
    - 防抖动函数使用到外部变量时


```javascript
var x = 2 
const obj = {
    x: 1
    handleClick: function () {
        return this.x
    }
}

const temp = obj.handleClick
temp()
```



