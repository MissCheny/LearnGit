## <center>`git reset` 命令</center>
<table><tr><td style='vertical-align:top;'>

#### 初始状态
```
A -> B -> C (HEAD)
```

</td><td style='vertical-align:middle;'>
<br><br>
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



</td></tr><tr><td style='vertical-align:top;'>

</td><td style='vertical-align:top;'>

</td><td style='vertical-align:top;'>

执行后会新增 `.git/ORIG_HEAD` 目录，  
所以，`git reset --hard ORIG_HEAD1` 是恢复到上一次提交的状态的“后悔药”

</td></tr></table>


### `git reset --soft HEAD~1`

1. **撤销错误提交**，但保留工作目录以进一步编辑。
2. **合并多个小提交**：频繁提交，将所有小提交合并成一个大的提交。

    使用 `git reset --soft HEAD~n`（其中 `n` 是你希望撤销的提交数量）来撤销多个提交，然后使用 `git add` 将所有更改重新添加到暂存区，最后使用 `git commit` 创建一个新的、合并后的提交。

3. **重新组织更改**：如果你在提交之后意识到某些更改应该被包含在之前的某个提交中，而不是作为一个新的提交。你可以使用 `git reset --soft` 来撤销当前的提交，重新组织更改，然后创建新的提交。

需要注意的是，使用 `git reset --soft` 不会影响已经提交的历史记录和远程仓库中的任何内容，因此在团队协作时，最好先与团队成员沟通，避免其他人基于你已经推送的提交进行开发。

---

`git reset` 和 `git revert`
都是根据 `.git/log/refs` 中的日志信息来实现撤销操作的。

```
├───logs
│   │   HEAD
│   │
│   └───refs
│       └───heads
│               main
```