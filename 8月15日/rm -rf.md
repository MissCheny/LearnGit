
<table><tr><td style='vertical-align=top; width:250px;'>

```bash
rm -rf ./* .git
git init
echo '111' >> aaa.txt
git add ./
git commit -m '111' ./
echo '222' >> aaa.txt
git commit -m '222' ./
```

</td><td style='vertical-align=top;'>

`./` 表示当前目录

`*` 是一个通配符，表示当前目录下的所有文件和目录（不包括隐藏文件，即以`.`开头的文件）

`rm -rf ./*` 的意思是删除当前目录下的所有文件和目录，但不包括`.git`目录和其他以`.`开头的隐藏文件或目录。

在 `git add ./` 命令中，`.` 可以省略，直接使用 `git add .` 即可

`git commit -m '提交信息' ./` 这个命令实际上是错误的，`git commit` 命令后面不需要指定文件路径。正确的用法是 `git commit -m '提交信息'`。

</td></tr></table>