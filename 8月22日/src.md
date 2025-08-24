```bash
Lenovo@老子的拯救者 MINGW64 ~
$ cd /d/learngit

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   file1.txt
        new file:   file2.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        file3.txt


Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git reflog
fatal: your current branch 'main' does not have any commits yet

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git ls-files -s
100644 5f2f16bfff90e6620509c0cf442e7a3586dad8fb 0       file1.txt
100644 c7dc989f8044a4fcf16361414998e14694e1ac7e 0       file2.txt

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git add .

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git ls-files -s
100644 5f2f16bfff90e6620509c0cf442e7a3586dad8fb 0       file1.txt
100644 c7dc989f8044a4fcf16361414998e14694e1ac7e 0       file2.txt
100644 427b8925f9e98c668e6647bc280000f59d8df530 0       file3.txt

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   file1.txt
        new file:   file2.txt
        new file:   file3.txt


Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git commit -m "file1、2、3.txt"
[main (root-commit) 5e3ff3d] file1、2、3.txt
 3 files changed, 4 insertions(+)
 create mode 100644 file1.txt
 create mode 100644 file2.txt
 create mode 100644 file3.txt

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git commit -am "folder1、2、3.txt"
[main 199437c] folder1、2、3.txt
 3 files changed, 4 deletions(-)
 delete mode 100644 file1.txt
 delete mode 100644 file2.txt
 delete mode 100644 file3.txt

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git mylog
* 5e3ff3d (30 minutes ago) file1、2、3.txt  (HEAD -> main)

Lenovo@老子的拯救者 MINGW64 /d/learngit (main)
$ git commit -am "folder1、2、3、4.txt"
[main 23e9979] folder1、2、3、4.txt
 3 files changed, 4 deletions(-)
 delete mode 100644 file1.txt
 delete mode 100644 file2.txt
 delete mode 100644 file3.txt
```