---
layout: post
title: git 使用总结
category: other
excerpt: git成长之路
tags: [other]
---

git 使用总结

## git 简介
Git是Linux之父Linus的第二个伟大的作品，它最早是在Linux上开发的，被用来管理Linux核心的源代码。后来慢慢地有人将其移植到了Unix、Windows、Max OS等操作系统中。

Git是一个分布式的版本控制系统，与集中式的版本控制系统不同的是，每个人都工作在通过克隆建立的本地版本库中。也就是说每个人都拥有一个完整的版本库，查看提交日志、提交、创建里程碑和分支、合并分支、回退等所有操作都直接在本地完成而不需要网络连接。

对于Git仓库来说，每个人都有一个独立完整的仓库，所谓的远程仓库或是服务器仓库其实也是一个仓库，只不过这台主机24小时运行，它是一个稳定的仓库，供他人克隆、推送，也从服务器仓库中拉取别人的提交。

## git 常用命令

1、从远程仓库克隆项目
> git clone 项目地址

2、创建分支，然后切换到分支
> git checkout -b dev

3、查看当前分支
> git branch,git branch命令会列出所有分支，当前分支前面会标一个*号

4、合并指定分支到当前分支
> git merge dev

5、删除本地dev分支
> git branch -d dev

6、删除远程dev分支
> git push origin :dev

7、切换分支
> git checkout [name]

8、查看远程库的信息
> git remote

9、推送分支
> git push origin master

10、拉取分支
> git pull

11、查看文件状态
> git status 

12、查看历史提交记录
> git log

13、将暂存区的内容提交到当前分支
> git commit -m "git tracks changes"

14、将工作去的内容放入版本库的暂存区
> git add [fileName]

15、查看工作区和版本库里面最新版本的区别
> git diff HEAD – [fileName]

16、将当前版本回退到上一个版本
> git reset --hard HEAD^

17、将当前版本回退到上两个版本
> git reset --hard HEAD^^

18、回退到指定版本
> git reset --hard commit_id


## 问题处理
1、gitignore规则不生效

> .gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。
解决方法就是先把本地缓存删除（改变成未track状态），然后再提交:
>> git rm -r --cached .
>>> git add .
>>>> git commit -m 'update .gitignore'