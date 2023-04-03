## git 学习记录

`git init` 初始化版本库。

`git add 文件名` 把文件添加到暂存区。

`git commit -m "提交消息"` 把文件提交到 `HEAD`。

`git status` 显示工作树状态。

`git diff` 查看尚未缓存的改动 。

`git diff --cached` 查看已缓存的改动。

`git diff HEAD` 查看已缓存的和未缓存的所有改动。

`git rm [-r] --cached 文件名` 从暂存区删除文件（夹），不会删除本地文件。

`git rm --cached .` 清空暂存区。

`git log --oneline --graph --decorate --all` 查看提交日志。

`HEAD` 表示当前版本，即最新的提交。`HEAD^` 上一个提交。`HEAD^100`，往上 100 个版本。

`git reset --hard HEAD^` 退回到上一个版本。

`git reset --hard 1094a` 退回到指定版本。

回退版本时仅仅是更改 HEAD 指向，然后更新工作区。

`git reflog` 查看历史命令。

工作区、暂存区、版本库。`git add` 把所有要提交的修改放到暂存区。`git commit` 把所有暂存区的修改提交到版本库。

`git checkout -- 文件名` 丢弃工作区的修改。

`git reset HEAD 文件名` 把暂存区的修改撤销掉。






### 参考

- [廖雪峰 git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [菜鸟教程](https://www.runoob.com/git/git-tutorial.html)
