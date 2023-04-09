
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


## 参考

- [Github 入门与实践](https://book.douban.com/subject/26462816/)
