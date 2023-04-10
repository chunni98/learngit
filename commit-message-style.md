# commit message 规范

## 格式

`<type>(<scope>): <subject> 空一行 <boey> 空一行 <footer>`

**Header**

type（必须）：

用于说明 commit 的类别。

- feat：一个新功能。
- fix：修复 bug。
- docs：修改文档。
- style：修改格式（不影响代码运行）。
- refactor： 重构。
- test：测试。
- chore：非 src 路径文件和测试文件的修改，如 `.gitignore`，`.editconfig` 等。
- revert: 代码回退

type 为 feat 或 fix 则该 commit 肯定出现在 change log 中。

scope：用于说明 commit 影响的范围。

subject 是 commit 的简短描述。建议以动词开头。不加句号。

**Body**

Body 部分是对本次 commit 的详细描述。

**Footer**

只用于两种情况：

1. 不兼容变动，以 `BREAKING CHANGE:` 开头，后面是对变动的描述以及变动理由和迁移方法。
2. 处理 issue。

处理 issue格式：

本次提交与某个 issue 有关系：

`Issue #1,#2,#3`

当前提交信息解决了某个 issue：

`Close #1,#2,#3`

## Issue

Github 的 issue 功能是一个轻量级的协作系统。

issue 可以有额外的属性：

- labels，标签，表示 issue 的类型，解决的方式。
- Milestone，里程碑。作为 issue 的一个集合，如 demo，release 等。通常用来表示项目的一个阶段。
- Assignee，负责人。这个 issue 由谁负责。

## 参考

- [Git Commit Message 应该怎么写？](https://www.cnblogs.com/alwaysbeta/p/17280127.html)
- [Git Commit message 编写指南](https://gitee.com/help/articles/4231#article-header0)

