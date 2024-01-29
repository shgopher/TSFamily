# 类型
在 ts 中，使用 `let` `var` 表示变量，使用 `const` 表示常量
```ts
let a: number = 1
var b: string = "12"
```
## var or let
不过，虽然 let var 都可以表示变量，但是 let 的作用域是小于 var 的，在函数体中，var 表示函数级变量，let 则表示局部变量，所以，ts 中，推荐使用 let 来定义变量，这样可以避免变量的污染。

下面我通过几个例子演示一下

```ts
function age(){
  {
    let a: number = 1
    var b: number = 2
  }
  // 你会发现，a 不可正常执行，但是 b 可以
  console.log(a, b)
}
```
var 的作用域明显是不合理的，这也是 js 中的陋习，let 表示的局部变量更加清晰，也更安全。

```ts
let a: number = 1
function age(){
  let b: string ="你好"
  console.log(a,b)
}
age()
```
所以，在 ts 中，不要使用 var 作为变量声明，除非你有特殊需求
## 常量
常量就比较常规了：
```ts
const PI:number = 3.14

function age(){
  console.log(PI)
}
```
## 变量初始化
ts 中，类型需要初始化，跟 go 等编程语言，声明就是初始化零值不同，ts 需要手动给予初始化类型
```go
// ts
let a : number = 0
// go
var a int
```
## 基础类型
ts 所拥有的基本类型如下：

### null
表示空是所有类型的子类型 (当你指定--strictNullChecks 标记，null 和 undefined 只能赋值给 void 和它们各自的类型)
  ```ts
  let a: null = null
  ```
### undefinded
表示未定义
  ```ts
  let a: undefined = undefined
  ```
### string
字符串类型，ts 跟 go 不同，go 有字符类型，ts 不管是单引号还是双引号都只表示字符串的含义，ts 使用反引号 `` 表示字符串模版，go 表示格式输出
  ```go
  //ts
  let a: string = '123'
  // go ❌，字符只能是单个字符
  var b string ='123'

  // ts
  let a: string = "123"
  // go
  var b string = "123"

  // ts
  let age: string = "world"
  let a : string = `hello${age}`

  // go
  var a string = `
      d
      dfff
  `
  ```
### number
数字类型，ts 中并没有 uint int float 的概念，统一称之为 number，实际上它是浮点数，它存在一定的精度限制和误差，特别是在进行高精度计算或涉及小数部分的操作时。因此，在金融、科学计算等领域，直接使用 number 类型可能会导致数值不精确的问题。对于金融领域需要高精度计算的应用场景，推荐使用专门处理高精度数学运算的库，比如在 TypeScript 中可以使用的 decimal.js 或 big.js 等库，这些库提供了能够准确表示和操作任意精度十进制数字的能力
  ```ts
  // 十进制
  let a: number = 123
  // 十六进制
  let a1: number = 0x123
  // 八进制
  let a2: number = 0o123
  // 二进制
  let a3: number = 0b101010
  // 浮点数
  let b: number = 123.456
  ```
### boolean
布尔类型
  ```ts
  let a: boolean = true
  let b: boolean = false
  ```
### bigint
大整数类型
  ```ts
  function age(){
    let a:bigint = 1299999499494934343443344334433443n
    let b:bigint = 443n
    console.log("d",a*b)
    // ❌ bigint和number不能混用
    console.log("d",a*2)
  }
  age()
  ```
### symbol
表示独一无二的值
  ```ts
  let a: symbol = Symbol()
  ```
### object
对象，比如数组之类的复杂数据都是对象类型
  ```ts
  let a: object = {name: "123"}
  ```
### void
表示函数返回值为空
  ```ts
  function a(): void {
  }
  ```
### never
never 类型表示的是那些永不存在的值的类型
  ```ts
  function error(message: string): never {
    throw new Error(message);
    }
  ```
### any
表示 any 类型，可以容纳所有值
  ```ts
  let a: any = 123
  ```
### unknown
any 类型对应的安全类型，unkown 类型的变量只能被赋值给 any 类型和 unknow 类型
  ```ts
  let a:unkown 
  a = 12
  a = true
  ```

其中，any unknown 类型是要慎重使用的，如果使用了 any 就跟没有使用类型一个意思了。
## 复杂类型
### array
数组类型
  ```ts

  let a: number[] = [1,2,3]
  let b: Array<number> = [1,2,3]
  ```
### tuple
元组类型
  ```ts
  let a: [number, string] = [1, "123"]
  let b: [number, string] 
  b = [1, "123"]
  ```
### enum
枚举类型
```ts
  enum Color {
    Red,
    Blue,
    Green
  }
  let c: Color = Color.Red
  // 设置 enum 类型初始值
  enum Color1 {
    Red = 1,
    Blue = 2,
    Green = 3
  }
  let c1: Color1 = Color1.Red
```
### Union Types
联合类型
```ts
  let a: number | string = 123
```
### Intersection Types
交叉类型，这个其实类似于 go 语言中的组合概念
```ts
  interface part1 {
    a:string
  }

  interface part2 {
    b:number
  }
  type Part = part1 & part2
  
  function age(p:Part){

  }
  let p:Part = {
    a:'hello',
    b:18,
  }
  age(p)
```
### String Literal Types
字符串字面量类型
```ts
let a: "123" = "123"
```
字符串字面量类型和联合类型以及类型别名结合在一起
```ts
type b = "124" |"44556"

function age(b1:b){
    console.log(b1)
}
age("124")
```
## 类型别名
类型别名，给一个类型起另外一个名字

在 ts 中类似接口的概念，但是它可以作用于原始值，联合类型，以及交叉类型等任何类型

```ts
type aliasBool = boolean

function age():void{
  let b:aliasBool = true
}
age()
```
## 参考资料
- https://typescriptlang.org
- https://www.coding-time.cn/

