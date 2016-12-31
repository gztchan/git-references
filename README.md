# Git References & Cheatsheet

## References

[常用 Git 命令清单 - 阮一峰](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html?utm_source=tool.lu)

[Ref-0](http://yanhaijing.com/git/2014/11/01/my-git-note/)

[Git 参考手册](http://gitref.org/zh/index.html)

[Git 简明指南](http://rogerdudler.github.io/git-guide/index.zh.htmlA)

[Learn Git Branching](http://learngitbranching.js.org/)

[Git Magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/zh_cn/)

[Git Book](https://git-scm.com/book/zh/v2)

[Git Flow](http://danielkummer.github.io/git-flow-cheatsheet/index.zh_CN.html)

[Pro Git](https://progit.org/)

## Common Sense

### Machanism

![machanism](https://raw.githubusercontent.com/gztchan/git-references/master/machanism.png)

### Basics

**Areas**

- Workspace
- Index / Stage
- Repository (local/remote)
- Remote

### Config

| command                                  | description        |
| ---------------------------------------- | ------------------ |
| git config —global user.name <new name>  | 修改全局 user.name     |
| git config —global user.email <new email> | 修改全局 user.email    |
| git config user.name <new name>          | 修改 repo user.name  |
| git config user.email <new email>        | 修改 repo user.email |

### Commit message

**type**

- "feat"
- "fix"
- "docs"
- "style"
- "refactor"
- "perf"
- "test"
- "chore"
- "revert"
- "deps"
- "merge"
- "release"

## Workflow

### 1. Create

| command                        | description |
| ------------------------------ | ----------- |
| git init                       | 创建 repo     |
| git clone <ur> <optional name> | 克隆 repo 到本地 |



### 2. Browse

| command                                  | description                    |
| ---------------------------------------- | ------------------------------ |
| git status                               | 当前变更文件                         |
|                                          |                                |
| git log                                  | 当前分支历史                         |
| git log —pretty=online/short             | 显示模式                           |
| git log —graph                           | 图形化显示                          |
| git log -<n>                             | 倒数第几条 log                      |
| git log —state                           | 显示 commit 历史，每次 commit 发生变更的文件 |
| git log —follow <file>                   | 显示某个文件的历史，包括文件改名               |
| git log -p <file>                        | 显示指定文件每次 diff                  |
| git log <commit-id> HEAD --pretty=format:%s | 显示某个commit之后的所有变动，每个commit占据一行 |
|                                          |                                |
| git blame <file>                         | 文件被什么人，什么时间修改过                 |
|                                          |                                |
| git diff                                 | 显示暂存区和工作区的差异                   |
| git diff —state                          | 查看简单的 diff 结果                  |
| git diff <file>                          | 查看指定文件的差异                      |
| git diff —cached <file>                  | 显示暂存区和上一个 commit 的差异           |
| git diff HEAD                            | 显示工作区与当前分支最新 commit 之间的差异      |
| git diff <branch>                        | 比较 work dir和 branch 之间的差异      |
| git diff <branch-A> <branch-B>           | 比较分支之间的差异                      |
| git diff <commit-A> <commit-B>           | 比较两次提交之间的差异                    |
| git diff —shortstatoe "{0 day age}"      | 显示今天改变了多少代码                    |
|                                          |                                |
| git reflog                               | 当前分支最近的几次提交                    |



### 3. Revert

| command                                  | description                              |
| ---------------------------------------- | ---------------------------------------- |
| git reset [commit id]                    | staged snapshot 重置，work dir 不变           |
| git reset —soft <commit-id>              | staged snapshot 和 work dir 未被改变          |
| **git reset —hard [commit id]**          | staged snapshot 和 work dir 都会退回到 commit-id 前 |
|                                          |                                          |
| git checkout <file>                      | 恢复指定文件到 work dir                         |
| git checkout .                           | 恢复 stage 所有文件到 work dir                  |
| git checkou <branch\|tag\|commit> <file> | 恢复指定 branch，tag，commit 下的文件到 work dir    |
|                                          |                                          |
| git revert HEAD                          | 撤销前一次 commit                             |
| git revert HEAD~                         | 撤销前前一次 commit                            |
| git revert HEAD~n                        | 撤销前 n 次 commit                           |
| git revert commit <commit-id>            | 撤销指定 commit                              |
| ...                                      |                                          |



### 4. Update

| command                     | description                              |
| --------------------------- | ---------------------------------------- |
| git fetch <origin> <branch> | 获取当前分支最新 commits，不合并                     |
| git pull <origin> <branch>  | 获取当前分支最新 commits，合并，并产生新的 merge commit (fetch + merge) |
| git merge <branch>          | 把 branch 与当前分支合并                         |
|                             |                                          |
| git rebase <branch>         | 变基 branch 到当前分支                          |
| git rebase —abort           | 放弃 rebase 操作                             |
| git rebase --continue       | 继续进行 rebase 操作                           |
| git rebase -i               | 交互模式                                     |
| git rebase --skip           | 跳                                        |
| git rebase <commit-id>      | rebase 当前分支，从 commit-id 以后的开始提交          |
| ...                         |                                          |



## 5. Branching/Tagging

| command                                  | description                      |
| ---------------------------------------- | -------------------------------- |
| git branch                               | 列出所有本地分支                         |
| git branch -r                            | 列出远程所有分支                         |
| git branch -a                            | 列出本地+远程所有分支                      |
| git branch <new branch>                  | 新建分支                             |
| git branch <new branch> <branch\|commit\|tag> | 指定 branch、commit、tag 拉出新的 branch |
| git branch -m <new-branch-name> <old-branch-name> | 重命名分支                            |
| git branch -d <branch>                   | 删除本地分支                           |
| git branch -dr <branch>                  | 删除本地和远程分支                        |
| git push <origin> —delete <branch>       | 删除远程分支                           |
|                                          |                                  |
| git checkout <branch>                    | 切换到分支                            |
| git checkout -                           | 切换到上一个分支                         |
| git checkout -b <branch>                 | 切换到分支，如果没有便创建                    |
|                                          |                                  |
| git tag                                  | 列出所有标签                           |
| git tag <tag>                            | 新建标签                             |
| git tag -a <tag> -m <comment>            | 新建带标注标签                          |
| git checkout <tag>                       | 切换到标签                            |
| git push <origin> <tag>                  | 推送标签到仓库                          |
| git push <origin> —tags                  | 推送所有标签到仓库                        |
| git tag -d <tag>                         | 删除本地分支                           |
| git push <origin> :refs/tags/<tag>       | 删除远程分支                           |
| ...                                      |                                  |



## 6. Commit

| command                               | description                        |
| ------------------------------------- | ---------------------------------- |
| git commit                            | 提交更新                               |
| git commit -m [message]               | 备注                                 |
| git commit —amend                     | 修改 HEAD 的 commit 信息，产生新的 commit-id |
| git commit <file>…<file> -m <message> | 提交 stage 区置顶文件到 repo               |
| ...                                   |                                    |



### 7. Push

| commands                           | description                       |
| ---------------------------------- | --------------------------------- |
| git push <remote> <branch>         | 推送 <branch> 到代码仓库                 |
| **git push <remote> -f**           | —force 强制推送当前分支到远程仓库，忽略 conflicts |
| git push <remote> —all             | 推送所有分支                            |
| git push <origin> :<branch>        | 删除远程特定分支                          |
| git push <origin> <branch> —delete | 删除远程特定分支                          |
| ...                                |                                   |



## Others

## Stash

| commands                   | description             |
| -------------------------- | ----------------------- |
| git stash                  | 保存 staged snapshot 状态   |
| git stash list             | 列出所有保存的 staged snapshot |
| git stash apply <stash-id> | 启用某个 stash              |
| git stash drop <stash-id>  | 删除某个 stash              |
| ...                        |                         |



### Remote

| command                                 | description    |
| --------------------------------------- | -------------- |
| git remote add <name> <url>             | 添加源            |
| git remote                              | 显示全部源          |
| git remote -v                           | 显示全部源 + 全部信息   |
| git remote rename <old name> <new name> | 重命名            |
| git remote rm <name>                    | 删除指定 name      |
| git remote show <name>                  | 查看指定 name 所有信息 |
| ...                                     |                |



## Add/Remove

| command                     | description                             |
| --------------------------- | --------------------------------------- |
| git add .                   | 添加所有文件到 staged snapshot                 |
| git add <files>             | 添加某些文件到 staged snapshot                 |
| git add <dir>               | 添加某目录和其子目录到 staged snapsshot            |
|                             |                                         |
| git rm <files>              | 删除 work dir 下文件，把这次删除放入 staged snapshot |
| git rm —cached <file>       | 停止追踪，保留文件在 work dir                     |
| git mv <original> <renamed> | 改变命名，并放到 staged snapshot                |
| ...                         |                                         |