---
title: 2019-07-26-1901090022-MIT60001-ProblemSet1(PartB)
date: 2019-07-26
tags: ['Python', 'MIT', '学习打卡']
categories: 'MIT60001'
---

### 打卡记录
- 学号：1901090022
- 学习课程：[Introduction to Computer Science and Programming in Python](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/)
- 学习内容：[Problem Set 1 (PDF)](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/assignments/MIT6_0001F16_ps1.pdf)
- 打卡天数：D03

### Part A 作业要求（截取）:
Part B: Saving, with a raise

Background

In Part A, we unrealistically assumed that your salary didn’t change. But you are an MIT graduate, and clearly you are going to be worth more to your company over time! So we are going to build on your solution to Part A by factoring in a raise every six months.

In ps1b.py, copy your solution to Part A (as we are going to reuse much of that machinery). Modify your program to include the following

1. Have the user input a semi-annual salary raise semi_annual_raise (as a decimal percentage)
2. After the 6 th month, increase your salary by that percentage. Do the same after the 12 th month, the 18 th month, and so on.

Write a program to calculate how many months it will take you save up enough money for a down payment. LIke before, assume that your investments earn a return of r = 0.04 (or 4%) and the required down payment percentage is 0.25 (or 25%). Have the user enter the following variables:

1. The starting annual salary (annual_salary)
2. The percentage of salary to be saved (portion_saved)
3. The cost of your dream home (total_cost)
4. The semi­annual salary raise (semi_annual_raise)

### 作业心得
PartB的作业其实和PartA的整体思路差不多，主要是增加了一个变动收入，没6个月加薪

写一个程序用于计算 需要多少个月储蓄才够首付，大多数变量都需要float类型，所以需要将用户的输入转化为float，程序需要用户输入以下变量：:

1. 一开始的年薪 (annual_salary)
2. 每月存款的比例 (portion_saved)
3. 房子的价钱 (total_cost)
4. 提薪的比率（semi_annual_raise）

整体的思路就是做一个循环，每个迭代就是一个月，判断当月 的存款是否大于等于首付。
存款由三部分组成：
1. 已有存款
2. 月薪按比例存款；月薪每6个月有涨幅（这里是重点，原文是after 6th month，也就是第7个月薪资变动才生效，而不是第6个月）
3. 每月投资回报


### 程序代码
``` python
# 起始年薪
# annual_salary = 75000
annual_salary = float(input("Enter your annual salary:"))

# 每月薪资存款比例
# portion_saved = .05
portion_saved = float(input("Enter the percent of your salary to save, as a decimal:"))

# 房价
# total_cost = 1500000
total_cost = float(input("Enter the cost of your dream home:"))

# 薪资涨幅
# semi_annual_raise = 0.05
semi_annual_raise = float(input("The semi­annual salary raise:"))


# 首付比例
portion_down_payment = 0.25
# 存款年化率
r = 0.04
# 当前存款
current_savings = 0
# 当前月份
month_count = 1

# 首付
down_payment = total_cost * portion_down_payment

# while loop
while True:
    # 当月情况判断    

    # 计算当月存款 = 存款 + 月薪*每月薪资存款比例 + 投资回报
    current_savings = current_savings + annual_salary/12*portion_saved + current_savings*r/12

    # print("第{}个月，薪水{}，存款{}，首付{}".format(month_count, annual_salary, current_savings, down_payment))

    if current_savings >= down_payment:
        print("Number of months: {}".format(month_count))
        break
    if month_count % 6 == 0:
        annual_salary += annual_salary * semi_annual_raise

    # 月份自增
    month_count += 1
```