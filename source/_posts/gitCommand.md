---
title: Git常用命令
date: 2022-09-09 16:15:57
tags:
- Git常用命令
categories:
- Git
top_img: /img/cover11.jpg
cover: /img/cover11.jpg
---
## Git 基本操作
{% note info no-icon%}
Git 的工作就是创建和保存你项目的快照及与之后的快照进行对比。
Git 常用的是以下 6 个命令：git clone、git push、git add 、git commit、git checkout、git pull
{% endnote %}
### 说明：
{% note info no-icon%}
workspace：工作区
staging area：暂存区/缓存区
local repository：版本库或本地仓库
remoterepository：远程仓库
{% endnote %}
### 简单的操作步骤
```
  $ git init //初始化仓库。
  $ git add .  // 添加文件到暂存区。
  $ git commit  //将暂存区内容添加到仓库中。
```
### 创建仓库
{% note info no-icon%}
  下表列出了 git 创建仓库的命令：
{% endnote %}
| 命令 | 说明 | 
|:-----|:-----|
| git init | 初始化仓库 |
| git clone | 拷贝一份远程仓库，也就是下载一个项目 |
### 本地项目关联到远程仓库
| 命令 | 说明 | 
|:-----|:-----|
| git remote add origin https://github.com/xienb/NPC.git | 关联到远程仓库 |
### 提交与修改
{% note info no-icon%}
  Git 的工作就是创建和保存你的项目的快照及与之后的快照进行对比。
  下表列出了有关创建与提交你的项目的快照的命令：
{% endnote %}
| 命令 | 说明 | 
|:-----|:-----|
| git add	| 添加文件到仓库 |
| git status | 查看仓库当前的状态，显示有变更的文件 |
| git diff | 比较文件的不同，即暂存区和工作区的差异 |
| git commit -m “备注” | 提交暂存区到本地仓库 |
| git reset | 回退版本 |
| git reset HEAD | 用于取消已缓存的内容 |
| git rm | 删除工作区文件 |
### 提交日志
| 命令 | 说明 | 
|:-----|:-----|
| git log	                 | 查看历史提交记录 |
| git log --oneline	        | 查看历史记录的简洁的版本 |
| git log --oneline --graph | 查看历史中什么时候出现了分支、合并 |
| git blame	                | 以列表形式查看指定文件的历史修改记录 |
### 远程操作
| 命令 | 说明 | 
|:-----|:-----|
| git remote | 远程仓库操作 |
| git fetch	  | 从远程获取代码库 |
| git pull	 | 下载远程代码并合并 |
| git push	  | 上传远程代码并合并 |
### 分支管理
| 命令 | 说明 | 
|:-----|:-----|
|git branch (branchname)	              |  创建分支命令|
|git checkout (branchname)	            |   切换分支命令|
|git merge	                            |   合并分支命令|
|git pull origin (branchname)	          |从远程分支（branchname）合并到当前分支|
|git branch -r	                        |  查看远程分支|
|git branch -vv	                        |查看分支详细信息|
|git fetch	                            |  同步远程仓库|
|git branch -d (branchname)	            |删除分支|
|git checkout -b (branchname)	          | 创建并切换到分支|
|git push origin (branchname)	          | 创建远程分支|
|git checkout -b feature origin/dev	    |  从远程分支dev创建本地分支feature|
|git push origin --delete (branchname)	|     删除远程分支dev|
|git remote updata origin -p	          |     更新远程分支列表|
### 标签管理
| 命令 | 说明 | 
|:-----|:-----|
| git tag	| 查看所有标签名称|
| git tag -ln	|显示标签名及其描述信息|
| git tag (tag_name)	|为当前分支指向的commit记录创建标签|
| git tag (tag_name) (hash_val)	|为指定的commitId创建标签|
| git tag -a (tag_name) -m “msg” (hash_val)	|合并分支命令|
| git tag -d (tag_name)	|删除本地的标签|
| git push origin (tag_name)	|将标签推送到远程服务器|
| git push origin --tags	|将本地的全部tag推送到远程服务器|
| git push (remote_name) :refs/tags/(tag_name)	|删除远程标签|
| git archive --format=zip --output=src/xxx.zip (tag_name)	|标签内容提取：提取为zip格式，src可以是相对路径，也可以是绝对路径|
| git checkout (tag_name)	|切换到指定标签|
