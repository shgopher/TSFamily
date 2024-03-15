<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-14 22:35:56
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-14 22:38:11
 * @FilePath: /TSFamily/nextjs/install/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# nextjs 安装
安装 Next.js 的步骤如下：

1. **确保你已经安装了 Node.js**
Next.js 需要 Node.js 版本 >= 10.13。你可以在终端运行 `node -v` 来检查你当前安装的 Node.js 版本。如果你还没有安装 Node.js，请访问 [Node.js 官网](https://nodejs.org/en/)下载并安装合适的版本。

2. **创建一个新的 Next.js 应用**
打开你的终端，切换到你想创建项目的目录，然后运行以下命令来创建一个新的 Next.js 应用：

```bash
npx create-next-app@latest
# or
yarn create next-app
```

上面命令会创建一个新的 Next.js 应用，并安装所有必需的依赖项。

3. **启动开发服务器**
Next.js 应用创建完毕后，你可以切换到这个项目目录，并运行以下命令来启动开发服务器：

```bash
npm run dev
# or
yarn dev
```

这会在 `http://localhost:3000` 启动一个热重载的开发服务器，你可以在浏览器中访问并查看结果。

4. **开始编码**
Next.js 应用的目录结构类似于：

```
project-name
├── node_modules
├── pages
│   └── index.js
├── public
├── package.json
└── yarn.lock
```

你可以在 `pages` 目录下编写 React 组件，这些组件会自动与路由关联。要了解更多 Next.js 的工作原理以及高级用法，请查看 [Next.js 文档](https://nextjs.org/docs)。

总的来说，Next.js 提供了开箱即用的服务端渲染、静态网站生成、文件系统路由等功能，使得构建 React 应用更加简单高效。