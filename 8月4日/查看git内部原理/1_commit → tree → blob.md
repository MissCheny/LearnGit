本文重点
```powershell
objects
   ├───14162d（tree）
   ├───1608b1（commit）
   └───789819（以blob类型存储文件内容）
```
## commit → tree → blob

<table>
<tr>
<td style="width: 40%; padding-right: 15px; vertical-align: middle;">

`1608b19` 是 **commit** 对象

</td><td style="vertical-align: top;">

```Bash
$ git commit -m "first commit"
    [main (root-commit) 1608b19] first commit
    1 file changed, 1 insertion(+)
    create mode 100644 file.txt
```

</td></tr>
<tr>
<td style="width: 40%; padding-right: 15px; vertical-align: middle;">

`1608b19` 是 **commit** 对象，记录了 **tree** 对象 `14162d6` 的哈希值，以及提交者、提交时间等信息。

</td><td style="vertical-align: top;">

```bash
$ git cat-file -p 1608b19
    tree 14162d6...
    author MissCheny <1312808428@qq.com> 1754284999 +0800
    committer MissCheny <1312808428@qq.com> 1754284999 +0800
```

</td></tr>
<tr><td style="vertical-align: middle; width=20%;">

`14162d6` 是 **tree** 对象，记录了 **blob** 对象 `7898192` 的哈希值，以及文件名、权限等信息。


</td><td style="vertical-align: top;">

```bash
$ git cat-file -p 14162d6 
    100644 blob 7898192...    file.txt
```

</td></tr>
<tr><td style="vertical-align: middle; width=20%;">

`7898192` 是 **blob** 对象，记录了文件内容（文件名在 **tree** 对象中）。

</td><td style="vertical-align: top;">

```bash
% git cat-file -p 7898192
    a
```

</td></tr></table>

## 执行相关命令以验证
<table>
<tr>
<td style="vertical-align: top;">

```Bash
$ git init
$ echo "a" > file.txt
```
执行完 `git init` 后，会生成一个 `.git` 目录文件

</td>
<td style="vertical-align: top;">

```Bash
$ git add .
```
执行后，目录中多了 **index** 和 **789819...** 这两个对象
</td>
<td style="vertical-align: top;">

```Bash
$ git commit -m "first commit"

[main (root-commit) 1608b19] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 file.txt
```
返回结果 `1608b19` 是 **commit** 对象，记录了 **tree** 对象 `14162d6...` 的哈希值，以及提交者、提交时间等信息。
<tr>
<td style="vertical-align: top;">

```powershell
D:\prac\.git>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
│   config
│   description
│   FETCH_HEAD
│   HEAD
│
├───hooks
│      （略） 
│
├───info
│       exclude
│
├───objects
│   ├───info
│   └───pack
└───refs
    ├───heads
    └───tags
```

</td>
<td style="vertical-align: top;">

```powershell
D:\prac\.git>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│
├───hooks
│       （略）
│
├───info
│       exclude
│
├───objects
│   ├───78
│   │       9819...
│   ├───info
│   └───pack
└───refs
    ├───heads
    └───tags
```

</td>
<td style="vertical-align: top;">

```powershell
D:\prac\.git>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│
├───hooks
│       （略）
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
│   ├───14
│   │       162d
│   ├───16
│   │       08b1
│   ├───78
│   │       9819
│   ├───info
│   └───pack
└───ref
    ├───heads
    │       main
    └───tags
```
</td>

</tr>

<tr>
<td style="vertical-align: top;">
</td>
<td style="vertical-align: top;">

```powershell
git cat-file -t 789819
>blob（二进制文件类型）

git cat-file -p 789819
>a（文件内容）
```
`git cat-file`
- `-t` 查看对象的类型（type）
- `-p` 查看对象的内容（pretty）
- `-s` 查看对象的大小（size）
</td>
<td style="vertical-align: top;">

```powershell
D:\prac\.git>git cat-file -t 1608b1
commit

D:\prac\.git>git cat-file -p 1608b1
tree 14162d6c68b9fe5a7ffd21108888bfe66c92f948
author MissCheny <1312808428@qq.com> 1754284999 +0800
committer MissCheny <1312808428@qq.com> 1754284999 +0800

first commit

D:\prac\.git>git cat-file -t 14162d
tree

D:\prac\.git>git cat-file -p 14162d
100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    file.txt
```

</tr>
</table>