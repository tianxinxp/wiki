---
title: Node.js中的path模块详解
description: 
published: true
date: 2023-03-20T07:17:45.256Z
tags: 
editor: markdown
dateCreated: 2023-03-20T07:17:45.256Z
---


#专题/Nodejs 

> 摘要 : Node.js中的path模块提供了一些方法来处理文件路径，包括路径的拼接、解析、规范化等。本文将介绍path模块中的各个方法，并给出实例。同时，我们还将结合`__dirname`，提供一个综合例子。
> 
> 关键字：Node.js、path模块、路径处理、`__dirname`、`path.join()`、`path.resolve()`、`path.normalize()`、`path.dirname()`、`path.basename()`、`path.extname()`。

Node.js和Python技术类似， 都致力于能够实现跨平台的通用代码。 为此，针对路径的拼接， Node.js提供了path模块。 该模块提供了一些方法来处理文件路径，包括路径的拼接、解析、规范化等。在本文中，田辛老师将介绍path模块中的各个常用方法，并给出实例。同时，我们还将结合`__dirname`，提供一个综合例子。

## 1 path模块
### 1.1 path.join()

`path.join()`方法将多个路径拼接成一个完整的路径。它会自动处理路径分隔符，确保生成的路径在不同操作系统上都能正常使用。

```javascript
const path = require('path'); 

const dir = '/path/to/dir'; 
const filename = 'file.txt'; 

const filePath = path.join(dir, filename); 
console.log(filePath); 

// 输出Linux：/path/to/dir/file.txt
// 输出Windows：\path\to\dir\file.txt
```

### 1.2 path.resolve()

`path.resolve()`方法将路径解析为绝对路径。它会将相对路径转换为绝对路径，并且可以处理多个参数。

```javascript
const path = require('path'); 
const dir = '/path/to/dir'; 
const filename = 'file.txt'; 
const filePath = path.resolve(dir, filename); 
console.log(filePath); 
// 输出Linux：/path/to/dir/file.txt
// 输出Windows：E:\path\to\dir\file.txt
```

<font color=red>注意： `path.join()`方法和`path.resolve()`方法都是基于路径的拼装，不保证文件的存在</font>

### 1.3 path.normalize()

`path.normalize()`方法规范化路径，去除多余的斜杠和点。它会将路径中的斜杠转换为当前操作系统的标准斜杠，并且会处理多个点和斜杠。

```javascript
const path = require('path');

const dir = '/path/to/dir//';
const filename = './file.txt';

const filePath = path.normalize(dir + filename);
console.log(filePath); 
// 输出：/path/to/dir/file.txt
```

### 1.4 path.dirname()

`path.dirname()`方法获取路径中的目录部分。它会返回路径中最后一个斜杠之前的部分。

```javascript
const path = require('path'); 
const filePath = '/path/to/dir/file.txt'; 
const dir = path.dirname(filePath); 
console.log(dir); 
// 输出：/path/to/dir
```

### 1.5 path.basename()

`path.basename()`方法获取路径中的文件名部分。它会返回路径中最后一个斜杠之后的部分。

```javascript
const path = require('path'); 
const filePath = '/path/to/dir/file.txt'; 
const filename = path.basename(filePath); 
console.log(filename); // 输出：file.txt
```

### 1.6 path.extname()

`path.extname()`方法获取路径中的文件扩展名部分。它会返回路径中最后一个点之后的部分。

```javascript
const path = require('path'); 
const filePath = '/path/to/dir/file.txt'; 
const extname = path.extname(filePath); 
console.log(extname); // 输出：.txt
```

## 2 `__dirname`变量

### 2.1 变量说明

`__dirname`变量是Node.js的一个全局变量， 它表示当前模块所在的目录的绝对路径。

```javascript
console.log(__dirname); // 输出：E:\develop\node.js
```

### 2.2 `__dirname` 和 path.join 联合使用

```javascript
const path = require('path');

const dir = path.join(__dirname, 'files');
const filename = 'file.txt';

const filePath = path.join(dir, filename);
console.log(filePath); // 输出：E:\develop\node.js\files\file.txt
```

在上面的例子中，田辛老师使用path.join()方法将__dirname和'files'拼接成一个目录路径，然后再将文件名拼接到目录路径中，得到完整的文件路径。这样，我们就可以方便地处理文件路径了。