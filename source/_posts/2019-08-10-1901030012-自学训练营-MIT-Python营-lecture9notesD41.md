---
title: 1901030012-MIT-自学 lecture9
date: 2019-08-10 23:50:10
tags: ['MIT', 'Python', '学习打卡']
categories: 'MIT60001'
---

### 学员信息

- 学号: 1901030012
- 学习内容: MIT第9课视频文稿p2
- 学习用时: 20mins Notes no.: Day41

### 学习笔记

1. [*Github Pulling changes from a remote repository*](https://help.github.com/en/articles/getting-changes-from-a-remote-repository#pulling-changes-from-a-remote-repository)

`git pull` is a convenient shortcut for completing both `git fetch` and `git merge` in the same command:  
```
$ git pull *remotename* *branchname*
# Grabs online updates and merges them with your local work
```

Because `pull` performs a merge on the retrieved changes, you should ensure that your local work is committed before running the `pull` command. If you run into *a merge conflict* you cannot resolve, or if you decide to quit the merge, you can use `git merge -- abort` to take the branch back to where it was in before you pulled.

2. [*Syncing a fork*](https://help.github.com/en/articles/syncing-a-fork)  
- [x] 2.1 Open Terminal.
- [x] 2.2 Change the current working directory to your local project.
- [x] 2.3 Fetch the branches and their respective commits from the upstream repository. Commits to `master` will be stored in a local branch, `upstream/master`.   
```
$ git fetch upstream  
> remote: Counting objects: 75, done.  
> remote: Compressing objects: 100% (53/53), done.  
> remote: Total 62 (delta 27), reused 44 (delta 9)  
> Unpacking objects: 100% (62/62), done.  
> From https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY  
> * [new branch]    master    -> upstream/master
```

- [x] 2.4 Check out your fork's local `master` branch.
```
$ git checkout master
> Switched to branch 'master'
```

- [x] 2.5 Merge the changes from `upstream/master` into your local `master` branch. This brings your fork's `master` branch into sync with the upstream repository, without losing your local changes.

```
$ git merge upstream/master  
> Updating a422352..5fdff0f  
> Fast-forward    
> README                    |     9 -------  
> README.md                 |     7 ++++++  
> 2 files changed, 7 insertions(+), 9 deletions(-)  
> delete mode 100644 README  
> create mode 100644 README.md  

```

If your local branch didn't have any unique commits, Git will instead perform a "fast-forward":  
```
$ git merge upstream/master
> Updating 34e91da..16c56ad  
> Fast-forward  
> README.md                 |    5 +++--  
> 1 file changed, 3 insertions(+), 2 deletions(-)  

```

3. 从Maestro给我们的参考资料入手，硬着头皮看了一遍，然后还是各种不知道该问什么问题。都不明白么？好像也不是。。。傻傻搞不明白这里面的具体操作，我就重新打字打一遍又看一次，well，好像没有那么陌生了，隐约觉得这个就是那天Maestro云淡风轻d秀肌肉使用的眼花缭乱的命令行技能？？？那我准备开始试着执行了哦。然后我就有第一个问题：  
*3.1 打开的Terminal是Mac的么？还是可以在VSCode里面的terminal里呢？*

果然哦，我在Mac的Terminal里输入的时候不知道要怎么输入 *remotename* 和 *branchname*，因为在`~`根目录下吧，所以报`fatal: not a git repository (or any of the parent directories): .git`。然后我在VSCode里面，显示的是我本地已经clone下来的selfteaching-learning-notes.github.io文件目录，然后`git pull`就居然就显示：  
```
cat at cattekimbp in ~/Documents/GitHub/selfteaching-learning-notes.github.io on source  
$ git pull  
Already up to date.
(base)  
```
尝试在Mac的Terminal里输入我猜的 *remotename* 和 *branchname*，我觉得我`.git`文件路径的问题么？是命名的问题么？我要去睡觉了，说不定我能梦到我在Google解。哈哈哈哈。加油，白天喝了咖啡再来玩。。。我觉得我似乎找到了一点儿`玩`的赶脚了。吾厘Maestro 万岁！！！yeah！
