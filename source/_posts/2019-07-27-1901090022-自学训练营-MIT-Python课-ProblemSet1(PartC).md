---
title: 1901090022-MIT60001-ProblemSet1(PartB)
date: 2019-07-27
tags: ['Python', 'MIT', '学习打卡']
categories: 'MIT60001'
---

### 打卡记录
- 学号：1901090022
- 学习课程：[Introduction to Computer Science and Programming in Python](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/)
- 学习内容：[Problem Set 1 (PDF)](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/assignments/MIT6_0001F16_ps1.pdf)
- 打卡天数：D04

### Part C 作业要求（截取）:
Part C: Finding the right amount to save away

In Part B, you had a chance to explore how both the percentage of your salary that you save each month and your annual raise affect how long it takes you to save for a down payment. This is nice, but suppose you want to set a particular goal, e.g. to be able to afford the down payment in three years. How much should you save each month to achieve this? In this problem, you are going to write a program to answer that question. To simplify things, assume:

1. Your semi­annual raise is .07 (7%)
2. Your investments have an annual return of 0.04 (4%)
3. The down payment is 0.25 (25%) of the cost of the house
4. The cost of the house that you are saving for is $1M.

You are now going to try to find the best rate of savings to achieve a down payment on a $1M house in 36 months. Since hitting this exactly is a challenge, we simply want your savings to be within $100 of the required down payment.

In ps1c.py, write a program to calculate the best savings rate, as a function of your starting salary. You should use bisection search to help you do this efficiently. You should keep track of the number of steps it takes your bisections search to finish. You should be able to reuse some of the code you wrote for part B in this problem.

Because we are searching for a value that is in principle a float, we are going to limit ourselves to two decimals of accuracy (i.e., we may want to save at 7.04% ­­ or 0.0704 in decimal – but we are not going to worry about the difference between 7.041% and 7.039%). This means we can search for an integer between 0 and 10000 (using integer division), and then convert it to a decimal percentage (using float division) to use when we are calculating the current_savings after 36 months. By using this range, there are only a finite number of numbers that we are searching over, as opposed to the infinite number of decimals between 0 and 1. This range will help prevent infinite loops. The reason we use 0 to 10000 is to account for two additional decimal places in the range 0% to 100%. Your code should print out a decimal (e.g. 0.0704 for 7.04%).

Try different inputs for your starting salary, and see how the percentage you need to save changes to reach your desired down payment. Also keep in mind it may not be possible for to save a down payment in a year and a half for some salaries. In this case your function should notify the user that it is not possible to save for the down payment in 36 months with a print statement. Please make your program print results in the format shown in the test cases below.

Note: There are multiple right ways to implement bisection search/number of steps so your results may not perfectly match those of the test case.

### 作业心得
PartC的作业，根据以下前提条件，计算如果3年内要付首付，每月最优存款比例：
1. 年薪涨幅是 .07 (7%)
2. 投资年回报率是 0.04 (4%)
3. 首付是总款的0.25(25%)
4. 总款是1百万

有几点需要注意：
- 需要用到 bisection search 算法
- 每月存款比例保留小数点后两位，比如7.041%，使用浮点数表示为 0.0741，所以我们可以利用0-10000的整数来做算法计算，最后再转化为float


本次作业学习到以下知识点：
- 需要用到 bisection search 算法，可以参考以下链接：https://stackoverflow.com/questions/47196917/python-bisection-search-exercise
- python 在函数外定义变量，默认是全局变量，在函数中默认能够读取，但无法修改，参考：https://www.programiz.com/python-programming/global-keyword

程序逻辑引入了全局变量，显得不太优雅，仍有改善空间。

程序实现的时候，参考了一下连接：
https://github.com/iamwhil/6.0001（运行结果与作业中的测试相符）
https://github.com/kaizenflow/6.0001-ps1（无法得到正确的结果）


### 程序代码
``` python
# 起始年薪
annual_salary = 1500000
# annual_salary = float(input("Enter the starting salary:"))

# 房价
total_cost = 1000000

# 薪资涨幅
semi_annual_raise = 0.07
# 首付比例
portion_down_payment = 0.25
# 存款年化率
R = 0.04

deep = 0

# 首付
down_payment = total_cost * portion_down_payment

last_portion_saved = False

def month_counter(current_savings, annual_salary, portion_saved):
    # 当前月份
    month_count = 1
    # while loop
    while True:
        # 当月情况判断
        # 计算当月存款 = 存款 + 月薪*每月薪资存款比例 + 投资回报
        current_savings = current_savings + annual_salary/12*portion_saved + current_savings*R/12

        # 如果存款 和 首付，相差不到100，也算达成条件
        if current_savings >= down_payment:
            break
        
        if month_count % 6 == 0:
            annual_salary += annual_salary * semi_annual_raise

        # 月份自增
        month_count += 1

    return [month_count, current_savings]

def bisection_search(portion_saved_rates, annual_salary):
    global last_portion_saved
    global deep
    deep += 1

    # 计算中位数，【//】 符合表示除法的商是整数
    if len(portion_saved_rates) == 1:
        return last_portion_saved


    middle = len(portion_saved_rates) // 2
    portion_saved = portion_saved_rates[middle] / 10000

    init_current_savings = 0

    # 如何计算的月份与预期相等
    res = month_counter(init_current_savings, annual_salary, portion_saved)
    month_count = res[0]
    current_savings = res[1]

    # print(portion_saved_rates, month_count, current_savings, portion_saved, abs(current_savings - down_payment))

    if month_count == month_count_expect:
        last_portion_saved = portion_saved_rates[middle]
        if abs(current_savings - down_payment) > 100:
            return bisection_search(portion_saved_rates[:middle], annual_salary)
        else:
            return portion_saved_rates[middle]
    elif month_count > month_count_expect:
        # 计算的月份比期望的大，说明存款比例少了,要提升比例
        # print(portion_saved_rates[:middle])
        return bisection_search(portion_saved_rates[middle:], annual_salary)
    else:
        return bisection_search(portion_saved_rates[:middle], annual_salary)

portion_saved_rates = range(0, 10000)
month_count_expect = 36

res = bisection_search(portion_saved_rates, annual_salary)
if res is False:
    print("It is not possible to pay the down payment in three years.")
else:
    print("Best savings rate: {}".format(res/10000))
    print(res/10000) 
    print("Steps in bisection search: {}".format(deep)) 
```