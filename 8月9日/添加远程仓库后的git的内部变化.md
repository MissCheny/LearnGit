## 添加远程仓库后.git目录下会有什么变化？

<table><tr><td style='vertical-align:top; width:40%;'>

1. **config文件**：在`.git/config`文件中，会添加远程仓库的相关配置信息，比如远程仓库的名称（通常是`origin`）、URL地址等。

2. **refs/remotes目录**：在`.git/refs/remotes`目录下，会创建一个以远程仓库名称命名的子目录（比如`origin`），并且在该子目录中会为远程仓库的每一个分支创建一个文件，文件中存储的是远程分支的最后一个提交对象的哈希值。

3. **FETCH_HEAD文件**：在`.git/FETCH_HEAD`文件中，会记录最近一次从远程仓库拉取的分支信息及其对应的提交哈希值。

4. **logs/refs/remotes目录**：在`.git/logs/refs/remotes`目录下，会记录远程分支引用的变更历史，每个远程分支在其对应的文件中都有日志记录。

这些变化是为了让你的本地Git仓库能够更好地与远程仓库进行交互，比如拉取（fetch）、推送（push）等操作。


<td style='vertical-align:top;'>

未添加远程仓库：
```markdown
.git
├── HEAD
├── branches
├── config
│   (本地仓库的配置信息)
├── description
├── hooks
├── info
│   └── exclude
├── objects
│   ├── info
│   └── pack
└── refs
    ├── heads
    │   └── main
    └── tags
```

</td><td style='vertical-align:top;'>

已添加远程仓库：
```markdown
.git
├── HEAD
├── branches
├── config
│   (本地仓库和远程仓库的配置信息)
├── description
├── hooks
├── info
│   └── exclude
├── objects
│   ├── info
│   └── pack
├── refs
│   ├── heads
│   │   └── main
│   └── tags
|
├── FETCH_HEAD
├── logs
│   └── refs
│       └── remotes
│           └── origin
│               └── main
└── refs
    └── remotes
        └── origin
            └── main
```

</td></tr></table>

## 用命令验证

1. 若 **本地 `main` 分支** 与 **远程的 `origin/main` 分支** 同步，那么这里的 `(commit-hash)` 应该是一致的。

   ```bash
   $ git mylog
      <commit-hash> (HEAD → main, origin/main)
   ```

   <table><tr><td rowspan=2 style='vertical-align:top; width:35%;'>

   ```markdown
   .git
   |
   ├── refs
   │   ├── heads
   │   │   └── main (commit-hash)
   │   └── tags
   |
   └── refs
      └── remotes
         └── origin
               └── main (commit-hash)
   ```

   <td style='vertical-align:top; width:%;'>

   ```cmd
   .git
   ├── refs
   │   ├── heads
   │   │   └── main
   ```

   </td><td style='vertical-align:top;'>

   ```cmd
   type .git\refs\heads\main
      <commit-hash>
   ```

   </td></tr><tr><td style='vertical-align:top; width:25%;'>

   ```cmd
   .git
   ├── refs
   │   ├── remotes
   |   |   ├── origin
   |   |   |   └── main
   ```

   </td><td style='vertical-align:top;'>

   ```cmd
   type .git\refs\remotes\origin\main
      <commit-hash>
   ```
   这个命令会显示远程分支`origin/main`的最后一个提交对象的哈希值。

   </td></tr></table>

2. 若 **本地 `main` 分支** 与 **远程的 `origin/main` 分支** 不同步，那么这里的 `(commit-hash)` 应该是不同的。

   ```bash
   $ git mylog
      <commit-hash> (HEAD → main)   # 本地main分支超前于远程origin/main分支1个提交
      <commit-hash> (origin/main)
   ```


---

1. 查看远程仓库的配置信息：
   ```bash
   git remote -v
   ```
   这个命令会列出所有配置的远程仓库及其URL地址（用于-fetch和push）。

2. 查看`.git/config`文件中的远程仓库配置：
   ```cmd
   type .git\config
   ```
   这个命令会直接显示`.git/config`文件的内容，你可以在这个文件中看到远程仓库的配置信息。

3. 查看`.git/refs/remotes`目录下的内容：
   ```bash
   tree .git\refs\remotes
   ```
   这个命令会列出`.git/refs/remotes`目录下的所有远程仓库名称。

4. 查看某个远程仓库的某个分支的哈希值：
   ```cmd
   type .git\refs\remotes\origin\branch_name
   ```
   将`branch_name`替换为你想要查看的远程分支名称，这个命令会显示该远程分支的最后一个提交对象的哈希值。

5. 查看`.git/FETCH_HEAD`文件的内容：
   ```cmd
   type .git\FETCH_HEAD
   ```
   这个命令会显示最近一次从远程仓库拉取的分支信息及其对应的提交哈希值。

6. 查看`.git/logs/refs/remotes`目录下的内容：
   ```cmd
   tree .git\logs\refs\remotes\origin
   ```
   这个命令会列出`.git/logs/refs/remotes/origin`目录下的所有远程分支的日志文件。