---
title: Playwright 测试框架
description: 
published: true
date: 2023-03-15T03:57:37.813Z
tags: 
editor: markdown
dateCreated: 2023-03-14T13:26:08.015Z
---

## Playwright 

> 田豆芽Playwright培训大纲
> v0.2: 当前的关注点是所有能讲的内容。 不涉及产品包装及定价

第一章 导论
1. 介绍
2. 什么是 Playwright?
3. 项目设置

第2节 Playwright 基础
1. 小试牛刀
2. 命令行参数(CLI)
3. 点击画面
4. 选择器(Selectors)
5. 使用输入
6. 断言
7. 注释
8. 标记
9. Playwright 配置
10. 报告
11. 屏幕截图
12. 前后Hooks
13. 自定义函数
14. 节点脚本
15. Playwright检查员
16. 失败时的人为因素
17. 并行测试执行

第三节 端到端测试

1. 章节介绍
2. 创建端到端测试配置
3. 端到端测试 - 登录 / 登出流程
4. 修复SSL证书错误
5. 端到端测试 - 反馈表单
6. 端到端测试 - 搜索
7. 端到端测试 - 转账
8. 端到端测试 - 过滤交易
9. 端到端测试 - 付款
10. 端到端测试 - 货币兑换 [挑战时间]

第4节：页面对象模式

1. 什么是页面对象模式？
2. 为登录创建页面模型类
3. 将页面模型应用于登录测试
4. 为首页创建页面模型类
5. 将页面模型应用于搜索测试
6. 反馈表单测试重构
7. 登录功能重构
8. 组件
9. 将页面模型应用于付款测试
10. 高级：抽象页面
11. 项目代码清理

第5节：高级：视觉测试
1. 创建视觉测试配置
2. 全页面快照
3. 单个元素快照
4. 带快照的页面对象模型
5. 更新快照
6. EXTRA：Node脚本
7. EXTRA：Percy.io指南

第6节：高级：REST API 测试
1. 章节介绍
2. API 测试配置
3. 简单的API 测试
4. 解析响应JSON数据
5. GET 请求测试
6. POST 请求测试
7. PUT 请求测试
8. DELETE 请求测试

第7节：高级：CI/CD 集成
1. 下载 Jenkins 服务器
2. 运行 Jenkins 服务器
3. 创建 Jenkins 构建
4. 参数化 Jenkins 构建
5. Jenkins 服务器 Node 脚本

第8节：高级：技巧和技巧
1. 测试信息对象
2. 跳过浏览器注释
3. Fixme 注释
4. 重试
5. 参数化测试
6. 模拟鼠标移动
7. 多个浏览器页面
8. 设备仿真
9. 生成 PDF 文件
10. 生成定制截图
11. 模拟浏览器语言和时区
12. 数据助手-获取随机数
13. 数据助手-随机字符串

第9节：专业定制报告
1. 创建自定义报告

第10节：使用Cucumber和Playwright进行BDD
1. Create Cucumber+Playwright项目
2. 项目结构概述
3. 全局断言
4. 全局钩子
5. 特性
6. 步骤定义
7. Cucumber的Node脚本
8. 页面对象模型
9. Cucumber HTML报告生成器
10. 场景大纲

第11节:BDD with CodeceptJS and Playwright的内容概述
1. 创建BDD项目
2. CodeceptJS设置
3. 创建并运行第一个测试
4. 断言
5. 多个场景
6. 处理Web元素
7. Before & After钩子
8. 配置
9. 页面对象模型
10. Node脚本

第12节：使用Playwright进行Web爬虫
1. Web爬虫项目设置
2. 爬虫脚本
3. 用于爬虫的浏览器设置
4. 设置用户代理
5. 从网站获取数据
6. 将数据存储到文件中

第13节：Percy 集成
#待渐进明细

第14节: 第三方测试运行器
111.Playwright与Mocha
112.Playwright与Jest
113.Playwright与Ava

第15节: HTML和JavaScript基础知识
114.HTML是什么？
115.标题和段落
116.链接
117.图像
118.格式化元素
119.注释
120.表格
121.列表
122.表单
123.Class、ID、Data-test属性
124.按钮
125.符号
126.动态内容
127.头部和元标签
128.Javascript技术栈概述
129.Var、Let和Const
130.Console log、info、warn、error
131.函数和箭头函数
132.数组
133.日期和时间
134.类
135.检查网站
136.描述、it、test和expect
137.异步/等待
138.帮助