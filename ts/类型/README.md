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
所以，在 ts 中，不要使用 var 作为变量声明，除非你有特殊需求 0
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
never 类型表示的是那些永不存在的值的类型，

never 的概念在 go 中并没有被提及，它是所有类型的子类型，也就是说，任何类型都不能赋值给 never 类型
  ```ts
  function error(message: string): never {
    throw new Error(message)
    }
  ```
下面这个函数的返回值就是 never，因为它永远都没有返回值
### any
any 可以接受任意类型的值，这跟 go 语言的 any 是一个意思

any 和下文提到的 unknown 都属于顶层类型，也就是说能接受所有类型的父类型，这跟 go 的定义也是一样的

表示 any 类型，可以容纳所有值
  ```ts
  let a: any = 123
  ```
例如这里的 123 会被认为是 number 类型，但是，如果使用了 any 类型，那么，123 会被认为是 any 类型
### unknown
any 类型对应的安全类型，unkown 类型的变量只能被赋值给 any 类型和 unknow 类型
  ```ts
  let a:unkown 
  a = 12
  a = true
  ```

unknown 跟 any 不一样，在操作 unknown 类型的时候，必须进行断言，不断言不能进行操作
```ts
let u:unkown = 12

// ❌
u.fool()

// 必须进行断言才可以操作
// ✅
(u as number).fool()
```
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
    Red= "r",
    Blue ="b" ,
    Green="g",
  }
  let c: Color = Color.Red
  // 设置 enum 类型初始值,
  enum Color1 {
    Red = 1,// 依次递增
    Blue ,
    Green ,
  }
  let c1: Color1 = Color1.Red
```
```ts
interface a{
  v :string
}
interface b {
  x:number
}
enum shark {
  a,
  b,
}
// 这种用法就跟go中的组合一个意思了
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

它可以作用于原始值，联合类型，以及交叉类型等任何类型

```ts
type aliasBool = boolean

function age():void{
  let b:aliasBool = true
}
age()
```
## 高级类型
### 映射类型
在编译时转换已知类型的属性并且创建一个新的类型，可以对已知类型的属性进行转换修改或者添加，比如将属性变成只读类型或者可选类型
```ts
type NewType = {
  [Property in keyof ExistingType]:TransformType;
}
```
- NewType 是要创建的新类型
- property 是 ExistingType 的键
- TransformType 是对应属性的转换类型

例如我们看一下实例：
```ts
type Readonly<T> = {
  readonly [P in keyof T]:T[P];
}
```
```ts
// 接口
interface People {
  name:string;
  age:number;
}
// 类型别名
type ReadonlyPerson = Readonly<People>
const person:ReadonlyPerson = {
  name:"123",
  age:123,
}
```
- Partial 内置映射类型，将属性变成可选
  ```ts
  type Partial<T> = {
    [P in keyof T]?:T[P];
  }
  ```
- Pick 从执行类型中选择一部分创建新类型
  ```ts
  type Pick<T,K extends keyof T> = {
    [P in K]:T[P];
    }
  ```
  ```ts
  interface Person {
  name: string;
  age: number;
  occupation: string;
  }

  type PersonInfo = Pick<Person, "name" | "age">;

  const info: PersonInfo = {
  name: "John",
  age: 30,
  };

  ```
### 条件类型
```ts
T extends U ? X : Y
```
T 是待检查的类型，U 是条件类型，X 是满足条件时返回的类型，Y 是不满足条件时返回的类型。条件类型通常与泛型一起使用，以便根据不同的类型参数值进行类型推断和转换。



### 模版字面量类型
```ts
type Greeting<T extends string> = `Hello, ${T}!`;

type GreetingWorld = Greeting<'World'>;  // GreetingWorld的类型为"Hello, World!"
```
## 类型断言
如果想告诉编译器类型推断的意图，我们可以直接断言
```ts
let value = "Hello, World!"
let length = (value as string).length
```
## 类型守卫
类型守卫用在运行时检查变量的类型，并缩小变量类型的范围，类型收窄可以让 ts 编译器更好的理解代码的意图
### typeof 类型守卫
```ts
function printbValue(value:string | number){
  // 我们发现其实 value 是联合类型，类型还不够窄，我们可以使用typeof 进一步缩短
  if(typeof value === "string"){
    console.log(value.length)
  }else {
    console.log(value)
  }
}
```
### instanceof 类型守卫
instanceof 类型守卫，可以用来判断某个值是否为某个类的实例

```ts
class Animal {
  move(){
    console.log("Animal is moving")
  }
}
class Dog extends Animal {
  bark(){
    console.log("Dog is barking")
  }
}
func printDogValue(animal:Animal){
  if (animal instanceof Dog){
    animal.bark()
  }else {
    animal.move()
  }
}
```
### 自定义谓词函数类型守卫
```ts
interface Circle{
  kind:'Circle';
  radius: number;
}
interface Rectangle{
  kind:'Rectangle';
}
type Shaple = Circle | Rectangle

function calculateArea(shape: Shape) {
  if (isCircle(shape)) {
    console.log(Math.PI * shape.radius ** 2);
  } else {
    console.log(shape.width * shape.height);
  }
}

// 其中这一句 shape is Circle 是一个断言，也是告诉编译器我们要检查的是shap的类型
//TypeScript 编译器会根据这个返回值类型断言推断调用此函数后的变量就是 Circle 类型，
// 增强了编译时类型检查的安全性。
function isCircle(shape: Shape): shape is Circle {
  return shape.kind === 'circle';
}
```
### 联合类型守卫
这个跟 go 的 switch 断言语句类似

```ts
interface Car {
  type: 'car';
  brand: string;
  wheels: number;
}

interface Bicycle {
  type: 'bicycle';
  color: string;
}

interface Motorcycle {
  type: 'motorcycle';
  engine: number;
}

type Vehicle = Car | Bicycle | Motorcycle;

function printVehicleInfo(vehicle: Vehicle) {
  switch (vehicle.type) {
    case 'car':
      console.log(`Brand: ${vehicle.brand}, Wheels: ${vehicle.wheels}`);
      break;
    case 'bicycle':
      console.log(`Color: ${vehicle.color}`);
      break;
    case 'motorcycle':
      console.log(`Engine: ${vehicle.engine}`);
      break;
    default:
      const _exhaustiveCheck: never = vehicle;
  }
}
```
### in 操作符进行类型守卫
in 判断某个属性是否在某个类型中
```ts
interface Circle {
  kind: 'circle';
  radius: number;
}

interface Rectangle {
  kind: 'rectangle';
  width: number;
  height: number;
}

type Shape = Circle | Rectangle;

function printArea(shape: Shape) {
  if ('radius' in shape) {
    console.log(Math.PI * shape.radius ** 2);
  } else {
    console.log(shape.width * shape.height);
  }
}
```
### 真值类型守卫
当条件表达式的结果是 true 的时候，收窄类型
```ts
function isV(value:string|null){
  if (value){
    console.log(value.length)
  }else{
    console.log('value is null')
  }
}
```
### 自定义类型判断守卫
```ts
interface Bird {
  fly(): void;
}

interface Fish {
  swim(): void;
}

// 最后的一句是断言语句，同时它也是一个布尔类型
function isBird(animal: Bird | Fish): animal is Bird {
  return (animal as Bird).fly !== undefined;
}
```
## 参考资料
- https://typescriptlang.org
- https://www.coding-time.cn/

