---
title: 1901030012-自学训练营-MIT-自学 lecture9
date: 2019-08-30 23:59:09
tags: ['MIT', 'Python', '学习打卡']
categories: 'MIT60001'
---

### 学员信息

- 学号： 1901030012
- 学习内容：MIT视频文稿lecture9p7-8
- 学习用时：145mins Notes no.: Day44



### 学习笔记

1. **default arguments** 

   > because newname actually has a default argument, OK? So that tells Python, if no parameter is passed in for this particular formal parameter, then use whatever is up here by default. So if I haven't passed in the parameter a.get_na-- a.set_name(), sorry-- a.sett_name() is going to be setting the name to the empty string, because that's what the default parameter is. So in the next line, when I print a.get_name(), this is just going to print the empty string,

   > 
   >
   > Whatever you pass in overrides the default argument, and everything is good.  

   > If you don't provide a default argument for newname and you do this case here, then that's going to give you an error.   

   如果有默认值的，不赋值就使用默认值，如果没有设置默认值，python也会friendly的使用报错提示需要至少默认值赋值。

   

2. **hierarchies**

   >So the great thing about object- oriented programming is that it allows us to add layers of abstraction to our code, all right? So we don't need to know how very, very low-level things are implemented in order to use them. And we can build up our code to be more and more complex as we use up these different abstractions.

   object -- Parent class -- child class

   十分形象的表达，我终于看到营友们之前提到的继承了。。。

   

3. what will happen?

   > So the idea here is, when you have hierarchies, you have a parent class, you have a child class, you could have a child class to that child class, and so on and so on. So you can have multiple levels of inheritance.

   > What happens when you create an object that is of type something that's been-- of a type that's the child class of a child class of a child class, right? What happens when you call a method on that object? Well, Python's are going to say, does a method with that name exist in my current class definition? And if so, use that.
   >
   > But if not, then, look to my parents. Do my parents know how to do that, right? Do my parents have a method for whatever I want to do? If so, use that. If not, look to their parents, and so on and so on. So you're sort of **tracing back up** your ancestry to *figure out* **if you can do this method or not**.

   wow, niubility...

   

4. avaibility cascades shuffled me...我太关注那部分超小概率事件，不过，能观察到自己的注意力受到的外部压力影响，也是很开心的一点收获，还好有俺们营这个habitat，我再shifting away都能游回来。感谢这里的所有人。

   

5. 硬着头皮和教练沟通，加上自己数据营的作业的进展，让我开始理解寻找适合我的方法时候已有方案可以再改进的地方，我还是被自己的一些原有不清晰的概念而限制了。完成任务是目标，eyes on the very task！出発する。

   

