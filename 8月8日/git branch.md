## <center>`git branch`</center>

学习的 `git branch` ，以及什么时候用 `git branch` 什么时候用 `git switch`


### **一、git branch 的作用**

主要用于 **分支管理操作**，不会改变当前工作目录：

| 场景 | 命令 | 作用 |
|---------|--------|--------|
| 查看分支 | `git branch` | 列出所有本地分支，当前分支前有 `*` 号 |
| 创建分支 | `git branch <分支名>` | 仅创建，不切换 |
| 删除分支 | `git branch -d <分支名>` | 安全删除，会检查合并状态 |
| 强制删除 | `git branch -D <分支名>` | 强制删除未合并的分支 |
| 重命名分支 | `git branch -m <旧分支名> <新分支名>` | 重命名分支 |

---

### **二、git switch 的作用**
专门用于 **切换分支**，会更新工作目录：

| 场景 | <center>命令</center> | 说明 |
|:-----:|-----|------|
| 切换分支 | `git switch <分支名>` |  |
| 创建并切换分支 | `git switch -c <新分支名>` | 等价于 `git checkout -b` |
| 基于特定提交切换 | `git switch -c <新分支名> <commit-hash>` |  |

---

### **三、使用场景对比**

| 场景                  | 使用命令               | 示例                          |
|----------------------|-----------------------|------------------------------|
| **仅创建分支**         | `git branch`          | `git branch feature`         |
| **切换到已有分支**     | `git switch`          | `git switch main`            |
| **创建并切换分支**     | `git switch -c`       | `git switch -c hotfix`       |
| **删除分支**           | `git branch -d`       | `git branch -d old-feature`  |
| **查看所有分支**       | `git branch`          | `git branch -a` （含远程分支） |

---

### **四、为什么推荐用 `git switch` 而不是 `git checkout`？**
1. **语义更清晰**：`git switch` 明确表示切换分支，而 `git checkout` 还用于恢复文件，容易混淆。
2. **安全性更高**：`git switch` 在切换前会检查未提交的更改，避免意外覆盖。

---

### **五、最佳实践**
1. **创建分支**：`git switch -c <新分支名>` （一步完成创建+切换）
2. **临时切换分支**：`git switch <分支名>` + 后续操作
3. **清理分支**：定期用 `git branch -d` 删除已合并的分支

**示例流程：**
```bash
# 创建并切换到新分支
git switch -c feature-login

# 修改代码后提交
git add .
git commit -m "Add login feature"

# 切回主分支
git switch main

# 删除已完成的分支
git branch -d feature-login
```