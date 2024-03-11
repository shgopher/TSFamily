<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-06 17:50:28
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-11 22:36:56
 * @FilePath: /TSFamily/ts/装饰器/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 装饰器

这个就跟 arkts 中的装饰器很像了

装饰器是一种特殊的声明，它附加到类，方法，属性，访问器等内容上，增加原本组建的内容，行为，为其添加内容

装饰器使用 @expression 这种形式，expression 必须是一个将被调用的函数，它会在运行时被调用，被装饰的声明信息将作为参数传入。

```ts
// 定义一个装饰器函数
function logClass(target: Function) {
  console.log('Class decorated:', target);
}

// 定义一个装饰器工厂函数
function logParameter(target: Object, propertyKey: string | symbol, parameterIndex: number) {
  console.log('Parameter decorated:', target, propertyKey, parameterIndex);
}

// 装饰类
@logClass
class Person {
  private name: string;

  constructor(name: string) {
    this.name = name;
  }

  // 装饰方法参数
  greet(@logParameter message: string) {
    console.log(`Hello, ${message}`);
  }
}

const person = new Person('John');
person.greet('world'); // 输出: Parameter decorated: ... // 输出: Hello, world
```

在这个示例中：

- logClass 是一个装饰器函数，它会在编译期间被调用，并将被装饰的类作为参数传入。
- logParameter 是一个装饰器工厂函数，它返回一个装饰器，用于装饰方法参数。
- 使用 @logClass 语法将 logClass 装饰器应用到 Person 类上。
- 使用 @logParameter 语法将 logParameter 装饰器应用到 greet 方法的 message 参数上。

装饰器的执行顺序是从上到下，从右到左。当实例化 Person 类时，会先执行 logClass 装饰器，输出 Class decorated： ...。当调用 greet 方法时，会先执行 logParameter 装饰器，输出 Parameter decorated： ...。

## 类装饰器
```ts
function Sealed(constructor: Function) {
    Object.seal(constructor);
    Object.seal(constructor.prototype);
}

@Sealed
class Greeter {
    constructor(public greeting: string) {}
    greet() {
        return "Hello, " + this.greeting;
    }
}

```
## 方法装饰器
```ts
function Log(target: Object, propertyKey: string, descriptor: TypedPropertyDescriptor<any>) {
    let originalMethod = descriptor.value; // 保存原始函数
    descriptor.value = function (...args: any[]) {
        console.log("Arguments: ", JSON.stringify(args));
        let result = originalMethod.apply(this, args);
       

 console.log("Result: ", result);
        return result;
    }
}

class Calculator {
    @Log
    add(x: number, y: number): number {
        return x + y;
    }
}

```
## 访问器装饰器
```ts
function ReadOnly(target: any, key: string, descriptor: PropertyDescriptor) {
    descriptor.writable = false;
    return descriptor;
}

class Circle {
    private _radius: number;

    constructor(radius: number) {
        this._radius = radius;
    }

    @ReadOnly
    get radius() {
        return this._radius;
    }
}

```
