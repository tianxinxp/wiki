---
title: 项目管理中蒙特卡洛模拟的Python实现（进度管理的例子）
description: 
published: true
date: 2023-03-12T15:37:18.151Z
tags: python, pmp, 项目管理
editor: markdown
dateCreated: 2023-03-12T15:28:06.445Z
---

#专题/Python
#专题/项目管理

> 蒙特卡洛模拟是一种基于概率统计的方法，通过随机模拟来计算出某个事件发生的概率。在项目管理中，蒙特卡洛模拟主要用于计算项目工期、成本等关键指标的概率分布，帮助项目经理更好地进行风险管理和决策。今天呢，田辛老师带领大家，用Python中的numpy和matplotlib库来进行计算和绘图，帮你你轻松掌握蒙特卡洛模拟的计算方法。


周末上了， 从早到晚讲了一天~ 一不小心搞得田辛老师都断更了。 

今天呢，田辛老师来给大家继续讲一个著名的项目管理工具：蒙特卡洛模拟。 当然，田辛老师既然发到CSDN上面，无论如何要给出关于蒙特卡洛模拟的Python实现啦。 下面就是我们今天的代码执行结果。 

![蒙特卡洛模拟.png](/项目管理/蒙特卡洛模拟.png)

## 什么是蒙特卡洛模拟？

蒙特卡洛模拟是一种基于概率统计的方法，通过随机模拟来计算出某个事件发生的概率。在项目管理中，蒙特卡洛模拟主要用于计算项目工期、成本等关键指标的概率分布，帮助项目经理更好地进行风险管理和决策。

让我们来看上面这张图， 这张图是针对三个项目活动:活动1、活动2、活动3进行的蒙特卡洛模拟。 模拟的依据是这三个活动的三点估算结果。 然后让计算机进行了1,000,000次随机预算， 得出的上面这张图。 

我们拿上边这张图的蓝色虚线的交叉举例，这个点指的是什么呢？ 我们看Y轴，这里的90%指的是完工概率90%。 这个点对应的横轴将近19天的样子。也就是说，通过计算机100万次的模拟。在19天以下完成项目的概率是90%。 

做过项目的同学都知道， 客户或者领导总是希望我们快些快些再快些。 领导说，19天没有，只有16天。 这时候，作为项目经理通过上面的图，发现，X轴16天对应Y轴的值大概在30%左右。 你就问领导：成功率只有30%哟， 你赌还是不赌~ 

这不失为一种不错的“科学算命”的方式。 关键是简单，还有概率论给你撑腰。 

## Python实现

在Python中如何计算项目管理的蒙特卡洛模拟呢？其实很简单，我们可以使用Python中的numpy和matplotlib库来进行计算和绘图。下面田老师给出完整的代码：

```python
#!/usr/bin/env python
# -*- coding:utf-8 -*-
"""
#-----------------------------------------------------------------------------
#                     --- TDOUYA STUDIOS ---
#-----------------------------------------------------------------------------
#
# @Project : di08-tdd-cdg-python-learning
# @File    : monte_carlo.py
# @Author  : tianxin.xp@gmail.com
# @Date    : 2023/3/12 18:22
#
# 用Python实现蒙特卡洛模拟
#
#--------------------------------------------------------------------------"""
from datetime import datetime

import matplotlib.pyplot as plt
import numpy as np
from matplotlib.ticker import FuncFormatter, MultipleLocator
from scipy.stats import norm

plt.rcParams['font.sans-serif'] = ['SimHei']
plt.rcParams['axes.unicode_minus'] = False


def to_percent(y, position):
    # 将纵轴用百分数表示
    return '{:.0f}%'.format(100 * y)


class Activity:
    """ 活动类，用于表示一个项目中的活动

   Attributes:
       name (str): 活动名称
       optimistic (float): 乐观时间
       pessimistic (float): 悲观时间
       most_likely (float): 最可能时间
   """

    def __init__(self, name, optimistic, pessimistic, most_likely):
        """
            初始化活动类

            Args:
                name (str): 活动名称
                optimistic (float): 乐观时间
                pessimistic (float): 悲观时间
                most_likely (float): 最可能时间
        """
        self.name = name
        self.optimistic = optimistic
        self.pessimistic = pessimistic
        self.most_likely = most_likely


class PMP:
    """
    PMP类用于进行项目管理中的相关计算：
    方法：
    monte_carlo_simulation : 蒙特卡洛模拟试算，包括计算项目工期、平均值、标准差、绘制积累图和概率密度曲线等功能。
    """

    def __init__(self, activities):
        """
        初始化PMP类，传入活动列表。
        :param activities: 活动列表，包括活动名称、乐观值、最可能值和悲观值。
        """
        self.activities = activities

    def monte_carlo_simulation(self, n):
        """
        进行蒙特卡洛模拟试算，计算项目工期、平均值、标准差、绘制积累图和概率密度曲线等。
        :param n: 模拟次数。
        """
        # 模拟参数和变量
        t = []
        for activity in self.activities:
            t.append(np.random.triangular(activity.optimistic, activity.most_likely, activity.pessimistic, n))

        # 计算项目工期
        project_duration = sum(t)

        # 计算平均值和标准差
        mean_duration = np.mean(project_duration)
        std_duration = np.std(project_duration)

        # 绘制积累图
        fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(8, 10), gridspec_kw={'height_ratios': [3, 1]})

        ax1.hist(project_duration, bins=50, density=True, alpha=0.7, color='blue', cumulative=True)
        ax1.yaxis.set_major_locator(MultipleLocator(0.1))
        ax1.yaxis.set_major_formatter(FuncFormatter(to_percent))
        ax1.set_ylabel('完成概率')
        ax1.set_title('PMP蒙特卡洛模拟试算', fontsize=20)

        # 绘制概率密度曲线
        xmin, xmax = ax1.get_xlim()
        x = np.linspace(xmin, xmax, 100)
        p = norm.cdf(x, mean_duration, std_duration)
        ax1.plot(x, p, 'k', linewidth=2, drawstyle='steps-post')

        # 找到完成概率90%的点
        x_90 = norm.ppf(0.9, mean_duration, std_duration)

        # 绘制垂线
        ax1.axvline(x_90, linestyle='--', color='blue')
        ax1.axhline(0.9, linestyle='--', color='blue')

        # 隐藏右边和上方的坐标轴线
        ax1.spines['right'].set_visible(False)
        ax1.spines['top'].set_visible(False)

        # 添加表格
        col_labels = ['活动名称', '乐观值', '最可能值', '悲观值']

        cell_text = [[activity.name, activity.optimistic, activity.most_likely, activity.pessimistic] for activity in
                     self.activities]
        table = ax2.table(cellText=cell_text, colLabels=col_labels, loc='center')

        # 设置表格的字体大小和行高
        table.auto_set_font_size(False)
        table.set_fontsize(14)

        # # 设置表格的行高为1.5倍原来的高度
        for i in range(len(self.activities) + 1):
            table._cells[(i, 0)].set_height(0.2)
            table._cells[(i, 1)].set_height(0.2)
            table._cells[(i, 2)].set_height(0.2)
            table._cells[(i, 3)].set_height(0.2)

        ax2.axis('off')

        # 调整子图之间的间距和边距
        plt.subplots_adjust(hspace=0.3, bottom=0.05)

        # 保存图表
        now = datetime.now().strftime('%Y%m%d%H%M%S')
        plt.savefig('monte_carlo_simulation_{}.png'.format(now))

        # 显示图形
        plt.show()


if __name__ == '__main__':
    # 模拟参数和变量
    n = 1000000  # 模拟次数

    # 活动的工期分布
    activities = [
        Activity('活动1', 5, 10, 7),
        Activity('活动2', 3, 8, 5),
        Activity('活动3', 2, 6, 4)
    ]

    # 进行蒙特卡洛模拟
    pmp = PMP(activities)
    pmp.monte_carlo_simulation(n)
```


