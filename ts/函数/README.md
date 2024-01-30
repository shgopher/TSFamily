<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:19:10
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-01-30 15:48:33
 * @FilePath: /TSFamily/ts/函数/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 函数
```ts
func age(x:mumber,y:number):number{
  return x+y
}
```
这是一个基础的函数表达方法
## 函数作为类型
```ts
let myFunc:(x:number,y:number) => number = function(x:number,y:number) :number{
  return x+y
}
```
基本上没啥必要这么写，不推荐这种写法
## 可选参数
```ts
function myage(x:number,y?:number):number{
  if (y){
    return x+y
  } 
  return x
}
// 3
myage(1,2)
// 1
myage(1)
```
## 默认参数
```ts
function myage(x:number,y = 12){
  console.log(x+y)
}
// 3
myage(1,2)
// 12
myage(0)
```
## 不定参数
这个概念跟 go 一致
```ts
function myage(x:number, ...restNumber: Array<number>){
    console.log(x,restNumber.join(" "))
}

myage(1,2,3,4,5)
```
不过要注意的是，如果是 go 写法是不同的：
```go
package main

import "fmt"

func main() {
	myage(1, 2, 3, 34, 4)
}
func myage(x int, restNumber ...int) {
	fmt.Println(x, restNumber)
}
```
## 剪头函数保留函数创建时的 this 值
```ts
let myage = {
  name:["li","zhang"],
  age:Array(40),

  createStudent: function(){
    return ()=>{
      
      return {
        name:this.name,
        age:ag
      }
    }
  }
}
```
