<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:19:32
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-06 17:16:30
 * @FilePath: /TSFamily/ts/泛型/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 泛型

```ts
function myage<T>(age: T): T {
  return age
}
myage(12)
```
下面我们看一下 go 的泛型
```go
package main

import "fmt"

func main() {

	fmt.Println(myage("12"))
}

func myage[T int | string](t T) T {
	return t
}
```
看出来了什么？

ts 和 Java 一样都是伪泛型，只不过是类型的拆箱和装箱而已，类似于 go 的 any 反射，所以 ts 的泛型效率比较低，go 的泛型效率高，因为 go 的泛型是编译时的泛型，而 ts 的泛型是运行时的泛型，所以效率差很多

## 接口泛型

```ts
interface part<T,U>{
  first:T
  second:U 
  }
  let result:part = { first:45, second:"hello"}
```
## 类泛型
```ts
class part<T,U>{
  private second:U
  private first:T
  constructor(first:T,second:U){
    this.first = first
    this.second = second
  }
}
```
## ts 中 any 和反射

ts 中也有 any 类型，那么请问 any 跟泛型是不是一致的底层原理，反正都是运行时通过反射装箱不是吗

1. any 类型表示允许赋值为任意类型，disable 了类型检查，所以从编译原理来看，它与泛型的实现不同。

2. 泛型在编译时会进行类型推导和检查，但编译结果都会被擦除。any 类型编译时就完全禁用检查。

3. 泛型需要编译器保留部分信息用于运行时反射装箱。any 完全不需要这些信息。

4. any 可以表示任意值，泛型变量仍与指定的类型参数关联，有不同的语义约束。

5. 从实现角度，any 直接反映为动态类型，不需要反射来获取类型；泛型需要通过反射来实现运行时的类型装箱。

所以 any 类型和泛型的实现机制是不同的，前者完全动态，后者需要类型关联的元信息和反射。

总结一下，TypeScript 中的 any 类型和泛型从编译和运行时实现机制上区别很大，不能认为是相同的底层方式。any 完全动态，泛型需要类型关系和反射。
## 泛型使用省略
```ts
function identity<T>(arg: T): T {
  return arg;
}

// 可以省略类型
let output = identity(1);
```

TypeScript 的类型推断规则如下：

- 如果泛型函数的参数有类型注解，用参数的类型注解作为泛型类型
- 如果没有类型注解，则根据默认值推断类型
- 如果没有默认值，则默认为 any 类型

另外，在实例化泛型类时，如果不指定泛型类型参数，默认会使用 any 类型：

```ts

Copy code

class Generic<T> {}

let g = new Generic()
```

ts 也有约束的泛型

## extends 和类型约束

```ts
function printProperty<T extends { name: string }>(p: T) {
  console.log(p.name)
}
```
使用 extends 表示约束的内容，内容是属性叫做 name，name 的类型是 string

下面是内置的泛型约束

### Partial<T>

将类型 T 的所有属性都转化为可选属性

```ts
interface People {
  name: string;
  age: number;
}
type mP = Partial<People>

// 表示 age 属性是可选的
const dd:mP = {
  name: 'shgopher'
}
```
### Required<T>
将类型 T 的所有属性都转化为必需属性
### Pick<T,K>
从给定的 T 中选择指定的属性 K 组成一个新的类型

```ts
interface People {
  name: string;
  year:number;
  address:string;
}
type NewPerso = Pick<People,'name'|'year'>

const people:NewPerso = {
  name: 'John',
  year:2000,
} 

```