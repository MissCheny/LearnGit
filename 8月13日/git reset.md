## <center>`git reset` VS `git revert`</center>

`git reset` 可以说是改变了 commit 的引用或状态，而不是直接删除 commit。

删除 commit 可以通过其他方式，比如 `git rebase` 结合 `--interactive` 选项来实现。

- `git reset` 主要用于 **撤销提交** 或 **更改暂存区的状态**，
- `git revert` 主要用于重新应用提交到不同的基础之上，或者 **整理提交历史**。两者的目的和操作方式都不相同。

---
<table><tr><td style='vertical-align:bottom;'>

#### 初始状态
```
A -> B -> C (HEAD)
```

</td><td style='vertical-align:middle;'>
留意存区（staging area）和工作目录（working directory）的状态:

</td></tr></table>

<table><tr><td style='vertical-align:top;'>

#### `git reset --soft HEAD~1` 后
```
A -> B (HEAD) -> C
```
- 暂存区有 commit `C` 的更改。
- 工作目录有 commit `C` 的更改。

</td><td style='vertical-align:top;'>

#### `git reset --mixed HEAD~1` 后
```
A -> B (HEAD) -> C
```
- 暂存区没有 commit `C` 的更改。
- 工作目录有 commit `C` 的更改。

</td><td style='vertical-align:top;'>

#### `git reset --hard HEAD~1` 后
```
A -> B (HEAD)
C
```
- 暂存区没有 commit `C` 的更改。
- 工作目录恢复到 commit `B` 的状态。
- commit `C` 不再存在于当前分支的历史中。

</td></tr></table>


<br><br><br>

`git reset HEAD~1` 等同于 `git reset --mixed HEAD~1`

---

我用 Learn Git Branching 来学习git版本控制的，“撤销变更”这一课学习了：用 `git reset HEAD~1` 来撤销本地分支，用 `git revert HEAD` 来撤销远程分支。

然后我还补充学习了：
`git reset HEAD~1` 相当于 `git reset --mixed HEAD~1`