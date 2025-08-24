<table><tr><td style='vertical-align:top;'>

#### 初始状态
```
A -> B -> C (HEAD)
```

</td><td style='vertical-align:middle;'>
<br><br>
留意存区（staging area）和工作目录（working directory）的状态:

</td></tr></table>

<table><tr><td style='vertical-align:top;'>

#### `git reset --soft HEAD~1` 后
```
A -> B (HEAD) -> C
```
- 暂存区有 commit `C` 的更改。
- 工作目录有 commit `C` 的更改。

</td><td style='vertical-align:top;'>

#### `git reset --mixed HEAD~1` 后
```
A -> B (HEAD) -> C
```
- 暂存区没有 commit `C` 的更改。
- 工作目录有 commit `C` 的更改。

</td><td style='vertical-align:top;'>

#### `git reset --hard HEAD~1` 后
```
A -> B (HEAD)
C
```
- 暂存区没有 commit `C` 的更改。
- 工作目录恢复到 commit `B` 的状态。
- commit `C` 不再存在于当前分支的历史中。



</td></tr><tr><td style='vertical-align:top;'>

</td><td style='vertical-align:top;'>

</td><td style='vertical-align:top;'>

执行后会新增 `.git/ORIG_HEAD` 目录，  
所以，`git reset --hard ORIG_HEAD1` 是恢复到上一次提交的状态的“后悔药”

</td></tr></table>

<br><br><br>


<table>
<tr><td style='vertical-align:top;'>

</td><td style='vertical-align:top;'>

```bash
$ git reset --soft HEAD~1
```

</td></tr>
<tr><td style='vertical-align:top;'>

```bash
$ git mylog
* 102f67c (13 seconds ago) append GPL  (HEAD -> main)
* 889a029 (19 seconds ago) add distributed
* c5bbb1f (28 seconds ago) wrote a readme file

$ git ls-files -s
100644 8443d230a5fda3c1f1cc18a586a6a860d0a2537b 0       readme.txt

$ git cat-file -p 8443d23
Git is a distributed version control system.
Git is free software distributed under the GPL.
```

</td><td style='vertical-align:top;'>

```bash
$ git mylog
* 889a029 (14 minutes ago) add distributed  (HEAD -> main)
* c5bbb1f (14 minutes ago) wrote a readme file


$ git ls-files -s
100644 8443d230a5fda3c1f1cc18a586a6a860d0a2537b 0       readme.txt

$ git cat-file -p 8443d23
Git is a distributed version control system.
Git is free software distributed under the GPL.
```

```
$ cat .git/ORIG_HEAD
102f67c8cfa002cb32d1768040e407c16e94a216

$ git cat-file -p 102f67c
tree 411c5c2654fe24749d9c24df848dbebd2a01521f
parent 889a0297433c1f83b0ce5a304540c66a88d9bda6
author MissCheny <1312808428@qq.com> 1755760608 +0800
committer MissCheny <1312808428@qq.com> 1755760608 +0800

append GPL

$ git cat-file -p 411c5c2
100644 blob 8443d230a5fda3c1f1cc18a586a6a860d0a2537b    readme.txt

$ git cat-file -p 8443d23
Git is a distributed version control system.
Git is free software distributed under the GPL.
```

</td></tr></table>