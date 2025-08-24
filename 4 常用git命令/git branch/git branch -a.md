<table><tr><td style='vertical-align:top;'>

```bash
$ git branch -a
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/main

$ git branch -r
  origin/HEAD -> origin/main
  origin/main
```

</td><td style='vertical-align:middle;'>

在需要同步代码或创建新分支时，可以帮助确认分支状态

- `remotes/` 前缀表示这些是远程分支在本地的缓存
- `HEAD -> origin/main` 表示远程仓库的默认分支是 main
- 远程分支的格式是 `<远程仓库名>/<分支名>`（如 origin/main）
- 星号 `*` 在 Git 的输出中总是表示当前所处的分支

</td></tr></table>

---

<table><tr><td style='vertical-align:top;'>

列出所有本地和远程跟踪分支

```bash
git branch -a
```

</td><td style='vertical-align:top;'>

本地分支只有 main，远程仓库(origin)的默认分支也是 main

```
* main                ← 当前所在的分支（带星号）
remotes/origin/HEAD → origin/main  ← 远程仓库的默认分支指向
remotes/origin/main   ← 远程仓库的 main 分支
```

</td></tr></table>

---

<table><tr><td style='vertical-align:top;'>

列出远程跟踪分支

```bash
git branch -r
```

</td><td style='vertical-align:top;'>

这个命令过滤了本地分支，只显示来自 origin 远程仓库的分支信息

```
origin/HEAD → origin/main  ← 远程仓库的 HEAD 引用
origin/main               ← 远程仓库的 main 分支
```

</td></tr></table>