# Git版本管理快速入门

## 版本管理概念

Git是一种**版本管理**系统。

什么是版本管理？

简单来说，就是对你的每一次修改进行管理。你可以随时查阅历史上你的所有修改，并随时恢复历史。

了解几个基本概念——

### 分布式版本控制系统

Git是一种分布式控制系统，版本库分布在各人的电脑上，同时，服务器上也有一个版本库。

大家各自改大家的，但统一使用服务器上的版本库作为最高目标和标准；

### Commit 提交
你做出修改之后，进行一次Commit，就会被记录为一个Commit修改，将生成一个Commit版本；

### Push 推送
将你本地的版本库，push给服务器的版本库，进行同步；

### Pull 拉取
将服务器的版本库，拉下来，进行更新；

### Branch 分支
默认的分支，叫master，你可以建立自己的分支，建立自己的小世界做自己的事情，其它人在master的所有修改，都跟你自己的分支无关；

## Git使用

### 网站

#### Github

注意了，很多人分不清Git和Github什么关系。

Git是版本管理工具，Github是一个网站，上面存放着全世界各种各样的Git版本库。

也有很多人误会Git是一个程序员的工具，Git是版本管理工具，像有很多的网站、文档、论文、新闻，都在使用Github。

#### Gitlab

一个Git仓库管理网站系统，你可以理解为，它是一个我们自己的Github私有化版。

我们的代码工程都存放在上面，并且围绕它做各种各样的产品管理、研发管理、文档管理。


### 工具

Git版本库的管理工具。

#### SourceTree

SourceTree作为Git管理工具，免费，全平台通用。

[https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/)

![SourceTree](./images/sourcetree.png)


#### Github Desktop

Github官方出品的Git管理工具，比较简单易用。

[https://desktop.github.com/](https://desktop.github.com/)

![Github Desktop](./images/githubdesktop.jpg)


#### Git命令

你也可以直接使用Git命令进行版本管理操作。

![Git Command Line](./images/gitcommand.png)
