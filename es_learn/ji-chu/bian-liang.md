# 变量

`var` 声明: 函数作用域

```javascript
function test() {
    var msg = "Test" // 局部变量
    console.log(msg) // Test
}
test()
console.log(msg) // undefined
```

```javascript
function test() {
    msg = "Test" // 全局变量
    console.log(msg)
}
// test() // 不先调用, msg 则会是 undefined
console.log(msg)
```

```javascript
function test() {
    console.log(msg) 
    var msg = "Hello" // 自动提升到函数作用域顶部 上面语句不会报错 
}
test() // undefined

// 所谓的“提升”（ hoist），也就是把所有变量声明都拉到函数作用域的顶部。
// 此外，反复多次使用 var 声明同一个变量也没有问题
function test() {
    var age = 18
    var age = 20
    var age = 30
    console.log(age)
}
test()
```

`let` 声明: 块作用域

```javascript
function test() {
    let age = 18
    let age = 20
    let age = 30
    console.log(age) // 报错，let声明的变量名不能反复使用
}

if (true) {
    var name = "MATT"
    console.log(name) // MATT
}
console.log(name) // MATT

if (true) {
    let age = 18
    console.log(age) // 18
}
console.log(age) // 报错
```

与 var 关键字不同，使用 let 在全局作用域中声明的变量不会成为 window 对象的属性（ var 声 明的变量则会）

`const` 声明:  块作用域

```javascript
const name // 报错
const age = 20
age = 10 // 报错

const msg = "Hello"
if (true) {
    const msg = "hello" // 块作用域 
}
console.log(msg)
```

const 的行为与 let 基本相同，唯一一个重要的区别是用它声明变量时必须同时初始化变量，且尝试修改 const 声明的变量会导致运行时错误，也不允许重复声明
