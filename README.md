## 配置与帮助
``` c
# 查看 Git 配置信息
$ git config -l

# 修改 Git 配置文件
$ git config -e

# 修改提交时的用户信息
$ git config user.name "[name]"
$ git config user.email "[email]"

# 查看所有指令
$ git help

# 查看某条指令，例如 config
$ git config --help
```

## 版本库创建
``` c
# 在当前文件夹初始化一个空的版本库，若已存在版本库则将其重新初始化
$ git init

# 新建一个目录并初始化一个空的版本库
$ git init [repo-name]

# 通过 ssh 从远程仓库克隆
$ git clone git@github.com:Coder-ZJQ/Test-Git.git

# 通过 https 从远程仓库克隆
$ git clone https://github.com/Coder-ZJQ/Test-Git.git

```

## 文件操作
``` c
# 新建一个文件
$ touch [file-name]

# 新建一个文件夹
$ mkdir [dir-name]

# 查看一个文件
$ cat [file-name]

# 编辑一个文件，编辑完成输入 ":wq" 保存退出
$ vi [file-name]

# 将工作区中已修改的文件，添加到暂存区（可多个文件）
$ git add [file1] [file2] ...

# 将文件夹下已修改的文件添加到暂存区（可多个文件夹）
$ git add [dir1] [dir2] ...

# 将当前目录下的所有已修改文件添加至暂存区
$ git add ./

# 删除工作区的文件，并将此次操作放入暂存区
$ git rm [file1] [file2] ...

# 删除文件夹下的所有文件，并将此次操作放入暂存区（并不会删除文件夹）
$ git rm -r [dir]

# 为文件改名，并将此次操作放入暂存区
$ git mv [file-original] [file-renamed]

```

## 修改管理
``` c
# 查看当前状态
$ git status

# 将暂存区的修改提交至当前分支
$ git commit -m "[message]"

# 将暂存区中的指定文件或文件夹添加到当前分支
$ git commit [file] | [dir] ... -m "[message]"

# 将修改或删除的文件直接提交至当前分支，跳过 add 步骤（新建文件还需先 add ）
$ git commit -a -m "[message]"

# 提交一次新的 commit，重写 message
$ git commit --amend -m "[message]"

# 恢复修改至最近的一次 commit 或者 add，即放弃工作区中的修改
$ git checkout [file] | [dir] ...

# 若是已经将工作区的修改 add 至暂存区，可以先 reset 然后再 checkout
$ git reset HEAD [file] | [dir] ...

# 若是已经 add 并且 commit，可以版本回退，撤销修改
$ git reset --hard [commit-id]

# 保存当前工作区至工作栈
$ git stash

# 恢复工作栈栈顶的工作区，但并不会删除
$ git stash apply

# 删除工作栈栈顶的工作区
$ git stash drop

# 将工作栈栈顶的工作区出栈：恢复工作区并删除
$ git stash pop

# 查看工作栈中保存的工作区
$ git stash list
```

## 分支管理
``` c
# 查看本地分支
$ git branch

# 查看远程分支
$ git branch -r

# 查看所有分支
$ git branch -a

# 创建一个新的分支
$ git branch [branch-name]

# 在指定 commit 创建一个分支
$ git branch [branch-name] [commit-id]

# 在指定 tag 创建一个分支
$ git branch [branch-name] [tag-name]

# 新建一个分支，并追踪一个远程分支
$ git branch --track [branch-name] [remote-branch-name]

# 在现有分支与指定的远程分支之间建立追踪关系
$ git branch --set-upstream [branch-name] [remote-branch-name]
$ git branch -f --track test [branch-name] [remote-branch-name]

# 切换分支
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 创建一个新的分支，并跳转至该分支
$ git checkout -b [branch-name]

# 合并某分支至当前分支，默认是 Fast-forward 模式
$ git merge [branch-name]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote-branch]

```

## 远程仓库操作
``` c
# 创建 SSH Key
$ ssh-keygen -t rsa -C "youremail@example.com"

# 本地关联远程版本库，并设置简称
$ git remote add [remote-name] [remote-SSG | remote-URL]

# 将远程版本库代码更新至本地，但并不会执行合并操作
$ git fetch [remote-name]

# 从远程版本库获取代码，并与本地分支合并
$ git pull [remote-name] [branch-name]

# 上传本地指定分支到远程仓库
$ git push [remote-name] [branch-name]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote-name] --force

# 推送所有分支到远程仓库
$ git push [remote-name] --all

# 显示所有远程版本库
$ git remote -v

# 显示某个远程版本库信息
$ git remote show [remote-name]
```

## 标签管理
``` c
# 列出所有 tag 
$ git tag

# 查看 tag 信息
$ git show [tag-name]

# 在当前 commit 新建一个 tag
$ git tag [tag-name]

# 在指定 commit 上新建一个 tag
$ git tag [tag-name] [commit-id]

# 创建一个 tag 并指定标签信息
$ git tag -a [tag-name] -m "[message]" [commit-id]

# 删除标签
$ git tag -d [tag-name]

# 推送本地标签至远程版本库
$ git push [remote-name] [tag-name]

# 推送所有尚未推送的本地标签至远程版本库
$ git push [remote-name] --tags

# 删除远程版本库中的标签，先删除本地，再推送删除远程
$ git tag -d [tag-name]
$ git push [remote-name] :refs/tags/[tag-name]

```

## 信息查看
``` c
# 显示有变更的文件
$ git status

# 显示当前分支的版本历史
$ git log

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

# 搜索提交历史，根据关键词
$ git log -S [keyword]

# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s

# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature

# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]

# 显示指定文件相关的每一次diff
$ git log -p [file]

# 显示过去5次提交
$ git log -5 --pretty --oneline

# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn

# 显示指定文件是什么人在什么时间修改过
$ git blame [file]

# 显示暂存区和工作区的差异
$ git diff

# 显示暂存区和上一个commit的差异
$ git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"

# 显示某次提交的元数据和内容变化
$ git show [commit]

# 显示某次提交发生变化的文件
$ git show --name-only [commit]

# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

# 显示当前分支的最近几次提交
$ git reflog
```

## 其他
``` c
# 生成一个可供发布的压缩包
$ git archive
```
---
 参考资料：   
[廖雪峰的官方网站 - Git 教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)   
[阮一峰 - 常用 Git 清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html?utm_source=tool.lu)   
[git-scm](https://git-scm.com/docs)