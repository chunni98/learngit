
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

## 参考

- [Github 入门与实践](https://book.douban.com/subject/26462816/)
