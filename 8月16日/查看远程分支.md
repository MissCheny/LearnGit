### 2. 查看远程分支

<table><tr><td style='vertical-align:top;'>

列出所有远程分支：
```bash
$ git branch -r
```

</td><td style='vertical-align:top;'>

只显示远程仓库的所有分支，但不切换

```
origin/HEAD -> origin/main
origin/dev
origin/main
origin/feature
```
</td></tr></table>

### 3. 查看所有分支（包括本地和远程）
#### <font size=3><center>本地分支与远程仓库同步</center></font>

<table><tr><td style='vertical-align:top;'>

```bash
$ git branch -vv
```

</td><td style='vertical-align:top;'>

```
  * main 1a2b3c4 [origin/main] 添加了新的功能
    dev  5d6e7f8 [origin/dev] 修复了bug
```
</td></tr></table>

- `* main 1a2b3c4 [origin/main] 添加了新的功能`：  
  - `* main`：当前所在的分支
  - `1a2b3c4`：该分支的最新提交
  - `origin/main`：这个分支与远程仓库 `origin` 的 `main` 分支同步
  - 提交信息是“添加了新的功能”。
  
- `dev  5d6e7f8 [origin/dev] 修复了bug`：  
  - `dev`：一个本地分支
  - `5d6e7f8`：该分支的最新提交
  - `origin/dev`：这个分支与远程仓库 `origin` 的 `dev` 分支同步
  - 提交信息是“修复了bug”。

#### <font size=3><center>本地分支与远程分支不同步</center></font>

<table><tr><td style='vertical-align:top;'>

```bash
$ git branch -vv
```

</td><td style='vertical-align:top;'>

```
  main 1a2b3c4 [origin/main] 添加了新的功能
* dev  5d6e7f8 [origin/dev: ahead 1] 修复了bug
```
</td></tr></table>