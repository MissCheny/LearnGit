### `git reset [<mode>] <commit>`

| 模式      | HEAD<br>（分支） | 暂存区<br>（staging area） | 工作区<br>（working directory） |
|:---------:|:----------------:|:------------------------:|:----------:|
| `--soft`  | 移动         | 不变                   | 不变                        |
| `--mixed` | 移动         | 清除                   | 不变                        |
| `--hard`  | 移动         | 清除                   | 清除                        |