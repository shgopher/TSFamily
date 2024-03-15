<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-12 21:59:48
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-16 00:26:44
 * @FilePath: /TSFamily/react/basic/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# react 基础
## 使用脚手架安装 react

```bash
yarn create react-app my-app
```
## 插值
```jsx
// app.js

function App(){
  const divContent = '内容'
  const divTitle = '题目'
  const flag = true
  const list  = [
    {id:1,name:"1"}, {id:2,name:"2"}, {id:3,name:"3"}
    ]
  const listContent = list.map(item => (
      <li key={item.id}>{item.name}</li> // 在jsx中只要是变量嵌入到html中的情况，一律使用 {} 插值操作
  ))

  const [tdata,setData] = useState(
    [
      {
        title:'标题1',
        data:'内容1'
      },
      {
        title:'标题2',
        data:'内容2'
      },
      {
        title:'标题3',
        data:'内容3'
      }
    ]
  )
  // 这里注意哦，省略了  return {} 这个东西 后面接的就是直接为返回值
  // 所以原本应该是这样的

  // tdata.map(function(item){
  // return ( <li key={item.title}> {item.data}</li>)
  //})
  const myData = tdata.map(item=>(
      <li key={item.title}> {item.data}</li>
  ))


  let divPop = ''

  if (flag) {
    // 这里很神奇吧，不用加上 ''  这就是jsx 一种 js和 html结合在一起的写法
    divPop = <h1> 确实</h1>
  }else {
    divPop = <h2>是的是的</h2>
  }

  return (
    // react jsx 必须只能有一个根元素，所以这里只能有一个div
    // 在jsx区域必须使用  {/* 在jsx中只要是变量嵌入到html中的情况，一律使用 {} 插值操作 */} 这种方法注释
    // 非jsx区域就可以使用 // 即可
    <div tile={divTitle}>
      {divTitle}
      <hr/>
      {/*  */}
      {divContent}
      <hr/>
      {divPop}
      <ul>
        {myData}
      </ul>
      <ul>
        {listContent}
      </ul>
    
    </div>
  )
}
```