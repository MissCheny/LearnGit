## 简单的目录结构
<table>
<tr>
<td style="vertical-align: top; width:150px;">

假设有以下目录结构：
```
prac/
└── file.txt
```

</td>
<td style="vertical-align: top; width:480px;">

初始化仓库并添加文件：
```bash
$ git init
Initialized empty Git repository in /path/to/prac/.git/

$ git add file.txt

$ git commit -m "Initial commit"
[main (root-commit) 1608b19] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 file.txt
```

</td>
<td style="vertical-align: top;">

`[main (root-commit) 1608b19] Initial commit`
- `main` 提交的分支名
- `(root-commit)` 根提交，即该分支的第一个提交
- `1608b19` 该提交的哈希值
- `Initial commit`：我写的提交信息，通过 `-m` 参数指定。

`1 file changed, 1 insertion(+)`
- 有1个文件被修改了，其中新增了1行内容。插入的内容用 `+` 号表示。

`create mode 100644 file.txt`：创建了一个模式为 `100644` 的文件。
- `100644` 是文件的权限模式，通常表示这是一个普通的文件，并且所有者有读写权限，而组用户和其他用户只有读权限。
- `file.txt` 是我刚刚创建的文件名。

</td>
</tr>
</table>


## 复杂的目录结构

<table>
<tr>
<td style="vertical-align: top; width:200px;">

假设有以下项目结构：
```
prac/
├── README.md
├── src/
│   ├── main.c
│   ├── utils/
│       ├── helper.c
│       └── helper.h
└── include/
    └── config.h
```

</td>
<td style="vertical-align: top; width:420px;">

初始化仓库并添加文件：
```powershell
D:\prac> git init
Initialized empty Git repository in D:/prac/.git/

D:\prac> git add .

D:\prac> git commit -m "Initial commit"
[main (root-commit) 1234567] Initial commit
    4 files changed, 10 insertions(+)
    create mode 100644 README.md
    create mode 100644 src/main.c
    create mode 100644 src/utils/helper.c
    create mode 100644 src/utils/helper.h
    create mode 100644 include/config.h
```

</td>
<td style="vertical-align: top;">

`[main (root-commit) 1234567] Initial commit`
- `main` 提交的分支名
- `(root-commit)` 根提交，即该分支的第一个提交
- `1234567` 该提交的哈希值
- `Initial commit`：我写的提交信息，通过 `-m` 参数指定。

`4 files changed, 10 insertions(+)`
- 有4个文件被修改了，其中新增了10行内容。插入的内容用 `+` 号表示。

`create mode 100644 [file name]`：创建普通模式文件
```powershell
    create mode 100644 README.md
    create mode 100644 src/main.c
    create mode 100644 src/utils/helper.c
    create mode 100644 src/utils/helper.h
    create mode 100644 include/config.h
```
创建了5个模式为 `100644` 的文件  
`100644` 是文件的权限模式，通常表示这是一个普通的文件，且我有读写权限，而组用户和其他用户只有读权限。

</td>
</tr>
</table>
