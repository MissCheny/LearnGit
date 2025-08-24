```bash
$ git init
Initialized empty Git repository in D:/learngit/.git/

$ (echo Git is a version control system. && echo Git is free software.) > readme.txt && git add readme.txt && git commit -m "wrote a readme file"
[main (root-commit) 5e77c2f] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt

$ (echo Git is a distributed version control system. && echo Git is a free software.) > readme.txt &&git commit -am "add distributed"
[main beb1d08] add distributed
 1 file changed, 2 insertions(+), 2 deletions(-)

$ (echo Git is a distributed version control system. && echo Git is free software distributed under the GPL.) > readme.txt && git commit -am "append GPL"
[main 65d8b00] append GPL
 1 file changed, 1 insertion(+), 1 deletion(-)
```

<table>
<tr><td style='vertical-align:bottom;;'>

```bash
$ git mylog
* 65d8b00 (7 seconds ago) append GPL  (HEAD -> main)
* beb1d08 (15 seconds ago) add distributed
* 5e77c2f (35 seconds ago) wrote a readme file
```

</td><td style='vertical-align:top;'>

```bash
$ git reset --mixed HEAD~1
Unstaged changes after reset:
M       readme.txt
```

<br>

```bash
$ git mylog
* beb1d08 (8 minutes ago) add distributed  (HEAD -> main)
* 5e77c2f (9 minutes ago) wrote a readme file
```

</td></tr>
<tr><td style='vertical-align:top;'>

```cmd
PS D:\learngit> tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGIT\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   HEAD
│   index
```

</td><td style='vertical-align:top;'>

```cmd
PS D:\learngit> tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGIT\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD (新增)
│   HEAD
│   index
│   ORIG_HEAD (新增)
```

</td></tr>

<tr><td style='vertical-align:top;'>

```bash
$ git ls-files -s
100644 65d8b003243f4d738fd1e02717f4fbaecdfdc7d1 0       readme.txt

$ git cat-file -p 65d8b00
Git is a distributed version control system.
Git is free software distributed under the GPL.
```

</td><td style='vertical-align:top;'>

```bash
$ git ls-files -s
100644 53676267be4e4d738fd1e02717f4fbaecdfdc7d1 0       readme.txt

$ git cat-file -p 5367626
Git is a distributed version control system.
Git is a free software.
```

</td></tr></table> 