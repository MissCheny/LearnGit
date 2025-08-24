## 等效性说明

1. **默认模式**：`git reset` 命令在不指定模式时，默认使用 `--mixed` 模式
2. **默认引用**：当不指定提交引用时，默认使用 `HEAD`
3. 因此，以下命令都是等效的：
   ```bash
   git reset
   git reset HEAD
   git reset --mixed
   git reset --mixed HEAD
   ```

## 三种 reset 模式的区别

为了更好地理解，这里对比一下 Git reset 的三种主要模式：

| 模式 | 作用对象 | 工作目录 | 暂存区 | HEAD |
|------|----------|----------|--------|------|
| `--soft` | 只移动 HEAD | 不变 | 不变 | 改变 |
| `--mixed` (默认) | 移动 HEAD 和暂存区 | 不变 | 重置 | 改变 |
| `--hard` | 移动 HEAD、暂存区和工作目录 | 重置 | 重置 | 改变 |

## 实际应用示例

```bash
# 撤销所有已暂存的更改（回到工作目录）
git reset HEAD

# 撤销特定文件的暂存
git reset HEAD file.txt

# 等效的明确写法
git reset --mixed HEAD file.txt
```

## 总结

- ✅ `git reset HEAD` = `git reset --mixed HEAD`
- ✅ 这是最常用的 reset 命令，用于取消暂存文件
- ✅ 它不会影响工作目录中的文件修改，只是将更改从暂存区移回工作区

如果你想要完全撤销更改（包括工作目录的修改），需要使用 `git reset --hard HEAD`，但请谨慎使用，因为这会永久丢弃未提交的更改。