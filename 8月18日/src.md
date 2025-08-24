```bash
Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git switch -c dev
    Switched to a new branch 'dev'

Lenovo@老子的拯救者 MINGW64 /d/learngit (dev)
$ git commit -am "本地修改：全部删除，只保留了一个文件"
    [dev e125823] 本地修改：全部删除，只保留了一个文件
    72 files changed, 7132 deletions(-)
    delete mode 100644 8月10日 四海一家/settings.md
    delete mode 100644 8月11日/index的作用.md
    delete mode 100644 8月11日/log.ipynb
    ...

Lenovo@老子的拯救者 MINGW64 /d/learngit (dev)
$ git mylog
    * e125823 (9 seconds ago) 本地修改：全部删除，只保留了一个文件  (HEAD -> dev)
    * d53e498 (42 minutes ago) Initial commit  (main)

Lenovo@老子的拯救者 MINGW64 /d/learngit (dev)
$
```

```powershell
PS D:\> cd learngit

PS D:\learngit> git reflog
e125823 (HEAD -> dev) HEAD@{0}: commit: 本地修改：全部删除，只保留了一个文件
d53e498 (main) HEAD@{1}: checkout: moving from main to dev
d53e498 (main) HEAD@{2}: commit (initial): Initial commit

PS D:\learngit> git mylog
* e125823 (34 minutes ago) 本地修改：全部删除，只保留了一个文件  (HEAD -> dev)
* d53e498 (76 minutes ago) Initial commit  (main)
```