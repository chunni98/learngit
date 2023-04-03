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

`git rm` 从本地中删除文件。

`git checkout -- 文件名` 用版本库的文件还原工作区的版本。从来没有添加到版本库的文件，是无法恢复的。

`ssh-keygen -t rsa -C "youremail@example.com"` 创建 SSH Key。

`git remote add origin git@github.com:xxxxxx/xxx.git` 添加远程库。

远程库名字就是 origin。

`git push origin master` 把当前分支 `master` 推送到 origin。

`git remote -v` 查看远程库信息。

`git remote rm 库名` 删除库。

`git clone git@github.com:xxx/xxx.git` 克隆一个本地库。

主分支，`master` 分支。

`git checkout -b dev` 创建并切换到 dev 分支。

相当于：

```shell
git branch dev
git checkout dev
```
切换到分支 `dev` 然后提交修改后，切换分支将无法看到修改。

`git merge 分支名` 合并分支。（默认Fast forward）。

`git merge --no-ff -m "提交信息" 分支名` 不使用 Fast forward。

`git branch -d 分支名` 删除分支。

git 鼓励使用分支完成某个任务，合并后删除分支。

合并分支后可能存在冲突，修改冲突后重新提交合并即完成。

git 使用 Fast forward 模式删除分支后会丢掉分支信息。

**分支策略**

main 分支应该是稳定的，用来发布新版本，平时不在上面干活。

dev 分支用来开发。需要发布版本时，再把 dev 分支合并到 main 分支。

每个开发者都有自己的分支，基于 dev 分支开发。

`git stash` 将未提交的修改（工作区的修改和暂存区的修改）暂时储藏起来。

`git stash pop` 将之前储藏的修改取出来。

`git cherry-pick 4c805e2` 复制一个特定的提交到当前分支。

修复 bug 时，会创建新的 bug 分支进行修复，然后合并，删除。

如果有工作未完成，可以保护现场，然后修复 bug，修复后，`git stash pop` 回到工作
现场。在其他分支修复的 bug，想要合并到 dev 分支，可通过
`git cherry-pick <commit>` 命令复制，避免重复劳动。

添加一个新功能，最好新建一个 feature 分支，完成后合并，最后删除分支。

删除一个未合并的线程，使用：

`git branch -D feature` 强制删除 `feature` 参数。


### 参考

- [廖雪峰 git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [菜鸟教程](https://www.runoob.com/git/git-tutorial.html)
