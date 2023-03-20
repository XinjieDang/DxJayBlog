---
layout: '../../layouts/MarkdownPost.astro'
title: 'TypeScript声明文件'
pubDate: 2023-03-21
description: 'TypeScript的使用'
author: 'ts入门'
cover:
    url: 'https://cdn2.unrealengine.com/vr-week-2023-header-4-1920x1080-376e6c48383f.jpg?resize=1&w=1920'
    square: 'https://cdn2.unrealengine.com/vr-week-2023-header-4-1920x1080-376e6c48383f.jpg?resize=1&w=1920'
    alt: 'cover'
tags: ["TypeScript", "前端"]
theme: 'light'
featured: false
---

### TypeScript声明文件

声明文件作用：

**使用第三方库时**，需要引用它的声明文件，**才能获得对应的代码补全、接口提示等功能**

**声明的新语法**

* `declare var ` 声明**全局变量**
* `declare function ` 声明**全局方法**
* `declare class`  声明**全局类**
* `declare enum` 声明**全局枚举类型**
* `declare namespace `声明（**含有子属性的全局对象**）
* `interface` 和`type `声明**全局类型**
* `export`**导出变量**
* `export namespace`导出（含有子属性的）对象
* `export default` ES6默认导出
* `export as namespace`  UMD库声明全局变量
* `declare global`扩展全局变量
* `declare module`扩展模块
* `///<reference/>`三斜线指令

**实例**

假设想要用第三方库jquery，常见方式是通过`<script>`标签引入Jquery，然后可以使用全局变量$

```javascript
//通常取一个id是foo的元素
$('#foo');
//ts中会报错，编译器不知道$是什么东西
JQuery('#foo');//ERROR：cannot find name 'Jqery'
```

需要用到**declare var 来定义它的类型**，只是**定义了全局变量`jQuery`的类型**，仅仅**用于编译时的检查**

```javascript
declare var JQuery:(selector:string)=>any;
Jquery('#foo')
```

**声明文件的定义**

通常会把声明语句发到一个单独的文件（jQuery.d.ts）中，这就是声明文件

```javascript
declare var JQuery:(selector:string)=>any;
```

一般ts会解析项目中所有的`*.ts`文件，也包含`.d.ts`结尾的文件，若无法解析，请检查下`tsconfig.json`中的`files`、`include`、和`exclude`配置

**第三方声明文件**

推荐使用**@types**统一管理第三方库的声明文件

`@types` 的使用方式很简单，直接用 npm 安装对应的声明模块即可，以 jQuery 举例：

```bash
npm install @types/jquery --save-dev
```



