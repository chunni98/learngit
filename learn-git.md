## git 学习记录

`git init` 初始化版本库。

`git add 文件名` 把文件添加到暂存区。

`git commit -m "提交消息"` 把文件提交到 `HEAD`。

`git commit` 提交并打开编辑器编写 commit message。

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

`git reset HEAD 文件名` 把暂存区的修改撤销掉，回滚。

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

`git push origin -d 分支名` 删除远程分支。

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

删除一个未合并的分支，使用：

`git branch -D feature` 强制删除 `feature` 参数。

推送分支：`git push origin dev`

main 分支是主分支，因此要时刻与远程同步。

dev 分支是开发分支，团队所有成员在上面工作，也需要与远程同步。

hotfix 分支只用于在本地修复 bug，命名：`hotfix-*`。

feature 分支是否推到远程，取决与是否需要合作。命名约定：`feature-*`。

抓取分支

`git clone git@github.com:xxx/xxx.git` 只会抓取 main 分支。

`git checkout -b dev origin/dev` 抓取远程 dev 分支。

多人协作的工作模式：

1. `git push origin <分支>`,远程仓库同步到本地版本库，不会影响工作区。
2. 推送失败，则合并,`git fetch origin`，`git merge`。
3. 合并有冲突，则解决冲突，在本地提交。
4. 解决冲突后 `git push origin <分支>`
5. 如果本地分支和远程分支的链接关系没有建立，则 `git branch --set-upstream-to <分支> origin/<分支>`

变基：`git rebase` 合并 commit 成直线。

创建标签：`git lag v1.0` 在当前分支打标签。

`git tag` 查看所有标签。

`git tag v0.9 f52c633` 对某次 commit 打标签。

`git tag -a v0.1 -m "xxx" 1094adb` 创建带说明的标签。

`git show <tagname>` 查看标签说明。

`git tag -d v0.1` 删除标签。

创建的标签都只存储在本地，不会自动推送到远程。

`git push origin <tagname>` 推送某个标签到远程。

`git push origin --tags` 推送所有本地标签。

从远程删除标签:

1. 从本地删除。

`git tag -d v0.9`

2. 从远程删除。

`git push origin :refs/tags/v0.9`

让 git 显示不同颜色：`git config --global color.ui true`

在Git工作区的根目录下创建一个特殊的.gitignore文件，
然后把要忽略的文件名填进去，Git就会自动忽略这些文件。

`git check-ignore -v 文件名`

检查哪个规则忽略了文件。

指定文件排除在 `.gitignore` 外：

`!main.o`


`c.gitignore` 文件示例：

```
.*
!.gitignore
# Prerequisites
*.d

# Object files
*.o
*.ko
*.obj
*.elf

# Linker output
*.ilk
*.map
*.exp

# Precompiled Headers
*.gch
*.pch

# Libraries
*.lib
*.a
*.la
*.lo

# Shared objects (inc. Windows DLLs)
*.dll
*.so
*.so.*
*.dylib

# Executables
*.exe
*.out
*.app
*.i*86
*.x86_64
*.hex

# Debug files
*.dSYM/
*.su
*.idb
*.pdb

# Kernel Module Compile Results
*.mod*
*.cmd
.tmp_versions/
modules.order
Module.symvers
Mkfile.old
dkms.conf

**/bin/*
*.*~
obj/
```

搭建 git 服务器：

1. 安装 git。
2. 创建 git 用户，运行 git 服务。
3. 创建证书登录。
4. 初始化 git 仓库。
5. 禁用 shell 登录。
6. 克隆远程库。

```shell
sudo apt-get install git
sudo adduser git
# 把所有要登陆的用户的公钥，即 id_rsa.pub 文件，导入到
# /home/git/.ssh/authorized_keys 文件里，一行一个。
# 选定一个目录作为 git 仓库，如 /srv/sample.git
# 在 /srv 目录下执行命令：
# 创建裸仓库，没有工作区
sudo git init --bare sample.git
# 服务器上的 git 仓库通常以 .git 结尾，把 owner 改为 git
sudo chown -R git:git sample.git
# 编辑 /etc/passwd 禁用 shell 登录
git:x:1001:1001:,,,:/home/git:/bin/bash
# 改为：
git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell
# git-shell 每次一登陆就自动退出。

# 克隆远程仓库：

git clone git@server:/srv/sample.git
```

**配置**

配置保存在 `~/.gitconfig` 文件中。

`git config -global core.editor vim` 修改默认编辑器。

`git config --list` 查看所有配置。

`git config --global user.name 名字` 设置账号名。

`git config --global user.email 邮箱` 设置邮箱。

`git config color.ui auto` 设置彩色输出。

### 参考

- [廖雪峰 git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [菜鸟教程](https://www.runoob.com/git/git-tutorial.html)
