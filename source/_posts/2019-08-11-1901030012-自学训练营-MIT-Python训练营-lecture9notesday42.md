---
title: 1901030012-MIT-自学 lecture9
date: 2019-08-11 23:20:00
tags: ['MIT', 'Python', '学习打卡']
categories: 'MIT60001'
---

### 学员信息

- 学号: 1901030012
- 学习内容: MIT第9课视频文稿p2-5
- 学习用时: 20mins Notes no.: Day42

### 学习笔记

1. *self*  
We defined the class in the sort of general way, OK? So we needed a way to be able to access *data attributes* of *any instance*. So we use this `self` variable, OK? And the self variable we used to refer to *any instance*-- to the data attributes of any instance in a general way **without** actually having a particular instance in mind, OK?

2. *methods*  
the bottom line of the class definition is that **your class defines all of the data**-- so data attributes-- and all of the methods that are going to **be common across all of the instances**. So any instance that you create of a particular object type, that instance is going to have this *exact same structure*, OK? The difference is that every instance's *values* are going to be different.

So when you're creating *instances of classes*, you can create more than one instance of the same class. So we can create a Coordinate object here using this syntax right here. So you say the type, and then, whatever values it takes in. And you can create more than one Coordinate object.

Each Coordinate object is going to have different data attributes. Sorry, *it's going to have different data attribute `values`*, OK? Every Coordinate object is going to have an x value and a y value. But the x and y values among different instances are going to vary, OK? **So that's the difference between defining a class and looking at a particular instance of a class.**

So instances have the *structure of the class*. So for a coordinate, all instances have an x value and a y value. But the actual values are going to vary between the different instances.

3. *Use OOB(Object-oriented Programming)*  
so ultimately, why do we want to use object-oriented programming? So, so far, the examples that we've seen were numerical, right-- a coordinate, a fraction. But *using object oriented programming*, **you can create objects that mimic real life**. So if I wanted to create
objects of-- an object that defined a cat and an object that defined a rabbit, I could do that with object-oriented programming. I would just have to decide, as a programmer, what data and what methods I'd want to assign to these groups of objects.

So I'm grouping sets of objects that are going to have the same attributes together. And attributes-- this is also a recap of last time-- come in **two** forms, right, *data attributes* and *procedural attributes*. So the data attributes are basically things that define what the object is.

So how do you represent a cat as an object? And *it's up to you, as the programmer, to decide how you want to do that*.

*Procedural attributes* were also known as *methods*. And the methods are essentially asking, what can your object do, OK? So how can someone who wants to use your object-- how can someone interact with it?

4. *getters and setters*
All right, so now we have this class, Animal. We've done the first part here, which is to initialize the class, right? So we've told Python how to create an object of this type.

There's a few other *methods* here that I've implemented. Next two we call *getters*, and the two after that we call *setters*, OK? And getters and setters are very *commonly used when implementing a class*. So getters essentially return the values of any of the data attributes, OK? So if you look carefully, `get_age()` is just returning `self.age` , and `get_name()` just returns `self.name` . So they're very simple methods. Similarly, `set_age()` and `set_name()`-- we're going to see what this funny equal sign is doing here in the next couple of slides. But setters do a very similar thing where they're going to set the data attributes to whatever is passed in, OK?

5. `#学习Python有力量`，我已经可以和Alucard沟通某些我原来完全不知道要怎么沟通的话题，因为原来在他提到的那些概念、理论时我完全不能听到大脑里，因为我完全不熟悉，，，现在，我感觉我不会因为害怕而宕机不听了，我会尝试提问，还是in a smarty way。hiahiahia。
