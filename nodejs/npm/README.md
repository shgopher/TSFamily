<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-14 16:34:09
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-14 16:41:23
 * @FilePath: /TSFamily/nodejs/npm/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# npm 基础操作

好的，下面是 npm 常用命令的示例：

1. **初始化新项目**

```bash
npm init
# 或者快速初始化
npm init -y
```

2. **安装依赖包**

```bash
# 安装最新版本的包
npm install <package_name>

# 安装特定版本的包
npm install <package_name>@<version>

# 安装包并添加到 dependencies
npm install <package_name> --save

# 安装包并添加到 devDependencies
npm install <package_name> --save-dev

# 全局安装
npm install <package_name> -g
```

3. **更新依赖包**

```bash
# 更新指定的包
npm update <package_name>

# 更新所有包
npm update
```

4. **卸载依赖包**

```bash
# 卸载包并从 dependencies 中移除
npm uninstall <package_name> --save

# 卸载包并从 devDependencies 中移除
npm uninstall <package_name> --save-dev

# 卸载全局包
npm uninstall <package_name> -g
```

5. **运行脚本**

```bash
# 运行 start 脚本
npm start

# 运行 test 脚本
npm test

# 传递参数给脚本
npm run <script_name> -- --my-argument=value
```

6. **查看包信息**

```bash
# 查看已安装的包
npm list

# 查看某个包的信息
npm view <package_name>

# 查看可更新的包
npm outdated
```

7. **清理缓存**

```bash
npm cache clean --force
```

8. **修改配置**

```bash
# 设置配置
npm config set <key> <value>

# 获取配置
npm config get <key>

# 删除配置
npm config delete <key>
```

9. **发布包**

```bash
# 登录 npm 账号
npm login

# 发布公共包
npm publish

# 发布私有包
npm publish --access=restricted
```

10. **其他命令**

```bash
# 查看帮助
npm help

# 检查 npm 版本
npm -v

# 查看安装路径
npm root -g
```

这些是 npm 常用的一些命令和用法，涵盖了包的安装、更新、卸载、脚本管理、配置修改等多个方面。可以通过 `npm help <command>` 查看每个命令的更多信息和选项。

## 详细命令
- [npm help install](./npm-install.md)