<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-05 22:51:14
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-06 22:17:34
 * @FilePath: /TSFamily/js/并发/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# ts js 异步解决方案 async/await

```ts
async function test() {
  try{
  let b = await nice()
  return b
  }catch(err){
    console.log(err)
  }
}
function nice() {
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
      resolve("nice")
    }, 1000)
    })
}

console.log("Testing")
test()
.then(data => console.log(data))
.catch(err => console.log(err))
console.log("Testing1")
```

输出结果：

testing
testing1
nice