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





### 参考

- [廖雪峰 git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [菜鸟教程](https://www.runoob.com/git/git-tutorial.html)