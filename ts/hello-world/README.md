<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:13:04
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-01-24 01:13:10
 * @FilePath: /TSFamily/ts/hello-world/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# TypeScript Hello wrold
hello world
```ts
function helloWorld():void{
    console.log('hello world')
}
// hello world
helloWorld()
```
下面让我们看一个稍微复杂一些的例子，可以了解更多 ts 相关的一些核心语法
```ts
// 基本类型
let name: string = 'Tom'
let age: number = 25

// 函数
function sayHello(name: string): void {
  console.log(`Hello ${name}!`)
}

sayHello(name)

// 接口
interface Person {
  name: string
  age: number
}

// 类
class Student {
  name: string
  age: number
  
  constructor(name: string, age: number) {
    this.name = name
    this.age = age
  }

  hello() {
    console.log(`Hi, my name is ${this.name}`)
  }
}

let stu = new Student('Jack', 20)
stu.hello()

// 模块
import {A} from './moduleA'

let a = new A()  
a.helloA()
```
你看到的就是一个基本的 TypeScript 代码示例，你只需要在命令行运行 `tsc *.ts` 就可以编译成 JavaScript 代码，然后在浏览器中运行

众所周知，ts 是 js 的一个改良，下面我们分析一下到底改良了什么部分

TypeScript 比 JavaScript 好的地方主要体现在以下几点：

1. 类型系统

TypeScript 引入了静态类型，可以在编译阶段就发现大部分错误，提高了代码质量和可维护性。比如接口、类、泛型等类型系统都使代码更具可读性和内在逻辑。

2. 更新的语言特性

TypeScript 相比 ES5/ES6 提供了许多新的语言特性，如枚举、装饰器等。这些特性可以编写出更简洁优雅的代码。


3. 支持最新和未来的 JavaScript 特性

TypeScript 提供最新的 JavaScript 特性比如切片、Promise 等。还可以翻译未来的提案比如元组类型到当前版本 JavaScript，可以提前使用新特性。

接下来让我们开始 ts 的正式学习
