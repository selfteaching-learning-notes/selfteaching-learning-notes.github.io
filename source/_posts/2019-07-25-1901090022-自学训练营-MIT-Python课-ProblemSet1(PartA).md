---
title: 1901090022-MIT60001-ProblemSet1(PartA)
date: 2019-07-25
tags: ['Python', 'MIT', '学习打卡']
categories: 'MIT60001'
---

### 打卡记录
- 学号：1901090022
- 学习课程：[Introduction to Computer Science and Programming in Python](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/)
- 学习内容：[Problem Set 1 (PDF)](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/assignments/MIT6_0001F16_ps1.pdf)
- 打卡天数：D02

### Part A 作业要求（截取）:

Part A: House Hunting 

You have graduated from MIT and now have a great job! You move to the San Francisco Bay Area and decide that you want to start saving to buy a house. As housing prices are very high in the Bay Area, you realize you are going to have to save for several years before you can afford to make the down payment on a house. In Part A, we are going to determine how long it will take you to save enough money to make the down payment given the following assumptions: 

1. Call the cost of your dream home total_cost. 

2. Call the portion of the cost needed for a down payment portion_down_payment. For simplicity, assume that portion_down_payment = 0.25 (25%). 

3. Call the amount that you have saved thus far current_savings. You start with a current savings of $0. 

4. Assume that you invest your current savings wisely, with an annual return of r (in other words, at the end of each month, you receive an additional current_savings\*r/12 funds to put into your savings – the 12 is because r is an annual rate). Assume that your investments earn a return of r = 0.04 (4%). 

5. Assume your annual salary is annual_salary. 

6. Assume you are going to dedicate a certain amount of your salary each month to saving for the down payment. Call that portion_saved. This variable should be in decimal form (i.e. 0.1 for 10%). 

7. At the end of each month, your savings will be increased by the return on your investment, plus a percentage of your monthly salary (annual salary / 12). 

Write a program to calculate how many months it will take you to save up enough money for a down payment. You will want your main variables to be floats, so you should cast user inputs to floats. 

Your program should ask the user to enter the following variables: 

1. The starting annual salary (annual_salary) 
2. The portion of salary to be saved (portion_saved) 
3. The cost of your dream home (total_cost) 

### 作业心得 

光看懂英文作业已经蛮吃力了，哈哈，简化作业说明如下： 

1. 买房子的总费用为 **total_cost** 
2. 首付（down payment）为25%, portion_down_payment = 0.25 
3. 存款为 **current_savings**，从0开始 
4. 存款有投资，年回报率（an annual return）为**r**（0.04），所以每月额外收入为 **current_savings\*r/12** 
5. 年薪为 **annual_salary** 
6. 从每月薪资中，固定比例用于首付，这个比率设为 **portion_saved** 
7. 每个月的收入来源，主要是 投资回报 + 每月工资 **monthly salary**（annual salary / 12） 

写一个程序用于计算 需要多少个月储蓄才够首付，大多数变量都需要float类型，所以需要将用户的输入转化为float，程序需要用户输入以下变量：: 

1. 一开始的年薪 (annual_salary) 
2. 每月存款的比例 (portion_saved) 
3. 房子的价钱 (total_cost) 

整体的思路就是做一个循环，每个迭代就是一个月，判断当月 的存款是否大于等于首付。 

存款由三部分组成： 

1. 已有存款 
2. 月薪按比例存款 
3. 每月投资回报 

### 程序代码 

``` python 
# 起始年薪 
# annual_salary = 120000 
annual_salary = float(input("Enter your annual salary:")) 

# 每月薪资存款比例 
# portion_saved = .10 
portion_saved = float(input("Enter the percent of your salary to save, as a decimal:")) 

# 房价 
# total_cost = 1000000 

total_cost = float(input("Enter the cost of your dream home:")) 

# 首付比例 
portion_down_payment = 0.25 

# 存款年化率 
r = 0.04 

# 当前存款 
current_savings = 0 
month_count = 1 
# 首付 
down_payment = total_cost * portion_down_payment 

while True: 
    # 计算当月存款 = 存款 + 月薪*每月薪资存款比例 + 投资回报 
    current_savings = current_savings + annual_salary/12*portion_saved +     current_savings*r/12 
    if current_savings >= down_payment: 
        print("Number of months: {}".format(month_count)) 
        break 
    # 月份自增 
    month_count += 1 
``` 