## 今日重点
```markdown
commit[新] → tree[新] → parent(commit) → tree → blob
    ↑           ↑            ↑           
 a1083fc     9e96e77      1608b19
```

```markdown
commit ← commit
  ↓         ↓   
 tree      tree
  ↓         ↓
blob       blob
```

## 执行的命令
```bash
$ git ls-files -s
    100644 78981922613b2afb6025042ff6bd878ac1994e85 0       file.txt    ( Blob[旧] )
--------------------------------------------------------------------------------------
$ echo "b" > file.txt
$ git add file.txt

$ D:\prac>git ls-files -s
    100644 462948753a5dda77be908e15a176c39eeb17552e 0       file.txt    ( Blob[新] )⬅add了文件，就会产生新的Blob对象
----------------------------------------------------------------------------------------

$ git status
    On branch main
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
            modified:   file.txt
----------------------------------------------------------------------------------------
$ git commit -m "second commit"
    [main a1083fc] second commit
    1 file changed, 1 insertion(+), 1 deletion(-)

$ git cat-file -t a1083fc
    commit

$ git cat-file -p a1083fc
    tree 9e96e773eadd7f038e14d7d426a3e3aee3ae32e5     ( tree[新] )
    parent 1608b1978e3442ee36ffec630d46d5f9b6000b7a   (commit[旧] )
    author MissCheny <1312808428@qq.com> 1754456691 +0800
    committer MissCheny <1312808428@qq.com> 1754456691 +0800
    second commit
```

## 根据执行的命令，观察 `.git` 目录变化
<table>
<tr>
<td style="vertical-align:top">
 
```cmd
D:\prac>echo "b" > file.txt
```
写入或修改文件 `.git` 是没有任何变化的

</td><td style="vertical-align:top">

```cmd
D:\prac>git add file.txt
```
将文件添加到暂存区，`.git` 目录下新增了一个 **Blob对象** `4629487`


</td><td style="vertical-align:top">

```cmd
D:\prac>git commit -m "second commit"
[main a1083fc] second commit
 1 file changed, 1 insertion(+), 1 deletion(-)
```

</td></tr>

<td style="vertical-align:top">

```cmd
D:\prac>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│
├───hooks
│      (略) 
│
├───info
│       exclude
│
├───logs
│   │   HEAD
│   │
│   └───refs
│       └───heads
│               main
│
├───objects
│   ├───14162d6 ( tree   )
│   ├───1608b19 ( commit )
│   ├───7898192 ( Blob   )
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags
```

</td>
<td style="vertical-align:top">


```cmd
D:\prac>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│
├───hooks
│       (略)
│
├───info
│       exclude
│
├───logs
│   │   HEAD
│   │
│   └───refs
│       └───heads
│               main
│
├───objects
│   ├───14162d6 ( tree   )
│   ├───1608b19 ( commit )
│   ├───4629487 ( Blob [新])
│   ├───7898192 ( Blob   )
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags
```

</td>
<td style="vertical-align:top">

```cmd
D:\prac>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│
├───hooks
│       (略)
│
├───info
│       exclude
│
├───logs
│   │   HEAD
│   │
│   └───refs
│       └───heads
│               main
│
├───objects
│   ├───14162d6 ( tree        )
│   ├───1608b19 ( commit      )
│   ├───4629487 ( Blob   [新] )
│   ├───7898192 ( Blob        )
│   ├───9e96e77 ( tree   [新] )
│   ├───a1083fc ( commit [新] )
│   │
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags
```

</tr></table>

