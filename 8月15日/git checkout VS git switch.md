## <center>`git checkout` VS `git switch`</center>

<a href='D:\Nocturne\学习书籍\日志2025年\8月11日\回退到某一个版本.md'>回退到某一个版本</a>

### **1. 核心区别**
| **命令**          | 主要用途       | 安全性                      | 推荐场景               |
|-------------------|---------------|:-------------------------:|-----------------------|
| `git checkout`    | 切换分支<br>创建分支<br>检出历史提交或文件 | 较低<br>（可能覆盖未提交的修改） | 复杂操作    |
| `git switch`      | **仅切换分支** | 较高<br>（默认拒绝覆盖修改） | 日常分支切换 |

---

### **2. 典型使用场景**
#### **切换现有分支**
```bash
# 两者等效
git checkout main
git switch main
```

#### **创建并切换新分支**
```bash
# 两者等效
git checkout -b new-feature
git switch -c new-feature  # -c 表示 create
```

#### **检出历史提交（分离头指针）**
```bash
# 只有 checkout 支持
git checkout 9a3d8f2  # 切换到某个提交的哈希值
```

#### **恢复文件状态**
```bash
# checkout 可以恢复工作区文件（但建议改用 git restore）
git checkout HEAD -- file.txt
```

---

### **3. 安全性对比**
- **`git switch` 更安全**：  
  默认会检查工作区是否有未提交的修改，若存在则拒绝切换（除非添加 `--discard-changes` 强制丢弃修改）。
  
- **`git checkout` 更宽松**：  
  允许直接覆盖未提交的修改（可能导致代码丢失）。

---

### **4. 何时用哪个？**
- **优先用 `git switch`**：  
  日常分支切换操作（Git 2.23+ 推荐）。
- **必要时用 `git checkout`**：  
  需要检出历史提交、恢复文件，或使用旧版 Git。

---

### **5. 设计背景**
Git 在 2019 年发布的 2.23 版本中，将 `checkout` 的功能拆分：
- `git switch` → 专门处理分支切换
- `git restore` → 专门处理文件恢复

目的是解决 `checkout` 命令职责过多导致的用户困惑。

---

### **总结**
- 如果是**纯分支切换** → `git switch`（更直观安全）。
- 如果需要**恢复文件/检出历史提交** → `git checkout` 或 `git restore`。
- 团队协作时，建议统一使用新版命令（`switch` + `restore`），减少误操作风险。