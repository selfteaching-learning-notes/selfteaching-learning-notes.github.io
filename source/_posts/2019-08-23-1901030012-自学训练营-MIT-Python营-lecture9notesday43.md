---
title: 1901030012-MIT-自学 lecture9
date: 2019-08-23 04:30:00
tags: ['MIT', 'Python', '学习打卡']
categories: 'MIT60001'
---

### 学员信息

- 学号: 1901030012
- 学习内容: MIT第9课视频文稿p6
- 学习用时: 128mins Notes no.: Day43

### 学习笔记

1. **Information hiding**

> So the whole reason why we’re using **classes** in object-oriented programming is so that you can abstract certain data from the user. One of the things you should be abstracting is these data attributes. So users shouldn’t really need to know how a class is implemented.
> They should just know ~how to use the class.~

> Eg: Let’s say whoever wrote the Animal class wants to change the implementation. And they’ve decided they don’t want to call the data attribute “age” anymore, they want to call it “years,” OK? So when they initialize an animal they say `self.years = age`. So an animal still gets initialized by its age. And the age gets passed into a data attribute named “years,”.

> Since I’m implementing this class, I want to have a getter, which is going to return `self.years`. So I’m not returning `self.age` anymore, because age is no longer the data attribute I’m using. So with this new implementation, if someone was using this implementation and was accessing age directly as— was accessing the data attribute age directly— with this new implementation, they’d actually get an *error*, right? **Because this animal that they created using my old implementation no longer has an attribute named “age.” And so Python’s going to spit out an error saying no attribute found or something like that.**

> If they were using the getter `a.get_age()`— the person who implemented the class reimplemented `get_age() `to work correctly, right, with their new data attribute, years, as opposed to age— so if I was using the getter `get_age()`, I wouldn’t have run into the bug, OK? So things to remember— ~write getters and setters for your classes.~ And ~later on in your code, use getters and setters to prevent bugs and to promote easy to maintain code.~

> *so information hiding is great.* But having said that, Python’s actually **not very great at** information hiding, OK? Python allows you to do certain things that you should **never** be doing:
> ~1.~ The first is to access data attributes from outside of the class, OK? So if I were to say a.age, Python allows me to do that without using a getter and setter.
> ~2.~ Python also allows you to write to data attributes from outside the class. [Eg](: So if I implemented the class Animal assuming that age was a number, an integer, and all of my methods work as long as age is an integer, but someone decided to be smart and, outside of the class, set age to be infinite as a string, that might cause the code to crash, OK? Python allows you to do that. But now you’re breaking the fact that age has to be an integer, right? So now the methods should probably be checking the fact that age is an integer all the time.)
> ~3.~ The other thing that you're allowed to do is to create data attributes outside of the class definition. [Eg](So if I wanted to create a new data attribute called “size” for this particular instance, Python also allows me to do that. And I can set it to whatever I want, OK? So Python allows you to do all these things, but it’s actually not good style to do any of them. So just don’t do it. All right.)


2. My boogieman is living in my illusion. Too much read between the lines.

3. 我就是想得offlined多一些。我如果不想做，想啥都不切题。有病要治，尝试找解药：

~3.1~ `Marcus.sleightofhand`

> **“上手”，才能解决焦虑。**“上手”，没有重点，但是有“通”点。……永远记得，我们真正的目标是，“上”手。

> ……如何给自己制造反馈。要制造反馈，你必须先有成果，制造反馈的目的就是要基于已有的成果来发现问题。所以要制造反馈，我们可能要写一点东西，录制一点音频，甚至录像，这些是给自己制造反馈的最佳手段。总结来说就是要及时输出。

> 你学了一些东西之后，一定要想办法讲出来或应用出来，这正是给自己制造反馈。所以你一定要积极地给别人讲东西，……

> 缺少反馈的一个最常见的情况是，我们平时会看一些书，看完了也就过去了，时间长了也就忘记了。就是因为没有反馈，我们并没有笑话书中的重要内容。
>       **—— Marcus XU “SLEIGHT ~OF~ HAND”**

~3.2~ `My Angel.letustalkaboutit`

@糖糖今天在AMA里也回答了我的问题，以任务为导向开干，而且不能闭门造车，要持续反馈和反复沟通。
所以，实际上最好的antivirus methods就是该干嘛干嘛，该作作业啊，，，“躲”着是个什么事儿，打开了作业指引读不进去的主要原因就是没想做作业。。。一条一条的读，记住自己读这个指引的任务是什么，拆解到最小单位的尝试输出，if offlined please try shifting back，practice makes progress。

~3.3~ `Max.piggiefight`

其实最大的鼓励还是来源于Max猪，他和爸比在玩的有一个游戏就是统计类的，然后他昨天的观察作业就是花的结构。和我数据营的作业一毛一样啊，，，他也不知道完整的统计啊，他也一开始并不全面知道花的那些结构的名词和作用啊，人家就是不怕地、兴致勃勃地完成自己的任务啊，他特别不理解的看着我苦闷的脸，然而，他还是patpat我说：麻麻你别怕哈，你来用电脑写你的作业，不懂的，我来教你。

4. **Eyes on “ME”**.

哎，四岁八个月的“我”，比同龄Max却还有很多心理建设需要做，好吧，还好我有Max的鼓励和支持，有这个自学营的小伙伴们，也说明我进步了，至少我不像以往那样封闭，而是在努力地追望着营友们的背影，现在爬行追赶。

我们每个人的学习方法是不同的，要摸索自己适合的方法，摸索靠``“上手”``呀，谢谢自学营里每一位campmates们的鼓励、帮助与支持，有你们的世界真好，**加油Cat!** 感谢教练们，，，让我再gu（四声）qiu（轻声）一会儿。。。。。。黑线脸喵。。。
