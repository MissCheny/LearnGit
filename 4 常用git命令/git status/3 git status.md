<!-- <link rel='stylesheet' href='../style.css'> -->

<table>
<tr>
<td style="vertical-align: top; width:35%;">

```Bash
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   file.txt
```
  
**命令 `git status` 输出结果显示：**  

当前在 `main` 分支上，有个新的文件 `file.txt` 已经被暂存，但还没有进行任何提交。若取消暂存这个文件，可使用 `git rm --cached file.txt` 命令。

</td>
<td style="vertical-align: top;">

命令 `git status` 将返回当前 Git 仓库的状态信息。

- `On branch main`
当前所在的分支是 `main`

- `No commits yet`
    - 这个仓库中还没有提交（commit）过任何内容。
    - 一个提交代表了一次保存仓库状态的操作。

- `Changes to be committed:`
    - 即将提交（commit）的更改  
    - **to be committed** 是一个被动语态形式，表示还没有被提交，将要被提交。

- `(use "git rm --cached <file>..." to unstage)`
    - 使用 `git rm --cached <file>` 命令将 `<file>` 其从暂存区移除。

- `new file:   file.txt`
    - 新文件 `file.txt` 已经被暂存，准备提交到仓库中。

</td>
</tr>
</table>