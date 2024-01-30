<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:18:55
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-01-30 16:04:51
 * @FilePath: /TSFamily/ts/接口/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 接口
ts 中的接口跟 go 那是大不相同，go 的接口是抽象方法，ts 的接口是类型

```go
type MyAge interface {
  Method1(x int,y int)(value int,err error)
  Method2()error
}
```

```ts
interface MyAge {
  name :string
}
function mysage(m :MyAge){
  console.log(m.name)
}
let obj = {
  name : 'shgopher',
  year : 1990,
}
mysage(obj)
```
通过上面的案例你应该也发现了，ts 中的接口也是鸭子理论，只要实现的数据符合接口，那么就相当于实现了接口

ts 中接口还能描述函数，不过跟 go 不同，它就是想表示这个函数而已
```ts
interface myF {
    (name :number):number
}
let f:myF = (name:number) => name
console.log(f(12))
```

接口还可以描述数组和索引类型
```ts
interface myArrar{
  [index:number]:string
}
interface MyMap {
  [index:string]:string
}
```