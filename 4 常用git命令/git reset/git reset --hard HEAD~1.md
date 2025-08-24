## 执行 `git reset --hard HEAD~1` 后的git内部变化：

<table><tr><td style='vertical-align:top;'>

```Bash


git mylog
* 6fdf424 (56 seconds ago) append GPL  (HEAD -> main)
* 5c50446 (4 minutes ago) add distributed
* 9a20565 (10 minutes ago) wrote a readme file
```

</td><td style='vertical-align:top;'>

```Bash
$ git reset --hard HEAD~1
HEAD is now at 5c50446 add distributed

$ git mylog
* 5c50446 (23 hours ago) add distributed  (HEAD -> main)
* 9a20565 (23 hours ago) wrote a readme file
```

</td></tr><tr><td style='vertical-align:top;'>

```cmd
D:\learngit>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGIT\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
```

</td><td style='vertical-align:top;'>

```cmd
D:\learngit>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGIT\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│   ORIG_HEAD（新增）
```

</td></tr></table>


<table><tr><td style='vertical-align:top;'>

```Bash
$ cat .git/ORIG_HEAD
6fdf4246faa8f5ca907a4854fb984ce7ee1c0c84 (版本2的commit)

$ git cat-file -p 6fdf424 (commit)
tree a60b9190c0b9eaa1603310ceaf099adddb9f1d98 (tree)
parent 5c5044665de425c5e0c8bc842f0e096946af86d7
author MissCheny <1312808428@qq.com> 1755581421 +0800
committer MissCheny <1312808428@qq.com> 1755581421 +0800

append GPL

$ git cat-file -p a60b919 (tree)
100644 blob 5ebee157af7808cd2880a227ffdb6a8eef4574f1    readme.txt (blob)

$ git cat-file -p 5ebee15 (blob【版本2：add distributed】)    
Git is a distributed version control system.
Git is free software distributed under the GPL.
```

</td><td style='vertical-align:top;'>

```txt
.git/ORIG_HEAD → 版本2的commit(6fdf424)
                    ↓
                  tree(a60b919)
                    ↓
                   blob
            (版本2：add distributed)
```

</td></tr></table>


<table><tr><td style='vertical-align:top;'>

## 撤回 `git reset --hard HEAD~1` 后的git内部变化：

<table><ta><td style='vertical-align:top;'>

```cmd
D:\learngit>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGIT\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│   ORIG_HEAD (版本2的commit)
```


</td><td style='vertical-align:top;'>

```cmd
D:\learngit>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGIT\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│   ORIG_HEAD (版本3的commit)
```

</td></tr></table>



<table><tr><td style='vertical-align:top;'>

```Bash
$ cat .git/ORIG_HEAD
5c5044665de425c5e0c8bc842f0e096946af86d7

$ git cat-file -p 5c50446
tree 3d4bd4794f98d5bcc6e00be3480a3479d3c661a1
parent 9a20565672a1ac83467feb8a27bbcffa957d30f6
author MissCheny <1312808428@qq.com> 1755581264 +0800
committer MissCheny <1312808428@qq.com> 1755581264 +0800

add distributed

$ git cat-file -p 3d4bd47
100644 blob a14450eb8917425e6482dae90615c1b874052934    readme.txt

$ git cat-file -p a14450e
Git is a distributed version control system.
Git is free software.
```

</td><td style='vertical-align:top;'>

```txt
.git/ORIG_HEAD → 版本2的commit(5c50446)
                    ↓
                  tree(3d4bd47)
                    ↓
                  blob
          (版本2：add distributed)
```

</td></tr></table>