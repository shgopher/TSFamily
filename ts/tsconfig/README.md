<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-01-24 00:20:11
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-01-24 00:20:17
 * @FilePath: /TSFamily/ts/tsconfig/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# ts config

```ts
{
  // 指定编译器将编译的TypeScript文件版本
  "target": "es6",

  // 指定生成哪个模块系统代码
  "module": "commonjs",

  // 启用严格类型检查
  "strict": true,

  // 允许编译未使用的本地变量或函数
  "allowUnusedLabels": false,

  // 报告使用过的标签错误
  "allowUnreachableCode": false,

  // 如果编译器检测到文件使用不同版本的库,就会发出警告
  "alwaysStrict": true,

  // 是否检查周围文件,并记录视为错误的文件
  "assumeChangesOnlyAffectDirectDependencies": false,

  // 当使用 --build 时,遇到出错则会终止
  "baseUrl": ".",

  // 不生成jspm程序包
  "declaration": true,

  // 生成相应的 '.d.ts' 文件
  "declarationDir": "./types",

  // '.d.ts'文件输出目录
  "diagnostics": true,

  // 显示诊断信息
  "downlevelIteration": true,

  // 为for...of, spread, 和generator,生成ES5代码
  "emitBOM": false,

  // 在输出文件开头加上BOM头(UTF-8 Byte Order Mark)
  "emitDecoratorMetadata": true,

  // 给源码里的装饰器声明加上设计类型元数据
  "experimentalDecorators": true,

  // 使用装饰器特性
  "forceConsistentCasingInFileNames": true,

  // 禁止对同一个文件使用不一致的大小写
  "importHelpers": true,

  // 引入tslib导入助手函数,编译后的JS文件体积会变小
  "incremental": true,

  // 增量编译,一旦文件被编译过,就往osncreat文件里写一个记录文件
  "inlineSourceMap": true,

  // 生成单个SourceMaps文件,而不是将每个文件 都生成 '.map' 文件
  "inlineSources": true,

  // 将代码和sourceMap生成到一个文件
  "isolatedModules": true,

  // 无条件的给没有导入语句的文件生成imports
  "jsx": "preserve",

  // 在'.tsx'文件里支持 JSX
  "lib": [],

  // 编译工程所需要的库文件列表
  "listEmittedFiles": false,

  // 打印出编译后被传出文件的路径
  "listFiles": false,

  // 打印出编译文件及其源文件的名称
  "maxNodeModuleJsDepth": 0,

  // node_modules依赖的编译失败时抛出错误
  "module": "commonjs",

  // 指定生成哪个模块系统的代码
  "moduleResolution": "node",

  // 决定如何处理模块
  "newLine": "lf",

  // 在生成文件时的当行符使用符号
  "noEmit": true,

  // 不生成输出文件
  "noEmitHelpers": false,

  // 不在输出文件中生成用户自己定义的帮助类
  "noEmitOnError": false,

  // 发生错误时不生成输出文件
  "noErrorTruncation": false,

  // 不截短错误消息
  "noFallthroughCasesInSwitch": false,

  // switch语句是否报告fallthrough错误
  "noImplicitAny": true,

  // 是否默认禁用any
  "noImplicitReturns": true,

  // 不是函数的根必须有返回值
  "noImplicitThis": true,

  // 当this表示any类型时是否发出错误
  "noImplicitUseStrict": false,

  // 模块是否创建命名空间
  "noLib": false,

  // 不加载默认库文件
  "noResolve": false,

  // 不把 /// <reference``>或模块导入的文件加到编译文件里
  "noStrictGenericChecks": false,

  // 是否对没有设定默认值的泛型不适用双向协变/确变位检查
  "noUnusedLocals": false,

  // 用于 阻止对命名代码的未使用本地的定义发出警告
  "noUnusedParameters": false,

  // 用于 阻止对命名代码的未使用参数的定义发出警告
  "outDir": "./dist",

  // 指定输出目录
  "outFile": "./dist/bundle.js",

  // 将程序编译为一个文件。
  "paths": {},

  // 模块名映射，将模块重定向到另外一个路径
  "plugins": [],

  // 要从编译器加载的插件列表
  "preserveConstEnums": false,

  // 如何处理常量枚举,或为生成代码保留const枚举
  "preserveSymlinks": false,

  // 不把符号链接解析为其真实路径;应对于符号路径使用工具或者库
  "preserveWatchOutputPath": false,

  // 保留监视输出文件夹的结构
  "pretty": false,

  // 使用可读的相对路径
  "project": "./tsconfig.json",

  // 编译工程的路径
  "reactNamespace": "React",

  // 为创建对React导入的指定JSX工厂覆盖以及生成命名空间声明
  "removeComments": false,

  // 删除编译后的所有注释
  "resolveJsonModule": false,

  // 使用webpack等导入器解析扩展名为.json的文件
  "rootDir": "./",

  // 仅用来控制输出的目录结构 --outDir
  "rootDirs": [],

  // 根文件夹列表
  "skipDefaultLibCheck": false,

  // 忽略所有的声明文件的类型检查
  "skipLibCheck": false,

  // 是否忽略目录下所有的声明文件的类型检查
  "sourceMap": true,

  // 生成相应的.map文件
  "sourceRoot": "./",

  // 指定TypeScript源文件目录
  "strictBindCallApply": true,

  // 对bind/call/apply监视严格
  "strictNullChecks": true,

  // 设置为true,null和undefined值不能赋给非这两种类型的变量
  "stripInternal": false,

  // 不对内部代码用strip处理
  "suppressExcessPropertyErrors": false,

  // 阻止"不同代码单元引用互不可见的类型检查器符号"错误
  "suppressImplicitAnyIndexErrors": false, 

  // 阻止"缺少索引签名"错误
  "traceResolution": false,

  // 输出模块和目录的策略现场数据
  "tsBuildInfoFile": "./",

  // 指定生成文件的存储目录
  "typeRoots": [],

  // 包含类型声明的文件目录列表
  "types": [],

  // 要包含的类型声明的文件名列表
  "watch": true,

  // 在监听模式下运行编译器
  "version": false,

  // 打印编译器的版本
  "lib": ["es5", "es6", "dom"],

  // 需要使用的库文件列表
  "jsx": "react",

  // 指定JSX代码生成目标
  "outFile": "./dist/app.js",

  // 将输出内容合并到一个文件
  "allowJs": true,

  // 允许编译JS文件
  "checkJs": false,

  // 在在 .js 文件中报告错误,与allowJS一起使用
  "maxNodeModuleJsDepth": 1, // 最大允许依赖的node_module依赖包
  
  "allowSyntheticDefaultImports": true // 允许从没有默认导出的模块中默认导入

  // 指定要包含在编译中的文件或目录。
  "include":
    [
      "src/**/*"
    ],
  
  // 指定应排除在编译之外的文件或目录。
  "exclude": 
    [
      "node_modules",
      "**/*.spec.ts"
    ],

  // 将指定目录下的指定文件编译为一个命名空间
  "composite": true 
}
```