<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:19:42
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-01-30 19:01:31
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

