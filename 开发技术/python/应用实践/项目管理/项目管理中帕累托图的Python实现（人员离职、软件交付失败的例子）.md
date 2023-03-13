---
title: 项目管理中帕累托图的Python实现（人员离职、软件交付失败的例子）
description: 
published: true
date: 2023-03-13T01:42:32.655Z
tags: python, pmp, 项目管理, 质量管理
editor: markdown
dateCreated: 2023-03-13T01:42:32.655Z
---

#专栏/Python 
#专栏/项目管理
#专栏/数据分析

>摘要： 作为一名多次创业者和项目管理培训师， 今天田辛老师要做一件跨界的事情。 一方面， 田老师整理了项目管理中的重要质量管理工具 “帕累托图”， 另一方面，田老师给到了帕累托图的Python的实现方式。  如果您只对Python实现方式感兴趣的话， 不妨直接看最后一部分。 

作为一名多次创业者和项目管理培训师， 今天田辛老师要做一件跨界的事情。 一方面， 田老师整理了项目管理中的重要质量管理工具 “帕累托图”， 另一方面，田老师给到了帕累托图的Python的实现方式。  如果您只对Python实现方式感兴趣的话， 不妨直接看最后一部分。 

## 1 定义

**帕累托图**：是一种特殊的直方图， 在项目管理知识体系中属于质量管理的工具。 它可以帮助观众了解哪些因素对结果影响最大。它基于帕累托原则，即 80％ 的结果来自 20％ 的原因。该图表有助于以图形方式显示此原理。

![帕累托图.png](/项目管理/帕累托图.png)

## 2 帕累托原理
该原则也被称为`80/20 规则`、`关键少数法则`或`因子稀疏原则`。[约瑟夫·朱兰 (Joseph Juran)](/zh/项目管理/名人堂/朱兰)于 1937 年公布了这个概念，并以著名经济学家维尔弗雷多·帕累托的名字命名，他在 19 世纪后期首次记录了这种现象。

从本质上讲，帕累托指出，在许多地方，80/20 的分布很普遍，几乎存在于我们生活的各个方面。他最初的观察是关于人口和财富。他发现，意大利 80％ 的土地归 20％ 的人口所有。对其他国家的调查显示了类似的分布模式。

这种财富分配目前仍然成立。1992 年联合国开发计划署发布的一份报告显示，世界 20％ 的人口创造了世界人口收入的 80％ 左右。这种极其不平等的分配存在于税收、收入以及几乎所有其他生活领域。

**体育**：15％ 的棒球运动员创造了 85％ 的胜利，从理论上讲，这适用于所有体育项目。还有人说，20％ 的训练方法产生了 80％ 的收益。

**计算**：微软发现，修复 20% 最常报告的错误可以解决 80% 的错误和崩溃。这是 20% 的代码持有 80% 的错误。相反，最棘手的 20% 的编码需要开发人员 80% 的时间。

**安全**：职业健康与安全专业人员承认，20％ 的危险导致 80％ 的伤害。

**健康和社会福利**：20% 的患者使用 80% 的资源。80% 的犯罪是由 20% 的罪犯犯下的。这份清单涵盖了所有人类属性。

## 3 帕累托原则如何应用于商业
正如 80/20 规则适用于非商业领域的几乎所有场景一样，它也适用于商业环境。80% 的销售额来自于 20% 的销售人员。20% 的销售和营销活动带来了 80% 的业绩。在工厂中，80% 的缺陷是由 20% 的流程造成的。 80% 的投诉是由于 20% 的流程造成的。从本质上讲，几乎商业所有方面都反映了这一规则，而拥有显示数字的图表有助于组织识别和解决问题。

基本上，如果知道 20％ 的东西会产生最积极的结果，就可以向其中投入更多的资源，而不是把时间、精力和金钱浪费在对组织没有帮助的事情上。如果帕累托图显示 80％ 的业务来自 Facebook 广告，您就知道应该把精力集中在哪里。

## 4 什么时候应该使用帕累托图？
帕累托图在以下情况下是理想的选择：
- 您需要轻松地将重要问题传达给利益相关者
- 需要确定任务的优先级

帕累托图需要具有可以用持续时间、成本或频率进行衡量的数据。还需要有一个数据发生的时间范围。数据的频率在左轴上表示，问题或其他可测量值显示在横轴上，以条形表示。线形图所表示的百分比曲线在右侧有一个刻度。

为了更易于理解，可以用不同的颜色突出显示 20% 的数据，或者用标签来表明这是需要关注的业务领域。

## 5 帕累托图与条形图有何不同？

和最开始一样， 帕累托图是一种特殊的直方图（或称条形图）。对于帕累托图，条形是按从高到低的顺序显示的。对于条形图，并没有强制性地从高到低排序。条形图常常按字母顺序排序，或者按某种其他逻辑顺序排序。

如下图，就是一个直方图的案例。 
![直方图案例.png](/数据分析/直方图案例.png)
而对于帕累托图， 应该是这样的：
![没有积累曲线的帕累托图.png](/数据分析/没有积累曲线的帕累托图.png)
帕累托图还可以添加一个积累频数线条：
![插入积累频数线条的帕累托图.png](/数据分析/插入积累频数线条的帕累托图.png)

## 6 帕累托图的替代方案
尽管帕累托图没有真正的替代方案，但有一套七种基本的质量控制工具，应该一起使用，作为解决组织问题的整体方法的一部分：

- 因果关系图：找出问题的原因并将想法分为几类
- 检查表：提供收集和分析数据的结构化方法
- 控制图：研究过程如何随时间变化
- 直方图：显示频率分布，例如一组数据中某个值出现的频率
- 帕累托图：显示因子的重要性
- 散布图：识别关系和模式
- 分层：分离数据并确定模式
这些工具一起使用，构成了确保组织质量的基础。

## 7 帕累托图的好处
### 7.1 专注解决问题
如果在一条装配线上有 100 种产品，存在一系列故障、缺陷和问题，那么组织如何知道首先要解决什么问题？帕累托图会立即显示最大的问题，从而显示需要首先解决的过程或产品。如果一个故障部件导致了大部分问题，则可以很容易地确定修复的优先级。

### 7.2 提供机会
虽然你可以看到缺陷和问题，但帕累托图也可以用来识别优势。然后，你可以制定计划加以利用。例如，你可以向顶级销售人员或最佳分支机构询问他们的做法，进行复制。或者，如果一个团队特别有效，他们的技术和方法可以在整个企业中复制。

### 7.3 增强决策能力
领导团队希望为自己的组织做出最佳选择，但要了解什么会产生最大的影响可能很难。除了机器学习和人工智能之外，最有用的工具可能是帕累托图。可以清楚地看到最大的好处或问题出现在哪里，意味着可以基于数据有效地做出有针对性的决策。

## 8 帕累托图的缺点
### 8.1 没有根本原因分析
虽然帕累托图显示了结果，但没有明确的方法可以看到数据背后的原因。例如，如果一家公司的特定分支机构表现良好，在图表中就无法轻易了解为什么会出现这种情况。

解决方案：分析和数据完成后，需要进行全面调查，以显示这些结果是如何发生的。为什么分支机构表现良好？为什么工厂在制造产品时总会弄坏某个零件？

### 8.2 没有定量数据
帕累托图纯粹是定性的。没有迹象表明缺陷或问题的严重性。发现这些信息需要对问题进行彻底的调查和分析。

### 8.3 仅显示过去的数据
帕累托图仅显示过去的数据。损害或问题已经发生且无法更改。此外，无法真正预测基于这些数据所做的更改是否会产生所需的积极结果。例如，使用机器学习也有助于进行预测；如果你更改了 X，那么 Y 也会受到影响。

## 9 如何用Python创建帕累托图
### 9.1 数据源
下面这个代码是使用Excel作为数据文件，文件名为：`data.xlsx`
数据文件的内容如下：放在第一个工作表的第一个A1单元格开始即可。 
| category                 | value |
| ------------------------ | ----- |
| 工资待遇与福利水平较差   | 90    |
| 公司发展前景与预期落差大 | 40    |
| 激励机制较差             | 38    |
| 晋升机会少               | 35    |
| 当前职业无法发挥个人专长 | 30    |
| 工作压力较大             | 28    |
| 工作缺少成就感           | 26    |
| 上级处事方式较差         | 25    |
| 工作氛围较差             | 16    |
| 公司地理位置不便         | 13    |
| 职业发展方向变化         | 12    |
| 个人创业或继续求学深造   | 11    |
| 其它                     | 10    |
| 个人家庭原因             | 9     |
| 个人身体原因             | 5     |
### 9.2 源代码
```python

# 用于命名和保存图片文件
import os
from datetime import datetime


import matplotlib.font_manager as fm  # 管理字体工具
import matplotlib.pyplot as plt  # 绘图包
import pandas as pd # 读取Excel数据

# 设置字体
font_path = 'C:/Windows/Fonts/simhei.ttf'  # 字体文件路径
font_prop = fm.FontProperties(fname=font_path, size=12)  # 字体属性
plt.rcParams['font.family'] = font_prop.get_name()

# 读取Excel数据
df = pd.read_excel('data.xlsx')

# 建立数据category和标识符的对应关系
category_dict = {}
for i, category in enumerate(df['category'].unique()):
    category_dict[category] = chr(65 + i)
    df['category'] = df['category'].replace(category, chr(65 + i))

# 按照数量降序排列
df = df.sort_values(by='value', ascending=False)

# 计算累计百分比
df['cumulative_percentage'] = df['value'].cumsum() / df['value'].sum() * 100

# 绘制帕累托图
fig, ax1 = plt.subplots(figsize=(8, 10))

# 判断是否有小于80%的数据
if df['cumulative_percentage'].min() < 80:
    # 将小于80%的数据用红色柱子表示
    ax1.bar(df[df['cumulative_percentage'] < 80].index, df[df['cumulative_percentage'] < 80]['value'], color='tab:red')
else:
    # 将第一个柱子设为红色背景
    ax1.bar(df.index[0], df['value'][0], color='tab:red')

# 绘制其余柱子
bar_heights = ax1.bar(df.index, df['value'], color='tab:blue', alpha=0.5)
ax1.set_ylabel('数量', fontproperties=font_prop)

# 在每个柱子上方添加具体的值
for i, bar_height in enumerate(bar_heights):
    ax1.text(i, bar_height.get_height() + 0.5, str(int(bar_height.get_height())), ha='center', fontproperties=font_prop)

ax2 = ax1.twinx()
ax2.plot(df.index, df['cumulative_percentage'], color='tab:red', marker='o')
ax2.set_ylim([0, 100])
ax2.set_ylabel('累计百分比', fontproperties=font_prop)

plt.xticks(df.index, df['category'], rotation=90, fontproperties=font_prop)
plt.title('帕累托图', fontproperties=font_prop)

# 添加A-Z和category的对应关系
ax1.set_xticks(df.index)
ax1.set_xticklabels(df['category'], rotation=90, fontproperties=font_prop)
ax1.tick_params(axis='x', which='major', pad=15)
ax1.spines['bottom'].set_position(('axes', -0.00))
ax1.spines['bottom'].set_linewidth(0)
ax1.spines['bottom'].set_color('gray')
ax1.spines['bottom'].set_visible(True)

for i, (category, abbr) in enumerate(category_dict.items()):
    ax1.text(-1, -4 * i - 10, f'{abbr}: {category}', transform=ax1.transData, ha='left', fontproperties=font_prop,
             va='top')

# 调整子图之间的间距和边距
plt.subplots_adjust(bottom=0.4)

# 保存图片
now = datetime.now().strftime('%Y%m%d%H%M%S')
filename = os.path.join(os.path.dirname(os.path.abspath(__file__)), f'pareto_{now}.png')
plt.savefig(filename)

plt.show()
```

### 9.3 输出结果
![程序执行结果.png](/数据分析/程序执行结果.png)