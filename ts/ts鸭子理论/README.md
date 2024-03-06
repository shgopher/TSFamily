<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-06 17:48:07
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-06 22:00:39
 * @FilePath: /TSFamily/ts/ts鸭子理论/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 鸭子理论
跟 go 的概念一致，都是讨论接口的实现

```ts
interface RWeader {
  read:()=>void;
  write:()=>void;
}

function Do(r:RWeader){
  r.read()
  r.write()
}

const Duck = {
  read: () => console.log("Duck read"),
  write: () => console.log("Duck write"),
  t: () => console.log("Duck t")
}

Do(Duck)
```
跟 go 概念基本一致

## 与 js 的操作

比如我们需要调用一个 js 的对象 `const jsArray = [1,2,3]`

那么 jsArray 拥有一个 forEach 方法对吧，我们只需要生命一个接口，它拥有这个方法即可

```ts
interface a {
  forEach:(callback:(item:any)=> void)=>void;
}
function d(a1:a){
  a1.forEach((item:any)=>{console.log(item)})
}
// js
const jsArray = [1,2,3]
d(jsArray)
```