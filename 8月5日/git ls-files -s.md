<table>
<tr>
<td style="vertical-align: top; width:250px;">

查看已经添加到暂存区的文件命令:
```
git ls-files -s
```
执行 `git add` 命令后，`git ls-files -s` 就会显示暂存区中所有的文件及其状态。

</td>
<td style="vertical-align: top;">




命令 `git ls-files -s` 的输出格式如下：

```
<mode> <sha1> <stage>\t<file>
```

- `<mode>` 文件的权限模式
    - `100644` 普通可读写文件，所有者有读写权限，而组用户和其他用户只有读权限。
    - `100755` 可执行文件，所有者有读写执行权限，而组用户和其他用户只有读权限。
    - `120000` 符号链接文件。
- `<sha1>` 文件内容对应的 blob 对象的 SHA-1 哈希值
- `<stage>` 文件的阶段号（文件处在什么阶段）
    - `0` 已提交到仓库中
    - `1` 已添加到暂存区
    - `2` 已提交到暂存区但还没有提交到仓库中
- `<file>` 文件名

---

实际运行结果：
```
$ git add .
$ git ls-files -s

100644 78981922613b2afb6025042ff6bd878ac1994e85 0       file.txt
```

- `file.txt` 的权限模式是 `100644`。
- `file.txt` 的内容对应的 blob 对象的 SHA-1 哈希值是 `789819226...`
- 阶段号是 `0`，表示这个文件已经提交到仓库中。
- `file.txt` 是文件名。

</td>
</tr>
</table>

### `git ls-files -s` 是怎么知道暂存的文件的？

Git 使用暂存区来保存文件的快照，这些快照将被包含在下一次提交中。当我运行 `git add` 命令时，Git 会将文件的当前内容添加到暂存区，并生成一个对应的 blob 对象。这个 blob 对象的 SHA-1 哈希值就是 `git ls-files -s` 输出中的 `<sha1>` 部分。

`git ls-files -s` 读取暂存区文件的信息，这些信息存储在 `.git/index` 文件中。这个文件是一个二进制文件，包含了工作目录中所有文件的元数据，包括文件的权限、内容的 SHA-1 哈希值以及文件路径等。通过解析 `.git/index` 文件，Git 可以获取暂存区文件的详细信息，并在执行 `git ls-files -s` 时将其输出。

---

<table>
<tr>
<td style='vertical-align: top;'>

```markdown
D:\prac\.git>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index(二进制文件)
│
├───hooks
├───info
├───logs
│
├───objects
│   ├───14162d
│   ├───1608b1
│   ├───789819(blob对象的SHA-1值)
│   ├───info
│   └───pack
└───ref
    ├───heads
    │       main
    └───tags
```
</td>
<td style='vertical-align: top;'>

```markdown
D:\prac>git ls-files -s
    100644 78981922613b2afb60250... 0       file.txt

D:\prac>git cat-file -p 789819
    a
```
`789819` 是blob对象，内容为 `a`  
`git cat-file -p 789819` 可查看 `789819` 对应的内容为 `a`  
`.git/index` 中的SHA-1值是 `789819` 
</td>
</tr>
</table>