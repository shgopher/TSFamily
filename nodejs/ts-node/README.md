<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 01:22:03
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-01-24 01:55:27
 * @FilePath: /TSFamily/nodejs/ts-node/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 使用 ts 去开发 nodejs


安装 ts 到当前项目中
```bash
npm i -D typescript
```
这句命令会执行几件事情：

- 下载并安装最新版本的 TypeScript 到当前项目的 node_modules 目录中
- 在 package.json 中的 devDependencies 列表中添加 TypeScript 依赖记录
- 允许在项目中通过 import 或 require 来使用 TypeScript

运行 typescript 代码，编译为 js，然后再用 nodejs 去运行 js 代码
```bash
npx tsc example.ts

node example.js
```
这里的 npx 代表 Node Package Execute。这个工具允许我们运行 TypeScript 的编译器，而无需全局安装它。

如果你想直接使用 ts 而不是现编译为 js 代码再运行，可以使用 ts-node

```go
npm i -g ts-node

ts-node index.ts
```
