<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-06 17:49:47
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-07 00:50:37
 * @FilePath: /TSFamily/ts/扩展类型定义/README.md
 * @Descr
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# 扩展类型定义

其实就是生成 `a.d.ts` 文件

通过这个声明文件，给现有的 js 库提供类型定义，或者给现有的类型提供额外的属性和方法

类型声明主要是声明变量函数，类，接口等类型的定义

```ts
// a.d.ts

declare var foo:string
declare function bar(value:number):boolean
```
## 声明全局变量
```ts
declare const foo:string
```
## 声明全局函数
```ts
declare function myFunction(age:number):void;
```
## 声明全局类
```ts
declare class MyClass {
  constructor(age:number)
  getName():string
}
```
## 声明命名空间
```ts
declare namespace myNameSpace {
  export const myV :number;
  export function myF(age:number):void;
}
```
## 声明模块
```ts
declare module 'myModule' {
  export const myV :number;
  export function myF(age:number):void;
}
```
## 通过声明文件扩展类型定义
它允许我们在多个位置声明同名的类型，然后 TypeScript 会将这些声明合并为一个类型。

```ts
// a.d.ts

interface Array<T> {
  last:T;
}

let nums :numbers[] = [1,2,3,4]
console.log(nums.last)//4
// TypeScript 编译器默认将 last 属性解析为 arr[arr.length - 1] 是一种约定俗成的实现
```
## 给第三方库创建声明文件
在 TypeScript 中，不一定需要显式地声明类型，TypeScript 编译器可以根据代码上下文自动推断出变量或参数的类型，这被称为类型推断 (Type Inference)。

但是，如果你想将 TypeScript 代码作为包发布和分发给其他人使用，那么最好提供类型声明文件 (。d.ts)。这样做有以下几个好处：

更好的开发体验：提供类型声明文件可以让使用你的包的开发者获得良好的编辑器支持，如自动补全、跳转到定义和显示文档等。
类型安全：使用你的包的开发者可以获得类型检查，防止拼写错误和使用不当。这有助于提高代码质量和可维护性。
文档：类型声明文件可以作为代码的文档，方便其他开发者理解你的代码和 API。
工具支持：一些工具如 Webpack、Rollup 等也依赖于类型声明文件来进行优化和处理。
如果你的包是用 TypeScript 编写的，那么在构建和发布时，通常会将生成的 JavaScript 文件和编译后的类型声明文件一起发布。如果你的包是用 JavaScript 编写的，那么需要手动编写对应的类型声明文件 (。d.ts)。


```ts
declare module 'axios' {
  export interface AxiosRequestConfig {
    url: string;
    method?: string;
    data?: any;
    headers?: any;
  }

  export interface AxiosResponse<T = any> {// 提供t的默认值，any类型
    data: T;
    status: number;
    statusText: string;
    headers: any;
    config: AxiosRequestConfig;
  }

  export function request<T = any>(config: AxiosRequestConfig): Promise<AxiosResponse<T>>;
  export function get<T = any>(url: string, config?: AxiosRequestConfig): Promise<AxiosResponse<T>>;
  export function post<T = any>(url: string, data?: any, config?: AxiosRequestConfig): Promise<AxiosResponse<T>>;
  // ... 其他请求方法的类型声明 ...
}
```

```ts
import axios, { AxiosResponse, AxiosRequestConfig } from 'axios';

const config: AxiosRequestConfig = {
  url: 'https://api.example.com',
  method: 'GET',
};

axios.get(config)
  .then((response: AxiosResponse) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });

```