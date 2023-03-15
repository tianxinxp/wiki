---
title: 探究Windows命令行工具：CMD vs PowerShel
description: 
published: true
date: 2023-03-15T14:23:01.703Z
tags: 
editor: markdown
dateCreated: 2023-03-15T14:23:01.703Z
---


>摘要：本文介绍了Windows操作系统中的两个命令行工具——CMD和PowerShell的区别。CMD是传统的命令行工具，适合程序员和专业用户使用，而PowerShell更加强大、灵活，支持更多的命令和功能。本文从语法、支持代码块和对象管道三个方面详细介绍了PowerShell的优势，希望能够帮助读者更好地了解Windows命令行工具的使用。

>标签：CMD、PowerShell、命令行工具、语法、代码块、对象管道、自动化脚本编写。

>以下正文：

今天，田辛老师给大家聊一聊Windows操作系统中的两个命令行工具——CMD和PowerShell的区别。

田辛老师最开始学习计算机， 大概是1988年，当时还是DOS2.0的系统。从1988用到现在， 可以说对命令行窗口还是很熟悉，也很有感情的。 

首先，我们可以说， CMD是Windows操作系统中**传统的**的命令行工具。对于程序员来说， 或者是一些专业的用户。 CMD能够解决绝大多数问题。而PowerShell——作为微软公司推出的新一代命令行工具。相比于CMD，PowerShell更加强大、灵活，支持更多的命令和功能。
    

## 1 语法不同

CMD的语法比较简单，命令和参数之间用空格隔开。而PowerShell的语法更加灵活，支持使用管道符、变量、循环等高级语法。
    
例如，我们想要在CMD中查找某个文件夹下的所有文件，可以使用`dir`命令：

`dir C:\Users\田辛老师\Desktop\`
    
这个命令很简单， 咱们就不显示输出结果了。 而在PowerShell中，我们可以使用Get-ChildItem命令，并通过管道符和Where-Object命令筛选出我们需要的文件。我们看一下这个命令：

`Get-ChildItem C:\Users\田辛老师\Desktop\ | Where-Object {$_.Extension -eq ".txt"}`

你会发现，这个命令就是检索`C:\Users\田辛老师\Desktop\`文件夹里面的所有txt文件。似乎也没比`dir`命令厉害多少。 

那么，田辛老师再举一个例子：直接输出json。这大概会让你感觉到Powershell的功能的灵活之处。

```powershell
PS D:\software\cmder
λ Get-ChildItem -Path "E:\sample\python\FX_ProjectManager\images" -Recurse -File | Select-Object Name, FullName, Length, CreationTime, LastWriteTime | ConvertTo-Json | Out-File "d:\filelist.json"

PS D:\software\cmder
λ
```

输出的JSON文件内容：

```json
[
    {
        "Name":  "main_window.jpeg",
        "FullName":  "E:\\sample\\python\\FX_ProjectManager\\images\\main_window.jpeg",
        "Length":  25238,
        "CreationTime":  "\/Date(1677227829985)\/",
        "LastWriteTime":  "\/Date(1677227829985)\/"
    },
    {
        "Name":  "new_project.jpeg",
        "FullName":  "E:\\sample\\python\\FX_ProjectManager\\images\\new_project.jpeg",
        "Length":  10107,
        "CreationTime":  "\/Date(1677227829985)\/",
        "LastWriteTime":  "\/Date(1677227829985)\/"
    }
]
```

这里，田辛老师简单总结一下对比`dir`命令，`Get-ChildItem` 命令的优势：

- 更加灵活的筛选功能：Get-ChildItem命令支持使用通配符、正则表达式等方式进行文件筛选，可以更加灵活地查找指定类型的文件。
- 支持对象管道：Get-ChildItem命令的输出可以作为其他命令的输入，从而实现更加灵活的操作。
- 支持多种输出格式：Get-ChildItem命令支持多种输出格式，包括列表、表格、XML、JSON等，可以根据需要选择不同的输出格式。
- 支持递归查找：Get-ChildItem命令支持递归查找子目录中的文件，可以一次性查找整个目录树。
- 支持显示文件属性：Get-ChildItem命令可以显示文件的属性，包括文件大小、创建时间、修改时间等，可以帮助用户更好地了解文件的信息。

总的来说，Get-ChildItem命令比dir命令更加强大、灵活，适合进行复杂的文件查找和操作。


二、支持代码块
    
PowerShell支持代码块，这意味着我们可以将多个命令组合在一起，形成一个代码块，然后一次性执行。这样可以提高效率，减少输入命令的次数。
    
例如，我们想要在CMD中创建一个文件夹，并在其中创建一个文本文件，可以使用以下命令：
    

```shell
mkdir C:\Users\田辛\Desktop\test
cd C:\Users\田辛\Desktop\test
echo "Hello World" > test.txt`
```

而在PowerShell中，我们可以使用代码块的方式，将这三个命令组合在一起：
    

```powershell
{ New-Item -ItemType Directory -Path D:\田辛老师\ Set-Location D:\田辛老师\ Add-Content -Path test.txt -Value "Hello World" }
```

当然，代码块操作也会非常灵活：

```shell
# 创建新的脚本块 # 创建新的脚本块
$block = {
  $write = Get-Process |Select-Object -First 1 
  "$($write.Name) 占用内存: $($write.WorkingSet/1mb) MB"
}

$block.GetType().Name

& $block
   
# 使用NewScriptBlock方法创建脚本块:
$blockStr = '$write=Get-Process |Select-Object -First 1 
  "$($write.Name) 占用内存: $($write.WorkingSet/1mb) MB"'
$block = $executioncontext.InvokeCommand.NewScriptBlock($blockStr)
$block.GetType().Name
& $block
```

执行结果为： 

```shell
PS D:\software\cmder
λ d:\1.ps1
ScriptBlock
AggregatorHost 占用内存: 6.90625 MB
ScriptBlock
AggregatorHost 占用内存: 6.90625 MB
```

三、支持对象管道
    
PowerShell支持对象管道，这意味着我们可以将一个命令的输出作为另一个命令的输入，从而实现更加灵活的操作。
    
例如，我们想要在CMD中查找某个文件夹下的所有txt文件，并将它们复制到另一个文件夹中，可以使用以下命令：
`xcopy C:\Users\田辛\Desktop\test*.txt C:\Users\田辛\Desktop\backup\
    
而在PowerShell中，我们可以使用对象管道的方式，将Get-ChildItem命令的输出作为Copy-Item命令的输入：
`Get-ChildItem C:\Users\田辛\Desktop\test*.txt | Copy-Item -Destination C:\Users\田辛\Desktop\backup\
    
以上就是CMD和PowerShell的一些区别。总的来说，PowerShell更加强大、灵活，适合进行复杂的操作和自动化脚本编写。希望这篇文章能够帮助大家更好地了解Windows命令行工具的使用。