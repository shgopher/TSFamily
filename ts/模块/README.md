<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:19:42
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-02-21 00:22:04
 * @FilePath: /TSFamily/ts/模块/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 模块
## 命名空间
```ts
namespace tsfamily{
  export const va:number = 10
  export function myage():void {
    console.log("my age is 10")
  }
}

使用的时候

tsfamily.myage()
```
命名空间还可以嵌套
```ts
namespace tsfamily{
  namespace myage{
    export function myag(age: number):void {
      console.log("my age is " + age)
    }
  }
}
tsfamily.myage.myag(10)
```
命名空间用的很少，尽量别用
## 模块

每个模块都有自己的作用域，只有明确导出的部分才能在其它模块中使用，如果跟go语言作类比的话，go自带模块，同一个package下的就是一个模块，开头大写就默认可导出。

创建模块
```ts
// myModule.ts
export const myDate: numer = 10
export function myFunction():void {
  console.log("my function")
}
```
导入并使用模块
```ts
import {myDate, myFunction} from "./myModule"

myFunction() 
```
