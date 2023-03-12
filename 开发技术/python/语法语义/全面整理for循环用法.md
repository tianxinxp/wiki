---
title: 【Python】全面整理for循环用法（range, enumerate, zip等）
description: 没看懂这篇文章，千万别说自己会for循环~
published: true
date: 2023-03-12T16:03:19.340Z
tags: python, for
editor: markdown
dateCreated: 2023-03-12T16:03:19.340Z
---

> 摘要： 编程之路要想走的远，除了天赋， 基本功也是很重要的。 在本文中， 田辛老师非常详细了列举了Python中for循环的主要用法。说实话，直到写完这篇文章， 都没想到能写2000多字。 就算做个总结吧。  

## 1 `for`基本语法

### 1.1 基本用法

与 `C` 系编程语言不同，`Python` 的 `for` 语句是在不使用计数器变量的情况下编写的。 `[变量名]` 是任意名称。

```python
for 变量名 in 可枚举对象:
	处理	
```

田辛老师第一次看到这个语法的时候，心里想的是：这不就是`foreach`嘛！实际上， 不是所有的循环都需要类似`C语言`那样的循环变量的。 而且Python实现`C`的效果本身也很容易。 

`for` 循环会将列表等可迭代对象的元素按顺序赋值给变量进行处理。 对所有元素重复该过程。 

请看如下示例：
```python
names = ['张三', '李四', '田辛']

for name in names:
    print(name)
    
>>> 输出 >>>
张三
李四
田辛

进程已结束,退出代码0
```

### 1.2 终止语句:`break`

如果要在`for`循环中结束循环， 需要使用`break`语句。

示例：
```python
names = ['张三', '李四', '田辛']

for name in names:
    if name == '李四':
        print('!!BREAK!!')
        break
    print(name)
    
>>> 输出 >>>
张三
!!BREAK!!

进程已结束,退出代码0
```

通常，程序会用`if`条件语句使程序执行`break`。

### 1.3 跳过特定的处理:`continue`

如果要跳过对特定元素的处理，可以使用`continue`。

对比一下：

-   `break` 直接停掉了整个`for` 循环，整个`for`处理戛然而止。 
-   `continue` 只是跳过了对该元素的 `continue` 语句之后的处理。 `for` 循环继续并处理下一个元素。

```python
names = ['张三', '李四', '田辛']

for name in names:
    if name == '李四':
        print('!!SKIP!!')
        continue
    print(name)

>>> 输出 >>>
张三
!!SKIP!!
田辛

进程已结束,退出代码0
```

### 1.4 for循环正常完成后的处理：`else`

如果你想在for语句的循环执行到结束后做一些处理，使用 `else` 。

```python
names = ['张三', '李四', '田辛']

for name in names:
    print(name)
else:
    print('!!FINISH!!')

>>> 输出 >>>
张三
李四
田辛
!!FINISH!!

进程已结束,退出代码0
```

如果 `break` 中途终止，则不会执行 `else` 处理。

```python
names = ['张三', '李四', '田辛']

for name in names:
    if name == '李四':
        print('!!BREAK!!')
        break
    print(name)
else:
    print('!!FINISH!!')

>>> 输出 >>>    
张三
!!BREAK!!

进程已结束,退出代码0
```
但是 `continue` 并不影响`else` 的执行。 这也是田辛老师刚才一直强调`break`是将整个`for`逻辑处理完全中断的原因。 

```python
for name in l:
    if name == 'Bob':
        print('!!SKIP!!')
        continue
    print(name)
else:
    print('!!FINISH!!')

>>> 输出 >>>  
张三
!!SKIP!!
田辛
!!FINISH!!

进程已结束,退出代码0
```



## 2 `for`语句中使用很方便的函数/处理



### 2.1 只提取一些元素：切片

如果只想提取某些元素，请使用 `[start:stop]` 之类的切片指定范围。为 `start` 和 `stop` 指定 0 的起始索引。请注意，不包括 `stop` 元素。

```python
letters = ['A', 'B', 'C', 'D', 'E', 'F', 'G']

for c in letters[2:5]:
    print(c)

>>> 输出 >>>
C
D
E

进程已结束,退出代码0
```

实际上，从列表中直接提取元素的语法是 `[start:stop:step]` 。 刚才田辛老师省略了`step`，其实同样的，`start`和`stop`也是可以省略的。 比如仅提取奇数和偶数元素的示例如下。

```python
letters = ['A', 'B', 'C', 'D', 'E', 'F', 'G']

for c in letters[::2]:
    print(c)
    
>>> 输出 >>>
A
C
E
G

进程已结束,退出代码0
```
当然，也可以只省略一个参数。
```python
letters = ['A', 'B', 'C', 'D', 'E', 'F', 'G']

for c in letters[1::2]:
    print(c)

>>> 输出 >>>
B
D
F

进程已结束,退出代码0
```



### 2.2 索引（计数器）：`range()` 函数

这个用法就是我们在开头说的， 类似于`C`语言， 在`for`循环中使用计数器。

```python 
for i in range(3):
    print(i)

>>> 输出 >>>
0
1
2

进程已结束,退出代码0
```

在Python3中， `range()` 创建了一个 range 类型的对象，即使 print() 输出了也不会显示内容。这里为了便于说明，将其转换为带有 list() 的列表并输出，但如上例中在for语句中使用时无需转换为列表。

`range(stop) `返回 [0 , stop) 的序列号。

```python
print(list(range(3)))

>>> 输出 >>>
[0, 1, 2]

进程已结束,退出代码0
```
实际上， `range()`的语法和刚才直接从列表中提取元素的语法是一致的。 也可以有三个参数：`range(start, stop, step) `。区别仅仅在于`stop`参数是默认参数罢了。



### 2.3 列表元素和索引：`enumerate()` 函数

如果想同时获取列表（数组）和索引（计数器）等可迭代对象的元素，使用 `enumerate()` 函数。

```python
names = ['张三', '李四', '田辛']

for i, name in enumerate(names):
    print(i, name)

>>> 输出 >>>
0 张三
1 李四
2 田辛    

进程已结束,退出代码0
```

`enumerate()` 函数没有指定增量 step 的参数，但可以按如下方式实现。

```python
names = ['张三', '李四', '田辛']
step = 2
for i, name in enumerate(names):
    print(i * 2, name)

>>> 输出 >>>
0 张三
2 李四
4 田辛

进程已结束,退出代码0
```



### 2.4 多个列表元素（多个变量）：zip() 函数

如果想获取多个可迭代对象（列表等）的元素作为多个变量，使用 zip() 函数。

```python
names = ['张三', '李四', '田辛']
ages = [34, 22, 48]
for name, age in zip(names, ages):
    print(name, age)

>>> 输出 >>>
张三 34
李四 22
田辛 48

进程已结束,退出代码0
```
不限于两个变量，也可以对三个或更多的可迭代对象进行分组。

```python
names = ['张三', '李四', '田辛']
ages = [34, 22, 48]
locations = ['北京', '上海', '广州']

for name, age, location in zip(names, ages, locations):
    print(name, age, location)

>>> 输出 >>>
张三 34 北京
李四 22 上海
田辛 48 广州

进程已结束,退出代码0
```



### 2.5 多个列表元素和索引：enumerate()、zip() 函数

如果想同时获取多个可迭代对象（列表等）的元素和索引（计数器），可以结合使用 enumerate() 和 zip() 函数。

<font color='red'>PS:`zip()` 函数的变量名必须括在括号 () 中。</font>

```python
names = ['张三', '李四', '田辛']
ages = [34, 22, 48]
locations = ['北京', '上海', '广州']

for i, (name, age, location) in enumerate(zip(names, ages, locations)):
    print(i, name, age, location)

>>> 输出 >>>
0 张三 34 北京
1 李四 22 上海
2 田辛 48 广州

进程已结束,退出代码0
```



### 2.6 倒序（取自后面）：reversed() 函数

#### 2.6.1 列表倒序

如果要以相反的顺序获取可迭代对象（例如列表）的元素，请使用 reversed() 函数。 这里面， 我们发现序号那里很奇怪，实际上在取补。 但是，田辛老师发现， 虽然`enumerate`并没有那么多参数可以产生倒序的逻辑。 但是可以`list()`

```python
names = ['张三', '李四', '田辛']

for i, name in enumerate(reversed(names)):
    print((len(names) - 1) - i, name)

>>> 输出 >>>
2 田辛
1 李四
0 张三

进程已结束,退出代码0
```

让我们来试试`list()`

```python
names = ['张三', '李四', '田辛']

for i, name in reversed(list(enumerate(names))):
    print(i, name)

>>> 输出 >>>
2 田辛
1 李四
0 张三

进程已结束,退出代码0
```

输出结果和刚刚的代码一模一样， 只不过注意`reversed()`函数的位置。 

同样的，`zip()`也不能反转， 也是通过`list()`反转的。 

```python
names = ['张三', '李四', '田辛']
ages = [34, 22, 48]
locations = ['北京', '上海', '广州']

for name, age, location in reversed(list(zip(names, ages, locations))):
    print(name, age, location)
print('====')
for name, age, location in reversed(zip(names, ages, locations)):
    print(name, age, location)

>>> 输出 >>>
田辛 48 广州
李四 22 上海
张三 34 北京
====


进程已结束,退出代码0
```

我们可以看到两个`for`循环， 只执行了第一个，第二个没有输出。 

#### 2.6.2 range倒序

range 对象也可以反转，就如下面的代码。 您也可以在不使用 reversed() 的情况下为 step 指定一个负值。

```python
for i in reversed(range(3)):
    print(i)

for i in range(2, -1, -1):
    print(i)

>>> 输出 >>>
2
1
0
2
1
0   

进程已结束,退出代码0
```

连续输出了两遍2-1-0，说明实际上两个循环的执行效果是等价的。



### 2.7 多个循环： itertools.product() 函数

Python中的多个循环可以这样写：块在 Python 中由缩进表示，因此只需添加更多缩进即可。下面例子是9×9乘法表的循环输出。 这里为了简单，把最大值改为了2。 然后生成2*2的乘法表。

```python
max = 2
for i in range(1, max + 1):
    for j in range(1, max + 1):
        print(f"{i} * {j} = {i * j}")
        
>>> 输出 >>>
1 * 1 = 1
1 * 2 = 2
2 * 1 = 2
2 * 2 = 4

进程已结束,退出代码0
```

以上这种写法固然对。但是要知道，Python语言的特性是优雅~ 在这里田辛老师提供一个更加简洁的写法：使用标准库 `itertools` 模块中的 `itertools.product()` 与不嵌套 for 的多个循环得到相同的结果。

```python
import itertools

max = 2
for i, j in itertools.product(range(1, max + 1), range(1, max + 1)):
    print(f"{i} * {j} = {i * j}")

>>> 输出 >>>
1 * 1 = 1
1 * 2 = 2
2 * 1 = 2
2 * 2 = 4

进程已结束,退出代码0
```

<font color='red'>使用 `break` 一次退出多个循环的内层循环时，使用 `itertools.product()` 很方便。</font>

## 3 其他内容

### 3.1 字典 (dict) for 循环

可以通过在 `for` 循环中传递字典 `dict` 对象来获取字典的键。

```python
d = {'姓名': '田辛', '年龄': 48, 'Base地': '北京'}

for k in d:
    print(k)

>>> 输出 >>>
姓名
年龄
Base地

进程已结束,退出代码0
```

如果要获取值或键值对，请使用 values() 和 items() 方法。

```python
d = {'姓名': '田辛', '年龄': 48, 'Base地': '北京'}

for v in d.values():
    print(v)
    
>>> 输出 >>>
田辛
48
北京

进程已结束,退出代码0
```

```python
d = {'姓名': '田辛', '年龄': 48, 'Base地': '北京'}

for k, v in d.items():
    print(k, v)
    
>>> 输出 >>>
姓名 田辛
年龄 48
Base地 北京

进程已结束,退出代码0
```

### 3.2 列表理解

在处理列表等可迭代对象的元素生成新列表时，可以使用列表推导式而不是for语句来描述更简单。

列表理解是这样写的：

`[表达式 for 变量 in 列表] `

 我们首先写一个不用列表推导式的代码：

```python
squares = []
for i in range(5):
    squares.append(i ** 2)

print(squares)

>>> 输出 >>>
[0, 1, 4, 9, 16]

进程已结束,退出代码0
```

以上代码生成一个0-4的平方的列表， 现在是3行有效代码形成列表， 1行`print()`输出。如果用推导式的方式的话，一行代码足以： 

 ```python
squares = [i**2 for i in range(5)]
print(squares)

>>> 输出 >>>
[0, 1, 4, 9, 16]

进程已结束,退出代码0
 ```

通过使用列表推导，不仅可以处理元素，还可以根据条件提取元素，值得记住。

## 4 全部代码

田辛老师写这篇博客的全部代码：
```python
#!/usr/bin/env python  
# -*- coding:utf-8 -*-  
"""  
#-----------------------------------------------------------------------------  
#                     --- TDOUYA STUDIOS ---  
#-----------------------------------------------------------------------------  
#  
# @Project : di08-tdd-cdg-python-learning  
# @File    : for_test.py  
# @Author  : tianxin.xp@gmail.com  
# @Date    : 2023/3/8 10:05  
#  
#   全面整理for循环用法
#  
#--------------------------------------------------------------------------"""  
  
print('=== Case 1 ===')  
  
names = ['张三', '李四', '田辛']  
  
for name in names:  
    print(name)  
  
print('=== Case 2 ===')  
  
names = ['张三', '李四', '田辛']  
  
for name in names:  
    if name == '李四':  
        print('!!BREAK!!')  
        break  
    print(name)  
  
print('=== Case 3 ===')  
  
names = ['张三', '李四', '田辛']  
  
for name in names:  
    if name == '李四':  
        print('!!SKIP!!')  
        continue  
    print(name)  
  
print('=== Case 4 ===')  
  
names = ['张三', '李四', '田辛']  
  
for name in names:  
    print(name)  
else:  
    print('!!FINISH!!')  
  
print('=== Case 5 ===')  
  
names = ['张三', '李四', '田辛']  
  
for name in names:  
    if name == '李四':  
        print('!!BREAK!!')  
        break  
    print(name)  
else:  
    print('!!FINISH!!')  
  
print('=== Case 6 ===')  
  
names = ['张三', '李四', '田辛']  
  
for name in names:  
    if name == '李四':  
        print('!!SKIP!!')  
        continue  
    print(name)  
else:  
    print('!!FINISH!!')  
  
print('=== Case 7 ===\n>>> 输出 >>>')  
letters = ['A', 'B', 'C', 'D', 'E', 'F', 'G']  
  
for c in letters[2:5]:  
    print(c)  
  
print('=== Case 8 ===\n>>> 输出 >>>')  
letters = ['A', 'B', 'C', 'D', 'E', 'F', 'G']  
  
for c in letters[::2]:  
    print(c)  
  
print('=== Case 9 ===\n>>> 输出 >>>')  
letters = ['A', 'B', 'C', 'D', 'E', 'F', 'G']  
  
for c in letters[1::2]:  
    print(c)  
  
print('=== Case 9 ===\n>>> 输出 >>>')  
for i in range(3):  
    print(i)  
  
print('=== Case 10 ===\n>>> 输出 >>>')  
print(list(range(3)))  
  
print('=== Case 11 ===\n\n>>> 输出 >>>')  
  
names = ['张三', '李四', '田辛']  
  
for i, name in enumerate(names):  
    print(i, name)  
  
print('=== Case 12 ===\n\n>>> 输出 >>>')  
  
names = ['张三', '李四', '田辛']  
step = 2  
for i, name in enumerate(names):  
    print(i * 2, name)  
  
print('=== Case 13 ===\n\n>>> 输出 >>>')  
  
names = ['张三', '李四', '田辛']  
ages = [34, 22, 48]  
for name, age in zip(names, ages):  
    print(name, age)  
  
print('=== Case 13 ===\n\n>>> 输出 >>>')  
  
names = ['张三', '李四', '田辛']  
ages = [34, 22, 48]  
locations = ['北京', '上海', '广州']  
  
for name, age, location in zip(names, ages, locations):  
    print(name, age, location)  
  
print('=== Case 14 ===\n\n>>> 输出 >>>')  
  
names = ['张三', '李四', '田辛']  
ages = [34, 22, 48]  
locations = ['北京', '上海', '广州']  
  
for i, (name, age, location) in enumerate(zip(names, ages, locations)):  
    print(i, name, age, location)  
  
names = ['张三', '李四', '田辛']  
  
print('=== Case 15 ===\n\n>>> 输出 >>>')  
names = ['张三', '李四', '田辛']  
  
for i, name in reversed(list(enumerate(names))):  
    print(i, name)  
  
print('=== Case 16 ===\n\n>>> 输出 >>>')  
for i in reversed(range(3)):  
    print(i)  
  
for i in range(2, -1, -1):  
    print(i)  
  
print('=== Case 17 ===\n\n>>> 输出 >>>')  
names = ['张三', '李四', '田辛']  
ages = [34, 22, 48]  
locations = ['北京', '上海', '广州']  
  
for name, age, location in reversed(list(zip(names, ages, locations))):  
    print(name, age, location)  
print('====')  
# for name, age, location in reversed(zip(names, ages, locations)):  
#     print(name, age, location)  
  
print('=== Case 17 ===\n\n>>> 输出 >>>')  
  
for i in range(1, 10):  
    for j in range(1, 10):  
        print(f"{i} * {j} = {i * j}")  
  
print('=== Case 17 for document===\n\n>>> 输出 >>>')  
  
max = 2  
for i in range(1, max + 1):  
    for j in range(1, max + 1):  
        print(f"{i} * {j} = {i * j}")  
  
print('=== Case 17 for document===\n\n>>> 输出 >>>')  
  
import itertools  
  
for i, j in itertools.product(range(1, max + 1), range(1, max + 1)):  
    print(f"{i} * {j} = {i * j}")  
  
print('=== Case 18 for document===\n\n>>> 输出 >>>')  
  
d = {'姓名': '田辛', '年龄': 48, 'Base地': '北京'}  
  
for k in d:  
    print(k)  
  
print('=== Case 19 for document===\n\n>>> 输出 >>>')  
  
d = {'姓名': '田辛', '年龄': 48, 'Base地': '北京'}  
  
for v in d.values():  
    print(v)  
  
print('=== Case 20 for document===\n\n>>> 输出 >>>')  
  
d = {'姓名': '田辛', '年龄': 48, 'Base地': '北京'}  
  
for k, v in d.items():  
    print(k, v)  
  
print('=== Case 21 for document===\n\n>>> 输出 >>>')  
  
squares = [i ** 2 for i in range(5)]  
print(squares)  
  
print('=== Case 22 for document===\n\n>>> 输出 >>>')  
  
squares = []  
for i in range(5):  
    squares.append(i ** 2)  
  
print(squares)
```








