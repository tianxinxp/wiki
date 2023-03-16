---
title: 如何在Node.js中进行文件操作：读取、写入、修改和删除文件
description: 
published: true
date: 2023-03-16T11:53:51.999Z
tags: public, javascript, back-end
editor: markdown
dateCreated: 2023-03-16T11:53:34.771Z
---


#专题/Nodejs

> 摘要：这篇文章介绍了如何在Node.js中进行文件操作，包括读取、写入、修改和删除文件。Node.js提供了fs模块，可以用于文件操作。在进行文件操作时，需要注意不同操作系统之间的差异，例如文件路径分隔符、文件权限和换行符等。为了确保程序能够正确地进行文件操作，建议使用系统库来操作文件系统。本文提供了一些常用的文件操作方法和注意事项，帮助读者更好地理解Node.js的文件操作。关键词：Node.js、文件操作、fs模块、注意事项。


Node.js是一个神奇的东西，它可以让JavaScript在服务器端运行，让我们的很多前端程序员也能在后端大展身手了！毕竟站在田辛老师的角度上来说，虽然我不喜欢“全栈”这个概念， 但是最近各个用人单位都喜欢这种所谓T型人才嘛。 

Node.js是一个基于Chrome V8引擎的JavaScript运行环境，田辛老师经常在服务器端使用Node.js运行JavaScript代码。Node.js提供了许多内置模块，其中包括文件系统模块，可以用于读取、写入、修改和删除文件。在本篇博客中，田辛老师将介绍Node.js的文件操作，并探讨在不同操作系统下进行文件操作的注意事项。
    
## 1 Node.js文件操作
    
Node.js提供了fs模块，可以用于读取、写入、修改和删除文件。以下是一些常用的文件操作方法：
    
### 1.1 读取文件
    
Node.js提供了fs.readFile()方法来读取文件。以下是一个简单的例子：
    
```javascript
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) throw err;
    console.log(data);
});
```
    
在上面的代码中，田辛老师使用了fs.readFile()方法来读取example.txt文件。第一个参数是文件名，第二个参数是编码格式，第三个参数是回调函数。回调函数有两个参数，第一个参数是错误对象，第二个参数是读取的文件内容。如果读取文件时发生错误，将抛出错误。
    
### 1.2 写入文件
    
Node.js也可以用于写入文件。以下是一个简单的例子：
    
```javascript
const fs = require('fs');

fs.writeFile('example.txt', 'Hello World!', (err) => {
  if (err) throw err;
  console.log('File has been saved!');
});
```
    
在上面的代码中，田辛老师使用了fs.writeFile()方法来写入example.txt文件。第一个参数是文件名，第二个参数是要写入的内容，第三个参数是回调函数。如果写入文件时发生错误，将抛出错误。
    
### 1.3 修改文件
    
Node.js也可以用于修改文件。以下是一个简单的例子：
    
```javascript
const fs = require('fs');

fs.appendFile('example.txt', 'This is a new line!', (err) => {
  if (err) throw err;
  console.log('File has been updated!');
});
```
    
在上面的代码中，田辛老师使用了fs.appendFile()方法来向example.txt文件追加一行新内容。第一个参数是文件名，第二个参数是要追加的内容，第三个参数是回调函数。如果修改文件时发生错误，将抛出错误。
    
### 1.4 删除文件
    
Node.js也可以用于删除文件。以下是一个简单的例子：
    
```javascript
const fs = require('fs');

fs.unlink('example.txt', (err) => {
  if (err) throw err;
  console.log('File has been deleted!');
});
```
    
在上面的代码中，田辛老师使用了fs.unlink()方法来删除example.txt文件。第一个参数是文件名，第二个参数是回调函数。如果删除文件时发生错误，将抛出错误。
    
## 2 注意事项
    
在进行文件操作时，需要注意以下几点：
    
1.  文件路径分隔符不同
    Linux操作系统使用正斜杠（/）作为文件路径分隔符，而Windows操作系统使用反斜杠（\）作为文件路径分隔符。因此，在进行文件操作时，需要使用path模块中的path.join()方法来生成跨平台的文件路径。
2.  文件权限不同
    Linux操作系统使用基于权限的文件访问控制，而Windows操作系统使用基于用户的文件访问控制。因此，在进行文件操作时，需要注意文件权限的设置。
3.  换行符不同
    Linux操作系统使用`\n`作为换行符，而Windows操作系统使用`\r` 作为换行符。因此，在进行文件操作时，需要注意文件中的换行符是否正确。<font color=red>注意换行符和回车符是有区别的哦</font>

Node.js 本身类似与Python这种语言一样， 旨在尽可能在不同操作系统下实现配适性。 所以这里田辛老师提示大家尽可能使用系统库来操作文件系统，包括拼装路径操作，常见的，例如使用`path.join()`方法来生成跨平台的文件路径，使用`os.EOL`来获取跨平台的换行符，使用`fs.constants`来设置跨平台的文件权限等。这样可以使程序在不同的操作系统上运行时都能够正确地进行文件操作。

## 3 总结

在Node.js中，文件操作是非常常见的操作之一。Node.js提供了fs模块，可以用于读取、写入、修改和删除文件。在进行文件操作时，需要注意不同操作系统之间的差异，以确保程序能够正确地进行文件操作。