## flowchart
```txt
commit 0dbd4e6
    |
    | (author: MissCheny)
    | (committer: MissCheny)
    | (message: Initial commit)
    |    V
  tree a2fae7a
    |
    |--- file1.txt (blob ee946e5)
    |
    |--- file2.txt (blob 4629487)
```

### 1. 创建并初始化仓库
```cmd
$ mkdir prac2 && cd prac2

$ git init
    Initialized empty Git repository in D:/prac2/.git/

$ git status
    On branch main

    No commits yet

    nothing to commit (create/copy files and use "git add" to track)
```

--- 

### 2. 写入文件并提交
<table><tr>
<td style="width: 45%; vertical-align: top;">

```cmd
$ echo "a" > file1.txt
$ echo "b" > file2.txt
$ git add .
```

生成2个Blob对象，  
分别对应file1.txt和file2.txt。

</td><td style="vertical-align: top;">

```cmd
tree /f .git

\.GIT
   └─objects
       ├───4629487(Blob对象, 内容为"b")
       └───ee946e5(Blob对象, 内容为"a")
```

```bash
$ git cat-file -p 4629
    "b"

$ git cat-file -p ee94
    "a"
```

</td></tr></table>

```bash
git ls-files -s
100644 ee946e553bd40581abcec7addc... 0       file1.txt   (Blob对象, 内容为"a")
100644 462948753a5dda77be908e15a1... 0       file2.txt   (Blob对象, 内容为"b")
```

---

### 3. 提交(Initial commit)

```bash
$ git commit -m "Initial commit"
    [main (root-commit) 0dbd4e6] Initial commit
    2 files changed, 2 insertions(+)
    create mode 100644 file1.txt
    create mode 100644 file2.txtgit commit -m "Initial commit"
```

```bash
tree /f .git

\.GIT
   └─objects
       ├───0dbd4e6 (commit对象 → tree对象a2fae7a)
       ├───a2fae7a ( tree 对象 → 2个Blob对象[ee946e5, 4629487])
       ├───4629487 ( Blob 对象，内容为"b")
       └───ee946e5 ( Blob 对象，内容为"a")
```
```bash
$ git cat-file -p 0dbd
    tree a2fae7a75d6e57cbec5da287395f13fe033454c2
    author MissCheny <1312808428@qq.com> 1754538398 +0800
    committer MissCheny <1312808428@qq.com> 1754538398 +0800

    Initial commit

$ git cat-file -p a2fa
    100644 blob ee946e553bd40581abcec7addcb70facc6019299    file1.txt
    100644 blob 462948753a5dda77be908e15a176c39eeb17552e    file2.txt

$ git cat-file -t a2fa
    tree

$ git cat-file -t 0dbd
    commit
```

## flowchart
```txt
commit 4e2d5f9
    |
    | (author: MissCheny)
    | (committer: MissCheny)
    | (message: second commit)
    |
    V
  tree 92a7763
    |
    |--- file1.txt (blob ee946e5)
    |
    |--- file2.txt (blob 190c5e3)
    |
    | (parent: commit 0dbd4e6)
    |
    V
commit 0dbd4e6
    |
    | (author: MissCheny)
    | (committer: MissCheny)
    | (message: Initial commit)
    |
    V
  tree a2fae7a
    |
    |--- file1.txt (blob ee946e5)
    |
    |--- file2.txt (blob 4629487)
```

### 修改 file2.txt 文件内容

<table><tr><td style="width: 35%; vertical-align: top;">

```cmd
tree /f prac2
    D:.
        file1.txt
        file2.txt

type file1.txt
    "a"

type file2.txt
    "b"

$ echo "c" > file2.txt
```

</td>

<td style="vertical-align: top;">

在 cmd 终端下用 `type`，在 Bash 终端用 `cat` 命令查看文件内容。

```bash
tree /f .git

\.GIT
   └─objects
       ├───0dbd4e6 (commit对象 → tree对象a2fae7a)
       ├───a2fae7a ( tree 对象 → 2个Blob对象[ee946e5, 4629487])
       ├───4629487 ( Blob 对象，内容为"b")
       └───ee946e5 ( Blob 对象，内容为"a")
```

</td></tr>

<tr>
<td colspan="2" style="vertical-align: middle;">

```cmd
$ git status
    On branch main
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
            modified:   file2.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

</td></tr></table>

---

### 添加并提交 file2.txt 文件

<table><tr><td style="width: 34%; vertical-align: top;">

```bash
$ git add file2.txt
$ git cat-file -p 190c5e3
    "c"
```

</td><td style="vertical-align: middle;">

```markdown
tree /f .git

\.GIT
   └──objects
        |
        ├───190c5e3 ( Blob 对象，内容为"c" [新])
        |
        ├───0dbd4e6 (commit对象 → tree对象a2fae7a)
        ├───a2fae7a ( tree 对象 → 2个Blob对象[ee946e5, 4629487])
        ├───4629487 ( Blob 对象，内容为"b")
        └───ee946e5 ( Blob 对象，内容为"a")
```

</td></tr></table>

```bash
$ git ls-files -s
    100644 ee946e553bd40581abcec7addcb70facc6019299 0       file1.txt  (Blob 对象，内容为"a")
    100644 190c5e32531f3716e08e460511c466410504c83f 0       file2.txt  (Blob 对象，内容为"c" [新])
```

---

```markdown
$ git commit -m "second commit"
    [main 4e2d5f9] second commit
    1 file changed, 1 insertion(+), 1 deletion(-)

$ git cat-file -p 4e2d5f9
    tree 92a776312b2b0c41bd9da04d2ae5ce43b4a95ab0
    parent 0dbd4e6bd9c6a5b258151587ed95cfd18767d7fd
    author MissCheny <1312808428@qq.com> 1754549635 +0800
    committer MissCheny <1312808428@qq.com> 1754549635 +0800

    second commit

$ git cat-file -p 92a7763 (tree)
    100644 blob ee946e553bd40581abcec7addcb70facc6019299    file1.txt  (Blob 对象，内容为"a")
    100644 blob 190c5e32531f3716e08e460511c466410504c83f    file2.txt  (Blob 对象，内容为"c" [新])

$ git cat-file -p 0dbd4e6 (parent commit)
    tree a2fae7a75d6e57cbec5da287395f13fe033454c2             (tree 对象 → 2个Blob对象[ee946e5, 4629487])
    author MissCheny <1312808428@qq.com> 1754538398 +0800
    committer MissCheny <1312808428@qq.com> 1754538398 +0800

    Initial commit
```

```
\.GIT
   └──objects
        |
        ├───4e2d5f9 (commit对象 → tree对象92a7763)               [新]
        ├───92a7763 ( tree 对象 → 2个Blob对象[ee946e5, 190c5e3]) [新]
        |
        ├───190c5e3 ( Blob 对象，内容为"c")
        |
        ├───0dbd4e6 (commit对象 → tree对象a2fae7a)
        ├───a2fae7a ( tree 对象 → 2个Blob对象[ee946e5, 4629487])
        ├───4629487 ( Blob 对象，内容为"b")
        └───ee946e5 ( Blob 对象，内容为"a")
```

<img src='pic/commit.png' width=350>