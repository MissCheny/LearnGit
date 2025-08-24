## <center>`git fetch`</center>

拉取远程仓库的最新提交到本地，但不会自动合并到本地代码。

这能让你查看其他人的提交，适合需要「先观望再操作」的场景。

<table><tr><td style='vertical-align:top;'>

### 🚀 **基础用法**
```bash
# 获取所有远程分支的更新（默认远程仓库名一般为 origin）
git fetch

# 获取指定远程仓库的更新（例如 origin）
git fetch origin

# 仅获取特定分支的更新（如 main 分支）
git fetch origin main
```

</td><td style='vertical-align:top;'>

### 🔍 **查看更新内容**

```bash
# 查看远程分支 origin/main 的提交历史
git log origin/main

# 对比本地分支与远程分支的差异
git diff main origin/main

# 切换到远程分支查看代码（只读状态）
git checkout origin/main
```
同步后，你可以通过这些命令检查远程改动

</td></tr></table>

### ⚙️ **常用进阶选项**
- **强制更新本地远程分支缓存**：`git fetch --force`（覆盖本地记录的远程分支状态）
- **清理已删除的远程分支**：`git fetch --prune`（删除本地存储的过时远程分支引用）
- **一次性拉取所有远程仓库**：`git fetch --all`

---

### ⚖️ **`git fetch` vs `git pull`**
| 命令          | 行为                                                                 |
|---------------|----------------------------------------------------------------------|
| `git fetch`   | 仅下载远程数据，需手动合并（如 `git merge origin/main`）            |
| `git pull`    | `git fetch` + `git merge`（自动合并，可能直接产生冲突需要解决）     |

**✅ 使用建议**：优先用 `git fetch` 查看改动，确认无误后再手动合并，避免意外冲突。

---

### 🌰 **实际场景示例**
1. **查看同事的新功能分支**：
   ```bash
   git fetch origin
   git checkout -b feature-branch origin/feature-branch  # 基于远程分支创建本地分支
   ```

2. **合并前检查差异**：
   ```bash
   git fetch origin main
   git diff main origin/main  # 确认改动内容
   git merge origin/main      # 手动合并到当前分支
   ```

---

### 📝 **注意事项**
- 若远程分支被强制覆盖（如 `git push --force`），需要用 `git fetch --force` 更新本地记录。
- 定期运行 `git fetch --prune` 可保持本地远程分支列表的整洁。

通过 `git fetch`，你可以更安全地协作，灵活控制代码合并时机！ 🛠️