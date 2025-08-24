
## 🔍 `git status` 的三种状态：

### 1. **Changes not staged for commit** (未暂存的修改)
```bash
# 文件已被跟踪，有修改，但未添加到暂存区
# 此时用：git restore . 或 git add .
Changes not staged for commit:
  modified:   file1.txt
  modified:   file2.txt
```

### 2. **Changes to be committed** (已暂存待提交)
```bash
# 文件修改已添加到暂存区，等待提交
# 此时用：git restore -S . (撤销暂存)
Changes to be committed:
  modified:   file1.txt
  modified:   file2.txt
```

### 3. **Untracked files** (未跟踪文件)

<table><tr><td style='vertical-align:top; width:500px;'>

```bash
# 全新的文件，从未被 git add 过
# 此时用：git clean -f (删除文件) 或 git add . (开始跟踪)
Untracked files:
  newfile1.txt
  newfile2.txt
```

</td><td style='vertical-align:top;'>

只要有 <b>Untracked files（未跟踪文件）</b>出现，  
就绝对不能使用 `git commit -am "xxx"`，  
必须使用 `git add . && git commit -m "xxx"` 来确保所有更改都被正确暂存后提交。

</td></tr></table>

## 📝 完整工作流示例：

```bash
# 1. 修改已跟踪的文件
echo "new content" > existing_file.txt

# 查看状态：显示 "Changes not staged"
git status

# 撤销工作区修改
git restore .  # 或 git restore existing_file.txt


# 2. 添加修改到暂存区
git add existing_file.txt

# 查看状态：显示 "Changes to be committed"  
git status

# 撤销暂存（放回工作区）
git restore -S .  # 或 git restore -S existing_file.txt


# 3. 创建新文件
echo "content" > new_file.txt

# 查看状态：显示 "Untracked files"
git status

# 删除未跟踪文件
git clean -f
```

## 🎯 简单记忆：
- **工作区修改** → `git restore .` (撤销修改)
- **暂存区文件** → `git restore -S .` (撤销暂存)  
- **全新文件** → `git clean -f` (删除文件)

### 总结流程图
```
工作区修改 → git restore file.txt（撤销工作区改动）
   ↓
git add → git restore -S file.txt（撤销暂存）
   ↓
git commit → git reset HEAD~1（撤销提交）
```