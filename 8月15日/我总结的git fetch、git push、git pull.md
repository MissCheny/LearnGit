`git fetch` 命令用于从远程仓库获取最新的数据，但不会自动合并到本地仓库。

`git fetch` + `git merge FETCH_HEAD`  =  `git pull`

`git fetch` + `git rebase FETCH_HEAD` = `git pull --rebase`

> `FETCH_HEAD` 是一个特殊的引用（reference），在 Git 中用于记录最近一次 `git fetch` 操作的结果。当你执行 `git fetch` 命令时，Git 会从远程仓库获取最新的数据，并将这些数据存储在本地仓库中。`FETCH_HEAD` 会指向最近一次获取的远程分支的最新提交。
>
> 当我从远程仓库 `origin` 的 `main` 分支获取更新，`FETCH_HEAD` 将会指向 `origin/main` 的最新提交。`git merge FETCH_HEAD` 命令实际上就是将 `FETCH_HEAD` 指向的提交合并到当前分支。
>
> 简单来说，`FETCH_HEAD` 是一个临时引用，用于保存最近一次 `git fetch` 操作后远程分支的状态，以便后续可以进行合并。
