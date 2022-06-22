**Git各指令的本质**

- [Git各指令的本质](#git各指令的本质)
  - [前言](#前言)
  - [Linux相关](#linux相关)
    - [创建目录（/文件夹）](#创建目录文件夹)
    - [创建文件](#创建文件)
    - [进入目录](#进入目录)
  - [基本概念](#基本概念)
    - [文件状态](#文件状态)
    - [commit节点](#commit节点)
    - [HEAD](#head)
    - [远程仓库](#远程仓库)
  - [分支](#分支)
    - [什么是分支](#什么是分支)
    - [分支的作用](#分支的作用)
  - [命令详解](#命令详解)
    - [提交相关](#提交相关)
    - [分支相关](#分支相关)
    - [合并相关](#合并相关)
    - [回退相关](#回退相关)
    - [远程相关](#远程相关) 
    - [常用命令](#常用命令)

真是通俗易懂哈

## 前言

> 作为当前世界上最强大的代码管理工具<mark>Git</mark>相信大家都很熟悉，但据我所知大部分人还停留在**clone、commit、pull、push**...的阶段是不是对rebase心里没底，只敢用merge？碰到版本回退就抓瞎？别人问我怎么知道的，嘿嘿，因为曾经我也是~。针对这些问题，今天好好总结一下对Git的认知和深入理解，尽可能从本质上讲解Git，了解Git的底层原理，更加熟练地使用Git指令。

## Linux相关

### 创建目录（/文件夹）

通过 **mkdir** 

> * 当前目录下，创建目录 <u>HelloGit</u>：**`mkdir HelloGit`**
> 
> * 在 <u>/home</u> 目录下，创建目录 <u>HelloGit</u>：**`mkdir /home/HelloGit`**

### 创建文件

通过 **touch**

> * 在当前目录下，创建文件<u> helloGit.txt </u>：**`touch helloGit.txt`**
> 
> * 在 <u>/home</u> 目录下，创建文件 <u>helloGit.txt</u>：**`touch /home/helloGit.txt`** 

### 进入目录

通过 **cd**

> * 进入 <u>helloGit</u> 目录：**`cd helloGit`**
> 
> * 进入 <u>/home/helloGit</u> 目录：**`cd /home/helloGit`**
> 
> * 返回上一级目录：
>   
>   > 上一级目录可以用  **`..`** 代替
>   > 
>   > 进入上一级目录：**`cd ..`**
>   > 
>   > 进入上一级目录后再上一级目录：**`cd ../../`**
>   > 
>   > 进入上一级目录下的 <u>helloGit</u>：**`cd ../helloGit`**

## 基本概念

Git是一个**分布式**代码管理工具，在讨论分布式之前避免不了提及一下什么是**中央式**代码管理工具。

> * 中央式：所有代码保存在中央服务器，所以提交必须依赖网络，并且每次提交都会带入到中央仓库，如果是协同开发可能频繁触发代码合并，进而增加提交的成本和代价，最典型的就是svn
> 
> * 分布式：可以本地提交，不需要依赖网络，并且将每次提交自动备份到本地。每个开发者都可以八远程仓库clone一份到本地，并会八提交历史一并拿过来。代表就是Git

> 那Git相当于svn有什么优势呢？打个比方，你费劲心思，巴拉巴拉写了一堆代码，突然发现写得有问题，想回到一个小时之前。对于这种情况Git优势就非常明显了，因为commot的成本比较小并且本地会保存所有的提交记录，随时随地可以进行回退。可这并不是说svn不能完成这种操作，只是Git的回退显得更加优雅。Git相对于中央式工具还有很多优点，此处就不一一列举了，感兴趣的可[自行探索](https://git-scm.com/doc)。

### 文件状态

> 在Git中文件大概分为三种状态：**已修改**（modified）、**已暂存**（staged）、**已提交**（committed）。

* **修改**：Git可以感知到工作目录中哪些文件被修改了，然后把修改的文件加入到**modified**区域

* **暂存**：通过**add**命令将工作目录中修改的文件提交到暂存区，等待被commit

* **提交**：将暂存区文件**commit**至Git目录中永久保存

### commit节点

> 为了便于表述，本篇会通过**节点**代称**commit提交**

在Git中每次提交都会生成一个**节点**，而每个节点都会有一个哈希值作为唯一标识，多次提交会形成一个**线性**节点链（不考虑merge的情况），如图<img title="" src="https://mmbiz.qpic.cn/mmbiz/GvtDGKK4uYnOtHiah7ia0r2pQVhbbPzR1HoWC6IhJwDq4kg1BeEpReND34oibhrefpBaQg9X81Vs85XGhQJA9XHTg/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1" alt="线性节点链" data-align="center">

> 节点上方是通过SHA1计算的哈希值

C2节点包含C1提交的内容，同样C3节点包含C1、C2提交内容

### HEAD

**HEAD**是Git中非常重要的一个概念，你可以称它为**指针**或者**引用**，它可以指向任意一个**节点**，并且指向的节点始终为当前工作目录，换句话说，当前工作区目录就是HEAD指向的节点。
以上图为例，如果HEAD指向C2，那工作目录对应的就是C2节点。具体怎么移动HEAD后面会讲到，此处不要纠结。
同时HEAD也可以指向一个**分支**，间接指向分支所指向的节点。

### 远程仓库

虽然Git会把代码以及历史保存到本地，但最终要是要提交到服务器上的远程仓库。通过**clone**命令可以把远程仓库上的代码下载到本地，同时也会将**提交历史、分支、HEAD**等状态一并同步到本地，但这些状态并不会实时更新，需要手动从远程仓库区拉取，至于何时拉，怎么拉取之后会讲到。

> 通过远程仓库为中介，你可以和别人进行协同开发，开发完新功能后可以申请提交到远程仓库，同时也可以从远程仓库同步别人的代码。

注意点

> 因为你和别人都以远程仓库的代码为基准，所以要时刻保证远程仓库的代码质量，切记不要将未经测试的代码提交至远程仓库。

## 分支

### 什么是分支

**分支**是Git中的一个重要概念，当一个分支指向一个节点时，当前节点的内容即是该分支的内容，它的概念与HEAD非常接近同样可以视为指针或者引用，不同的是分支可以存在多个，而HRAD只有一个。通常会根据功能和版本建立不同的分支。

### 分支的作用

> 举个例子：
> 你们的APP经历千辛万苦终于发布了v1.0版本，由于需求紧急 v1.0上线以后便马不停蹄地开始v1.1版本开发，正在你开发的时候，有用户反馈了一些bug，需要你修复然后重新发版，修复 v1.0肯定要基于v1.0的代码，可是你都已经开发了一部分v1.1了，此时怎么搞？

对于上面的问题，便通过分支的概念可以优雅地解决，如图：<img src="https://mmbiz.qpic.cn/mmbiz/GvtDGKK4uYnOtHiah7ia0r2pQVhbbPzR1HYHxIJKicF5K23582icibAE7feT2Unj6tyohxibUmvTyBRThicx7FufibGD4g/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1" title="" alt="-" data-align="center">

> * 先看左边示意图，假设C2节点既是v1.0版本代码，上线之后在C2节点的基础上新建了一个分支ft-1.0
> 
> * 再看右边示意图，在v1.0上线之后可在master分支开发v1.1内容，收到反馈后提交v1.1的代码生成节点C3 ，随后切换到ft-1.0分支做bug修复，修复完成后提交代码生成节点C4，最后切换到master分支并合并ft-1.0分支，到此我们就解决了问题

注意点：

> 挡在某个节点创建了一个分支后，并不会把该节点的代码复制一份出来，只是将新分支指向该节点，因此可以在很大程度上减少空间的开销，一定要牢记，不管是**HEAD**还是**分支**都只是引用而已，量级非常轻

## 命令详解

### 提交相关

之前提到过，想要对代码进行提交，必须得先加入到暂存区，，Git中通过命令**add**实现
**添加某个文件到暂存区：**

```
git add  文件路径
```

**添加所有到暂存区**

```
git add .  
```

同时，Git也提供了撤销**工作区**和**暂存区**命令

**撤销工作区改动：**

```
git checkout -- 文件名
```

**清空暂存区：**

```
git reset HEAD 文件名
```

提交：

> 将改动文件加入暂存区后就可以进行提交了，提交后会生成一个新的节点。

```
git commit -m "该节点的描述信息"
```

### 分支相关

**创建分支**

> 创建一个分支后，该分支会与HEAD指向同一节点

```
git branch 分支名
```

**切换分支**

> 当切换分支后，默认情况下，HEAD会指向当前分支，即HEAD会间接指向当前分支指向的节点

```
git checkout 分支名
```

> 同时也可以新创建一个分支后立即切换

```
git checkout -b 分支名
```

删除分支

> 为了保证仓库分支的简洁，当某个分支完成了他的使命后应该被删除。比如说单独开了一个分支完成某个功能，当这个功能被合并到主分支后应该将这个分支及时删除。

```
git branch -d  分支名
```

### 合并相关

> 关于合并的命令时最难掌握的同时也是最为重要的。我们常用的合并命令大概有三个**merge、rebase、cherry-pick**

----

**merge**

中文翻译：合并

merge 是最常用的合并命令，它可以将某个分支或者某个节点的代码合并至当前分支。

```
git merge 分支名/节点哈希值
```

> 如果需要合并的分支完全领先于当前分支，如图

<img title="" src="https://mmbiz.qpic.cn/mmbiz/GvtDGKK4uYnOtHiah7ia0r2pQVhbbPzR1Hdib7BEicU1KRGufhhfrx97VffvF5r3Ecwwu1HRWxowsCZ5h3fHD8KAdw/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1" alt="如图" data-align="center">

由于分支ft-1完全领先于分支ft-2，即ft-1完全包含于ft-2，所以ft-2执行了"git merge ft-1"后会触发**fast forward (快速合并)**，此时两个分支指向同一节点，这是最理想的状态。但是实际开发过程中我们碰到是下面这种情况：
<img src="https://mmbiz.qpic.cn/mmbiz/GvtDGKK4uYnOtHiah7ia0r2pQVhbbPzR1HDRULPAs0wtXaoDHm7N1wZhoPNk8dvHH6Pkl4FVRhfvg4243hmXAOAg/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1" title="" alt="图" data-align="center">

> 这种情况就不能直接合并了，当ft-2 执行了`git merge ft-1`后Git会将节点C3、C4合并生成一个新的节点C5，最后将ft-2指向C5

注意点：

> 如果C3、C4同时修改了同一个文件中的同一句代码，这个时候合并会出错误，因为Git不知道以哪个节点为基准，所以这个时候需要我们直接手动合并代码。

**rebase**

中文翻译：基底

rebase也是一种合并指令

```
git rebase 分支名/节点哈希值
```

与merge不同的是rebase合并看起来不会产生新的节点（实际上是会产生的，只是做了一次复制），而是将需要合并的节点直接累加
<img src="https://mmbiz.qpic.cn/mmbiz/GvtDGKK4uYnOtHiah7ia0r2pQVhbbPzR1HBhFFFc038rbAVBXB0AezcicMmic1JbrVpSXa6CdbrtrVNSHNmWaPpaMA/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1" title="" alt="图" data-align="center">

> 当左边的ft-1.0执行了git rebase master 后会将C4 节点复制一份到C3几点后面，也就是C4‘，C4 和 C4’ 相对应，但是哈希值却不一样。

rebase 相比与merge提交历史更加线性、干净，是并行的开发流程看起来更加像串行。

**merge 优缺点：**

> * 优点：每个节点都是严格按照时间排列。
>   当合并发生冲突时，只需要解决两个分支所指向的节点的冲突即可
> 
> * 缺点：合并两个分支时大概率会生成一个新的节点并分叉，久而久之会形成一团乱麻

**rebase 优缺点**

> * 优点：会使提交历史看起来更加线性、干净
> 
> * 缺点：虽然提交看起来是线性的，但不是真正的按时间排序，不管 C4 是早于还是晚于 C3 提交，它最终都会放在 C3 后面。并且当合并冲突时，理论上来将有几个节点 rebase 到目标分支，就可能处理几次冲突

**cherry-pick**

cherry-pick 的合并不同于merge和rebase，它可以选择某几个节点进行合并

```
git cherry-pick 节点哈希值
```

<img src="https://mmbiz.qpic.cn/mmbiz/GvtDGKK4uYnOtHiah7ia0r2pQVhbbPzR1HRtr8iaWAg0olJa4HQQsnGl0MT450kZFCdKOx49ZhPic1m9I9H3AFqywA/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1" title="" alt="图" data-align="center">

> 假设当前分支是master，执行了git cherry-pick C3(哈希值)、C4(哈希值) 命令会直接将 C3、C4 节点抓过来放在 C2 后面，对应 C3‘、C4’ 

### 回退相关

**分离HEAD**

> 在默认情况下HEAD是指向分支的，但也可以将HEAD从分支上取下来直接指向某个节点，此过程就是**分离HEAD**

```
/HEAD分离并指向前一个节点
git cheackout 分支名/HEAD^

/HEAD分离并指向前N个节点
git checkout 分支名 ~ N
```

将**HEAD分离**出来指向节点有什么用呢？举个例子：如果开发过程中发现之前的提交有问题，此时可以将HEAD指向对应的节点，修改完毕后再提交，此时你肯定不希望再生成一个新的节点，而你只需再提交时加上 `--amend`即可

```
git commit --amend
```

**回退**

> 回退在开发中还是比较常见的，比如你巴拉巴拉写了一堆代码然后提交，后面发现写得有问题，于是你想将代码回到前一个提交，这种场景可以通过 **reset** 解决

```
/回退N个提交
git reset HEAD-N
```

**reset** 和 **相对引用** 很像，区别是 reset 会使 **分支** 和 **HEAD** 一并回退。

### 远程相关

> 当我们接触一个新项目时，第一件事情肯定是要把它的代码复制过来，在Git中通过 **clone** 从远程仓库复制一份代码到本地

```
git clone 仓库地址
```

之前提过，**`clone`** 不仅仅是复制一份代码，它还会把远程仓库的引用（分支/HEAD）一并取下来保存在本地

<img src="https://mmbiz.qpic.cn/mmbiz/GvtDGKK4uYnOtHiah7ia0r2pQVhbbPzR1HguLxyzqLtoonrcL8NA3rn2j08J5gcxHLPycENmZkPIg1vvfSSBriaYA/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1" title="" alt="图" data-align="center">

其中 **origin/master** 和 **origin/ft-1** 为远程仓库的分支，而远程仓库的这些引用状态时不会实时更新到本地的，比如远程仓库 **origin/master** 分支增加了一次提交，此时本地是感知不到的，所以**本地的 origin/master** 分支仍指向 **C4** 节点。我们可以通过 **fetch** 命令来手动更新远程仓库的状态

小提示：

> 并不是存在于服务器上的仓库才能叫做远程仓库，你也可以 **clone** 本地仓库作为远程。当然实际开发中也不会把本地仓库当作共有仓库，这里只是为了方便你理解**<u>分布式</u>**

**fetch**

中文翻译：取来，拿来

说得通俗一点，**fetch** 命令就是一次下载操作，它会将远程新增加的节点以及**引用**（**分支/HEAD**）的状态下载到本地

```
git fetch 远程仓库地址/分支名
```

**pull**

中文翻译：拉取

**pull** 命令可以将远程仓库的某个引用拉取代码

```
git pull 远程分支名
```

> 其实 **pull** 的本质就是 **fetch** + **merge** ，首先更新远程仓库**所有状态**到本地，随后在进行合并。合并完成后本地分支指向**最新节点**
> 
> 另外，**pull** 也可以通过**rebase** 进行合并

```
git pull --rebase 远程分支名
```

**push**

中文翻译：推

**push** 命令可以将本地提交推送至远程

```
git push 远程分支名
```

> 如果直接 **push** 可能会失败，因为可能存在冲突，所以在 **push** 之前，往往会先 **pull** 一下，如果存在冲突本地解决。 **push** 成功后本地的远程分支引用会更新，与本地分支指向同一节点

**综上所述**

* 不管是 **HEAD** 还是 **分支** ，它们都只是 **引用** 而已，**引用  + 节点** 是Git构成分布式的关键

* **merge** 比 **rebase** 有更明确的时间历史，而 **rebase** 会使提交变得更加线性应当优先使用

* 通过移动 **HEAD** 可以查看每个提交对应的代码

* **clone** 或 **fetch** 都会将远程仓库的所有**提交**、**引用**保存一份在本地

* **pull** 的本质就是 **fetch + merge** ，也可以加入`--rebase`通过 **rebase** 方式合并 

## 常用命令

### 仓库

#### 在当前目录新建一个Git代码库

`$ git init`

#### 新建一个目录，将其初始化为Git代码库

`$ git init [project-name]`

#### 下载一个项目和它的整个代码历史

`$ git clone [url]`

### 配置

#### 显示当前的Git配置

`$ git config --list`

#### 编辑Git配置文件

`$ git config -e [--global]`

#### 设置提交代码时的用户信息

`$ git config [--global] user.name "[name]"`

`$ git config [--global] user.email "[email address]"`

### 增加/删除文件

#### 添加指定文件到暂存区

`$ git add [file1] [file2] ...`

#### 添加指定目录到暂存区，包括子目录

`$ git add [dir]`

#### 添加当前目录的所有文件到暂存区

`$ git add .`

#### 添加每个变化前，都会要求确认

#### 对于同一个文件的多处变化，可以实现分次提交

`$ git add -p`

#### 删除工作区文件，并且将这次删除放入暂存区

`$ git rm [file1] [file2] ...`

#### 停止追踪指定文件，但该文件会保留在工作区

`$ git rm --cached [file]`

#### 改名文件，并且将这个改名放入暂存区

`$ git mv [file-original] [file-renamed]`

### 代码提交

#### 提交暂存区到仓库区

`$ git commit -m [message]`

#### 提交暂存区的指定文件到仓库区

`$ git commit [file1] [file2] ... -m [message]`

#### 提交工作区自上次commit之后的变化，直接到仓库区

`$ git commit -a`

#### 提交时显示所有diff信息

`$ git commit -v`

#### 使用一次新的commit，替代上一次提交

#### 如果代码没有任何新变化，则用来改写上一次commit的提交信息

`$ git commit --amend -m [message]`

#### 重做上一次commit，并包括指定文件的新变化

`$ git commit --amend [file1] [file2] ...`

### 分支

#### 列出所有本地分支

`$ git branch`

#### 列出所有远程分支

`$ git branch -r`

#### 列出所有本地分支和远程分支

`$ git branch -a`

#### 新建一个分支，但依然停留在当前分支

`$ git branch [branch-name]`

#### 新建一个分支，并切换到该分支

`$ git checkout -b [branch]`

#### 新建一个分支，指向指定commit

`$ git branch [branch] [commit]`

#### 新建一个分支，与指定的远程分支建立追踪关系

`$ git branch --track [branch] [remote-branch]`

#### 切换到指定分支，并更新工作区

`$ git checkout [branch-name]`

#### 切换到上一个分支

`$ git checkout -`

#### 建立追踪关系，在现有分支与指定的远程分支之间

`$ git branch --set-upstream [branch] [remote-branch]`

#### 合并指定分支到当前分支

`$ git merge [branch]`

#### 选择一个commit，合并进当前分支

`$ git cherry-pick [commit]`

#### 删除分支

`$ git branch -d [branch-name]`

#### 删除远程分支

`$ git push origin --delete [branch-name]`

`$ git branch -dr [remote/branch]`

### 标签

#### 列出所有tag
`$ git tag`

#### 新建一个tag在当前commit

`$ git tag [tag]`

#### 新建一个tag在指定commit

`$ git tag [tag] [commit]`

#### 删除本地tag

`$ git tag -d [tag]`

#### 删除远程tag

`$ git push origin :refs/tags/[tagName]`

#### 查看tag信息

`$ git show [tag]`

#### 提交指定tag

`$ git push [remote] [tag]`

#### 提交所有tag

`$ git push [remote] --tags`

#### 新建一个分支，指向某个tag

`$ git checkout -b [branch] [tag]`

### 查看信息

#### 显示有变更的文件

`$ git status`

#### 显示当前分支的版本历史

`$ git log`

#### 显示commit历史，以及每次commit发生变更的文件

`$ git log --stat`

#### 搜索提交历史，根据关键词

`$ git log -S [keyword]`

#### 显示某个commit之后的所有变动，每个commit占据一行

`$ git log [tag] HEAD --pretty=format:%s`

#### 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件

`$ git log [tag] HEAD --grep feature`

#### 显示某个文件的版本历史，包括文件改名

`$ git log --follow [file]`

`$ git whatchanged [file]`

#### 显示指定文件相关的每一次diff

`$ git log -p [file]`

#### 显示过去5次提交

`$ git log -5 --pretty --oneline`

#### 显示所有提交过的用户，按提交次数排序

`$ git shortlog -sn`

#### 显示指定文件是什么人在什么时间修改过

`$ git blame [file]`

#### 显示暂存区和工作区的差异

`$ git diff`

#### 显示暂存区和上一个commit的差异

`$ git diff --cached [file]`

#### 显示工作区与当前分支最新commit之间的差异

`$ git diff HEAD`

#### 显示两次提交之间的差异

`$ git diff [first-branch]...[second-branch]`

#### 显示今天你写了多少行代码

`$ git diff --shortstat "@{0 day ago}"`

#### 显示某次提交的元数据和内容变化

`$ git show [commit]`

#### 显示某次提交发生变化的文件

`$ git show --name-only [commit]`

#### 显示某次提交时，某个文件的内容

`$ git show [commit]:[filename]`

#### 显示当前分支的最近几次提交

`$ git reflog`

### 远程同步

#### 下载远程仓库的所有变动

`$ git fetch [remote]`

#### 显示所有远程仓库

`$ git remote -v`

#### 显示某个远程仓库的信息

`$ git remote show [remote]`

#### 增加一个新的远程仓库，并命名

`$ git remote add [shortname] [url]`

#### 取回远程仓库的变化，并与本地分支合并

`$ git pull [remote] [branch]`

#### 上传本地指定分支到远程仓库

`$ git push [remote] [branch]`

#### 强行推送当前分支到远程仓库，即使有冲突

`$ git push [remote] --force`

#### 推送所有分支到远程仓库

`$ git push [remote] --all`

### 撤销

#### 恢复暂存区的指定文件到工作区

`$ git checkout [file]`

#### 恢复某个commit的指定文件到暂存区和工作区

`$ git checkout [commit] [file]`

#### 恢复暂存区的所有文件到工作区

`$ git checkout .`

#### 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变

`$ git reset [file]`

#### 重置暂存区与工作区，与上一次commit保持一致

`$ git reset --hard`

#### 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变

`$ git reset [commit]`

#### 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致

`$ git reset --hard [commit]`

#### 重置当前HEAD为指定commit，但保持暂存区和工作区不变

`$ git reset --keep [commit]`

#### 新建一个commit，用来撤销指定commit

#### 后者的所有变化都将被前者抵消，并且应用到当前分支

`$ git revert [commit]`

#### 暂时将未提交的变化移除，稍后再移入

`$ git stash`

`$ git stash pop`

### 其他

#### 生成一个可供发布的压缩包

`$ git archive`
