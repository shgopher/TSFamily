<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:19:22
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-01-30 16:20:12
 * @FilePath: /TSFamily/ts/类/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 类

```ts
class People {
  hi:string
  constructor(message:string){
    this.hi = message
  }
  greet(){
    console.log(this.hi)
  }
}
let a = new People('hi')
a.greet()
```
## 类的访问权限
默认是 public，可以使用 protected，private

- public 公开类：所有人都能访问
- protected 保护类：class 内部访问，以及子类中访问
- private 私有类：仅仅 class 自己内部访问

## 继承
ts 使用 extends 关键字实现继承，使用 super 关键字调用父类构造函数
```ts
class Student {
  name:string
  protected sex:string
   private age:number
  constructor(name:string,age:number,sex:string){
    this.name = name
    this.age = age
    this.sex = sex
  }
}
class grade1 extends Student {
  private school: string
  constructor(name:string,age:number,sex:string,school:string){
    // 继承父类构造函数
    super(name,age,sex)
    this.school = school
  }

hi() {
  return this.sex
}
}
let p = new Student('shgopher',18,'男','一高')
```

## 抽象类
抽象类只能作为基类，不能实例化

```ts
abstract class People {
  abstract hi():void
  greet(){
    console.log("Hello")
  }
}
class students extends People {
  hi(){
    console.log("hi")
  }
}
let p = new students()
p.greet()
p.hi()
```