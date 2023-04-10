
## 1 什么是 Github

Github 是为开发者提供 Git 仓库的托管服务。吉祥物是 octocat。

### 1.1 Github 提供的主要功能

**1. Git 仓库**

可以免费建立任意个 Github 提供的 Git 仓库。

**2. Organization**

免费创建组织账户，小团体合作开发。

**3. issue**

将一个任务或问题分配给一个 issue 进行追踪和管理。每一个功能或修正都对应一个
issue，讨论或修正都以这个 issue 为中心进行。

**4. Wiki**

任何人都能随时对一篇文章进行更改和保存，常用于开发文档或手册的编写。

**5. pull request**

开发者向 Github 的仓库推送更改或功能添加后，可以通过 Pull Request 功能向别人的
仓库提交申请，请求对方合并。

## 2 Git

### 2.1 版本管理

版本管理就是管理更新的历史记录。

Git 是分散型的版本控制工具。

### 2.2 Git 初始设置

```shell
git config --global user.name "shachi"
git config --global user.email "shachi1758@outlook.com"
```

内容会保存到 `~/.gitconfig` 中，会用于 Git 的提交日志中。

```shell
git config --global color.ui auto
```

让命令的输出拥有更高的可读性。

## 3 使用 Github 前的准备

### 3.1 创建账号

创建账号后，公开页面的 URL 即为：`http://github.com/username`。

### 3.2 创建头像

### 3.3 设置 SSH Key

```shell
ssh-keygen -t rsa -C "shachi1758@outlook.com"
```

创建成功后会在 `~/.ssh` 目录下生成 `id_rsa`私有密钥，`id_rsa.pub` 公钥。

### 3.4 添加公开密钥

为 github 账号添加公钥。

添加成功后，使用 `ssh -T git@github.com` 验证。

### 3.5 创建公开仓库

**1. 仓库名**

**2. 仓库描述**

**3. 公开/私有仓库**

**4. 初始化 README**

**5. 添加 .gitignore**

**6. 添加许可协议**

一般选择 MIT 协议。实际使用时，只需将 LICENSE 文件加入仓库，在 README.md 中声明
即可。

MIT 许可协议一般具有如下特征：

被授权人权利：被授权人有权利使用、复制、修改、合并、出版发行、散布、再授权和/或
贩售软件及软件的副本，及授予被供应人同等权利，唯服从以下义务。被授权人义务：在
软件和软件的所有副本中都必须包含以上版权声明和本许可声明。其他重要特性：此许可
协议并非属copyleft的自由软件许可协议条款，允许在自由及开放源代码软件或非自由软
件（proprietary software）所使用。MIT的内容可依照程序著作权者的需求更改内容。
此亦为MIT与BSD（The BSD license, 3-clause BSD license）本质上不同处。MIT许可
协议可与其他许可协议并存。另外，MIT条款也是自由软件基金会（FSF）所认可的自由软
件许可协议条款，与GPL兼容。

### 3.6 公开代码

**1. 克隆仓库**

将代码库 clone 到本地。

`git clone git@github.com:username/repo-name.git`

**2. 编写代码**

如编写一个 `hello_world.cc` 文件：

```cc
#include <iostream>
#include <cstdlib>


int main(int argc, const char* argv[])
{
    std:cout<< "Hello,World"<<std::endl;

    return EXIT_SUCCESS;
}
```

使用命令：

`git status` 查看仓库状态。

**3. 提交文件**

`git add hello_world.cc`，这样，这文件就进入了暂存区，可以由版本管理系统管理了。

`git cmmmit -m "提交信息"` 将暂存区的文件提交到版本库。

`git log` 查看提交日志。

**4. push**

将本地版本库推送到远程。

`git push origin main`

## 4. 实际操作学 git

### 4.1 基本操作

**1. 初始化仓库**

`git init` 初始化成功，目录下就会生成 `.git` 目录，这个目录里存储着管理当前目录
所需的数据。这个目录的内容被称作工作树。

**2. 查看仓库状态**

`git status` 用于显示仓库的状态。只要对 git 的工作树或者仓库进行操作，`git sta
tus` 的显示结果就会发生变化。

**3. 向暂存区添加文件**

只是在工作树创建了文件，该文件并不会被记入版本管理对象中。

暂存区（stage 或 index）是提交前的一个临时区域。

`git add <文件名>`

**4. 保存仓库的历史记录**

`git commit -m "提交信息"`

将暂存区的文件提交到本地版本库。

不加 `-m` 选项，则执行后编辑器会启动，可以记述详细的提交信息。

格式如下：第一行：用一行文件简述提交内容。第二行：空行。第三行及以后：详细内容。

不写提交信息则会终止提交。

提交完成后，查看状态，结果会显示工作树是干净的。

**5. 查看提交日志**

```shell
$ git log

commit 9f129bae19b2c82fb4e98cde5890e52a6c546922
Author: hirocaster <hohtsuka@gmail.com>
Date:   Sun May 5 16:06:492013 +0900

    First commit
```

`9f129b` 是指向这个提交的哈希值。最后一行是提交信息。

`git log --pretty=short` 只显示第一行简述信息。

`git log 文件名` 只显示指定目录、文件的日志。

`git log -p 文件名` 查看提交所带来的改动。

**6. 查看更改前后的差别**

`git diff` 查看工作树、暂存区、版本库之间的差别。

`git status` 显示上次提交更新后的更改或者写入缓存的改动，而 git diff 一行一行
地具体显示这些改动。

如在 README.md 中写入 `# git 教程`。

执行 `git diff` ，查看工作树和暂存区的差别：

```shell
$ git diff

diff --git a/README.md b/README.md
index e69de29..cb5dc9f 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1 @@
+# git教程
```

现在 `git add README.md` 将文件加入暂存区。

查看已缓存和未缓存的所有差别：

```shell
$ git diff HEAD
diff --git a/README.md b/README.md
index e69de29..cb5dc9f 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1 @@
+# Git教程
```

### 4.2 分支的操作

master 是 git 默认创建的分支，基本所有开发都是以这个分支为中心。

**1. 显示分支**

`git branch` 显示当前分支，分支名左侧标有`*`的是当前所在分支。

**2. 创建、切换分支**

`git checkout -b 分支名` 创建并切换到新分支。

相当于连续执行：`git branch 分支名`，`git checkout 分支名`。

创建多个分支，就可以在不互相影响的情况下同时进行多个功能的开发。

**3 合并分支**

`git merge --no-ff 分支名` 合并分支，并且记录下本次分支合并。

编辑器启动，默认信息包含合并操作。

`git merge --no-ff 分支名 -m "提交信息"`

**4 以图标形式查看分支**

`git log --graph` 以图标形式输出提交日志。

### 4.3 更改提交的操作

**1. 回溯历史版本**

`git reset --hard 哈希值` 工作树、暂存区、版本库 HEAD 回溯到指定时间点。

`git log` 只能查看以当前状态为终点的历史日志。

`git reflog` 可以查看当前仓库的操作日志。

**2. 消除冲突**

冲突解决后，执行 `git add` 和 `git commit` 命令。

**3. 修改提交信息**

`git commit --amend`

**4. 压缩历史**

`git rebase -i` 将多个提交合并成一个。

### 4.4 推送到远程仓库

**1. 创建仓库**

创建仓库时建议仓库名与本地仓库保持一致，并不要初始化 README。

**2. 添加远程仓库**

`git remote add 仓库别名 git@github.com:user-name/repo-name.git` 添加远程仓库。

`git remote add origin git@github.com:github-book/git-tutorial.git` 将远程仓库
的名称设置为 origin。

**3. 推送至远程仓库**

推送 main 分支：`git push -u origin main`。

`-u` 参数可以在推送到同时，将 orgin 的 main 分支设置为本地仓库当前分支 upstream
。以后使用 `git push`，`git pull` 可直接才 origin 的 main 分支获取内容。

推送 dev 分支：

```shell
git checkout dev
git push origin dev
```

### 4.5 从远程仓库获取

**1. 获取远程仓库**

`git clone git@github.com:username/repo-name.git [pathname]`

默认处于 main 分支，同时系统会自动将 origin 设置成该远程仓库的标识符。

`git branch -a` 查看本地仓库和远程仓库的分支信息。

**2. 获取远程仓库的分支**

`git checkout -b dev origin/dev` 新建分支并从远程仓库拉取。

**3. 获取最新的远程仓库分支**

`git pull origin dev`

## 5 详细解说 Github 功能

### 5.1 键盘快捷键

`shift + /` 打开键盘快捷键。

### 5.2 工具栏

![](./res/tool-bar.png)

**1. logo**

点击 logo 刷新页面。

**2. 搜索栏**

**3. Pulls**

查看自己的 pull request。

**4. Issues**

查看自己的 issues。

**5. Codespaces**

线上的编程环境，可以编写或者运行 Github 仓库中的代码。

相当于一个线上编辑器。

**6. Marketplace**

Github 的开放平台或者扩展平台。

提供两类扩展：apps 和 actions。

**7.Explore**

推送 Github 上的热门开源仓库。

**8. 铃铛 logo**

提示用户是否用新的通知。收到通知的同时会发送到用户的注册邮箱。

**9. +**

共有六个功能：

1. New repository 创建新的仓库。
2. import repository 导入仓库。
3. New codespace 在线上编辑器创建新项目。
4. New gist 创建新的 gist 库，gist ：github 保存文本片段的服务，可以用来记笔记、保存配置、记笔记、记录想法。
5. New organization 创建组织，合作编程。
6. New Project 创建新的项目，可以帮助组织工作，创建看板，定制工作流。

**10 .头像**

修改个人设置、账号设置。

- Your Profile

### 5.3 Your Profile

**1. Overview**

总览

**2. Repositories**

用户的所有仓库

**3. Projects**

用户创建的项目。

**4. Stars**

用户 star 过的仓库。

**5. Packages**

是一个包承载服务，完全和 Github 集成。可以将自己的package 打包上传。

如 docker 包、maven 包、NuGet 包、npm 包、Container 等。

### 5.4 issue

issue 的功能：

1. 发现软件的 BUG 并报告。
2. 有事想向作者询问、探讨。
3. 事先列出今后准备实施的任务。

**issue 可以添加标签便于管理**

**issue 可以添加里程碑以便管理任务。**

**通过 commit 操作 issue**

提交信息中包含 `#issue_num` 即可在 issue 下添加新的记录。

提交信息中包含：

```
fix #24
fixed #24
fixes #24
close #24
resolve #24
```

等即可关闭 issue。

issue 和 pull request 的编号通用。

### 5.5 Pull Request

**获取 Pull Request 的 diff/patch 格式文件**

在 URL 末尾添加 diff/patch 即可。

`https://github.com/username/reponame/pull/28.diff/patch`

可以在代码中插入评论。

### 5.6 Wiki

Wiki 可以编写文档，支持 GFW 语法，可以通过 git 进行管理。
克隆到本地然后创建、编辑、提交，push。

一般情况下，wiki 中记载着软件相关 FAQ、文档、代码示例和解说等信息。

所有的 wiki 页面都可以显示侧边栏。只要创建名为 `_sidebar` 的页面即可。

### 5.7 Settings

修改仓库名称、设置显示仓库 URL 时默认显示分支等。

可以更改 features 和 issue 等。

可以创建 github pages。

**Collaborators**

用户可以设置仓库的访问权限，赋予其他用户读写仓库的权限。

在公司等多人共同开发的组织中，建议使用组织账户。

**Deploy Keys**

添加用于部署的公钥，允许只读访问，每个仓库要赋予不同的密钥对。

### 5.8 其他功能

**Github Pages**

托管静态 HTML，可以绑定域名。

**Github Jobs**

**Github Enterprise**

**Github API**

## 6 Pull Request

### 6.1 Pull Request 的概要

Pull Request 是自己修改源代码后，请求对方仓库采纳该修改时采取的一种行为。

流程：

fork -> clone -> 创建特性 branch -> 修改 -> 提交 -> 创建远程分支

不 fork 发起 Pull Request：

如果用户对该仓库有编辑权限，可以直接创建分支，从分支发送 Pull Request 到主分支。

### 6.2 仓库的维护

通常来说 clone 的仓库与原仓库没有关系。我们需要将原仓库设为远程仓库，从该仓库获取数据后
与本地仓库进行合并。

将 `octocat/Spoon-Knife` 作为原仓库，fork 然后 clone。

给原仓库设置名称，给原仓库设置 upstream 名称，将其作为远程仓库。

`git remote add upstream git://github.com/octocat/Spoon-Knife.git`

即可以使用命令：

`git fetch upstream` 获取最新源代码。

这样，upstream/main 分支与当前 main 分支就可以合并了。

`git merge`


## 7 接收 Pull Request

1. 代码审查
2. 对比差异
3. 本地获取发送方的远程仓库
4. 创建用于检查的分支
5. 合并分支。（git merge PRsender/work)，将 work 分支的内容合并到测试分支。
6. 删除分支。(git branch -D check)
7. 合并到主分支。
8. git push。

## 8 与 Github 相互协作的工具和服务

1. hub 命令
2. Travis Ci
3. Coveralls
4. Gemnasium
5. Code Climate
6. Jenkins

## 9 使用 Github 的开发流程

### 9.1 Github Flow 以部署为中心的开发模式

1. 令 main 分支时常褒词可以部署的状态。
2. 进行新的作业要从 main 分支创建新分支，新分支名称要具有描述性。
3. 在 2 新建的本地仓库分支中进行提交。
4. 在 github 端仓库创建同名分支，定期 push。
5. 需要帮助或反馈时创建 Pull Request，以 Pull Request 进行交流。
6. 代码审查，确认作业完成后与 main 分支合并。
7. 与 main 分支合并后立刻部署。

## 参考

- [Github 入门与实践](https://book.douban.com/subject/26462816/)
