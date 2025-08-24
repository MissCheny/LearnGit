<table>
<tr>
<td style="vertical-align: top;">

回退到上一级目录：

```cmd
D:\prac\.git>cd ..

D:\prac>
```

</td>
<td style="vertical-align: top;">

清屏：

```cmd
cls
```
</td>
<td style="vertical-align: top;">

显示目录结构
```
tree
```

</td>
<td style="vertical-align: top;">

查看暂存区文件<br>
解析二进制内容
```
git ls-files -s
```

</td>

<td style="vertical-align: top;">

显示文件内容

```bash
$ git cat-file -p :file.txt
    "b"
```
</td> </tr> </table>

### 显示文件内容
<table>
<tr>
<td style="vertical-align: top">

Windows 系统下用 `type` 命令

</td>
<td style="vertical-align: top">

Linux 系统中常用Bash命令，<br>用 `cat` 命令

</td>
</tr>
<td style="vertical-align: top;">

```cmd
type file.txt
```

</td>
<td style="vertical-align: top;">

```bash
$ git show :file.txt
$ cat file.txt
```
</td>
</tr>
</table>

---

<table><tr><td style="vertical-align: top;">

```cmd
type .git\HEAD
ref: refs/heads/main
```

</td><td style="vertical-align: top;">

```bash
$ git rev-parse HEAD
```

</td></tr></table>

`ls -lh` 
- `ls`：列出
- `-l`：长格式
- `-h`：人类可读的格式

`cat <filename>`
- `cat`（concatenate）：查看文本文件内容


`d:` 切换到D盘、`cd` 切换目录、`dir` 查看目录内容、`mkdir` 创建目录、`rmdir` 删除目录、`tree` 显示目录结构