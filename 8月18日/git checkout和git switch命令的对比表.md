`git checkout`和`git switch`命令的对比表：

| 功能描述         |                |                |
|:----------------:|----------------------------------|----------------------------------|
| 切换到分支       | `git checkout {branch-name}`       | `git switch {branch-name}`       |
| 创建并切换到新分支 | `git checkout -b {branch-name}`    | `git switch -c {branch-name}`    |
| 切换到上一个分支   | `git checkout -`                   | `git switch -`                   |
| 强制切换到分支   | `git checkout -f {branch-name}`    | `git switch -f {branch-name}`    |
| 切换到某个提交     | `git checkout {commit-hash}`       | `git switch {commit-hash}`<br> (不推荐，使用 `git checkout` 更为合适) |
| 切换到某个标签     | `git checkout {tag-name}`          | `git switch {tag-name}`<br> (不推荐，使用 `git checkout` 更为合适) |

需要注意的是，`git switch` 主要用于切换分支，并不适用于切换到某个提交或标签的操作。在这些情况下，`git checkout` 仍然是更合适的选择。