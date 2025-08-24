```cmd
D:\>mkdir prac2

D:\>cd prac2

D:\prac2>git init
Initialized empty Git repository in D:/prac2/.git/

D:\prac2>git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)

D:\prac2>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
No subfolders exist


D:\prac2>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC2\.GIT
│   config
│   description
│   HEAD
│
├───hooks
│       applypatch-msg.sample
│       commit-msg.sample
│       fsmonitor-watchman.sample
│       post-update.sample
│       pre-applypatch.sample
│       pre-commit.sample
│       pre-merge-commit.sample
│       pre-push.sample
│       pre-rebase.sample
│       pre-receive.sample
│       prepare-commit-msg.sample
│       push-to-checkout.sample
│       sendemail-validate.sample
│       update.sample
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

D:\prac2>echo "a" > file1.txt && echo "b" > file2.txt

D:\prac2>git add .

D:\prac2>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
    file1.txt
    file2.txt

No subfolders exist


D:\prac2>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC2\.GIT
│   config
│   description
│   HEAD
│   index
│
├───hooks
│       applypatch-msg.sample
│       commit-msg.sample
│       fsmonitor-watchman.sample
│       post-update.sample
│       pre-applypatch.sample
│       pre-commit.sample
│       pre-merge-commit.sample
│       pre-push.sample
│       pre-rebase.sample
│       pre-receive.sample
│       prepare-commit-msg.sample
│       push-to-checkout.sample
│       sendemail-validate.sample
│       update.sample
│
├───info
│       exclude
│
├───objects
│   ├───46
│   │       2948753a5dda77be908e15a176c39eeb17552e
│   │
│   ├───ee
│   │       946e553bd40581abcec7addcb70facc6019299
│   │
│   ├───info
│   └───pack
└───refs
    ├───heads
    └───tags

D:\prac2>git cat-file -s 4629
5

D:\prac2>git cat-file -p 4629
"b"

D:\prac2>git cat-file -p ee94
"a"

D:\prac2>git ls-files -s
100644 ee946e553bd40581abcec7addcb70facc6019299 0       file1.txt
100644 462948753a5dda77be908e15a176c39eeb17552e 0       file2.txt

D:\prac2>git commit -m "Initial commit"
[main (root-commit) 0dbd4e6] Initial commit
 2 files changed, 2 insertions(+)
 create mode 100644 file1.txt
 create mode 100644 file2.txt

D:\prac2>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC2\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   HEAD
│   index
│
├───hooks
│       applypatch-msg.sample
│       commit-msg.sample
│       fsmonitor-watchman.sample
│       post-update.sample
│       pre-applypatch.sample
│       pre-commit.sample
│       pre-merge-commit.sample
│       pre-push.sample
│       pre-rebase.sample
│       pre-receive.sample
│       prepare-commit-msg.sample
│       push-to-checkout.sample
│       sendemail-validate.sample
│       update.sample
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
│   ├───0d
│   │       bd4e6bd9c6a5b258151587ed95cfd18767d7fd
│   │
│   ├───46
│   │       2948753a5dda77be908e15a176c39eeb17552e
│   │
│   ├───a2
│   │       fae7a75d6e57cbec5da287395f13fe033454c2
│   │
│   ├───ee
│   │       946e553bd40581abcec7addcb70facc6019299
│   │
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags


D:\prac2>git cat-file -p 0dbd
tree a2fae7a75d6e57cbec5da287395f13fe033454c2
author MissCheny <1312808428@qq.com> 1754538398 +0800
committer MissCheny <1312808428@qq.com> 1754538398 +0800

Initial commit

D:\prac2>git cat-file -p a2fa
100644 blob ee946e553bd40581abcec7addcb70facc6019299    file1.txt
100644 blob 462948753a5dda77be908e15a176c39eeb17552e    file2.txt

D:\prac2>git cat-file -t a2fa
tree

D:\prac2>git cat-file -t 0dbd
commit
```

```cmd
D:\prac2>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
    file1.txt
    file2.txt

No subfolders exist


D:\prac2>type file1.txt
"a"

D:\prac2>type file2.txt
"b"

D:\prac2>echo "c" > file2.txt

D:\prac2>git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   file2.txt

no changes added to commit (use "git add" and/or "git commit -a")

D:\prac2>tree /f
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:.
    file1.txt
    file2.txt

No subfolders exist


D:\prac2>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC2\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   HEAD
│   index
│
├───hooks
│       applypatch-msg.sample
│       commit-msg.sample
│       fsmonitor-watchman.sample
│       post-update.sample
│       pre-applypatch.sample
│       pre-commit.sample
│       pre-merge-commit.sample
│       pre-push.sample
│       pre-rebase.sample
│       pre-receive.sample
│       prepare-commit-msg.sample
│       push-to-checkout.sample
│       sendemail-validate.sample
│       update.sample
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
│   ├───0d
│   │       bd4e6bd9c6a5b258151587ed95cfd18767d7fd
│   │
│   ├───46
│   │       2948753a5dda77be908e15a176c39eeb17552e
│   │
│   ├───a2
│   │       fae7a75d6e57cbec5da287395f13fe033454c2
│   │
│   ├───ee
│   │       946e553bd40581abcec7addcb70facc6019299
│   │
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags

D:\prac2>git add file2.txt

D:\prac2>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\PRAC2\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   HEAD
│   index
│
├───hooks
│       applypatch-msg.sample
│       commit-msg.sample
│       fsmonitor-watchman.sample
│       post-update.sample
│       pre-applypatch.sample
│       pre-commit.sample
│       pre-merge-commit.sample
│       pre-push.sample
│       pre-rebase.sample
│       pre-receive.sample
│       prepare-commit-msg.sample
│       push-to-checkout.sample
│       sendemail-validate.sample
│       update.sample
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
│   ├───0d
│   │       bd4e6bd9c6a5b258151587ed95cfd18767d7fd
│   │
│   ├───19
│   │       0c5e32531f3716e08e460511c466410504c83f
│   │
│   ├───46
│   │       2948753a5dda77be908e15a176c39eeb17552e
│   │
│   ├───a2
│   │       fae7a75d6e57cbec5da287395f13fe033454c2
│   │
│   ├───ee
│   │       946e553bd40581abcec7addcb70facc6019299
│   │
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags

D:\prac2>git cat-file -p 190c5e3
"c"

D:\prac2>git ls-files -s
100644 ee946e553bd40581abcec7addcb70facc6019299 0       file1.txt
100644 190c5e32531f3716e08e460511c466410504c83f 0       file2.txt

D:\prac2>git commit -m "second commit"
[main 4e2d5f9] second commit
 1 file changed, 1 insertion(+), 1 deletion(-)

D:\prac2>git cat-file -p 4e2d5f9
tree 92a776312b2b0c41bd9da04d2ae5ce43b4a95ab0
parent 0dbd4e6bd9c6a5b258151587ed95cfd18767d7fd
author MissCheny <1312808428@qq.com> 1754549635 +0800
committer MissCheny <1312808428@qq.com> 1754549635 +0800

second commit

D:\prac2>git cat-file -p 92a7763
100644 blob ee946e553bd40581abcec7addcb70facc6019299    file1.txt
100644 blob 190c5e32531f3716e08e460511c466410504c83f    file2.txt

D:\prac2>git cat-file -p 0dbd4e6
tree a2fae7a75d6e57cbec5da287395f13fe033454c2
author MissCheny <1312808428@qq.com> 1754538398 +0800
committer MissCheny <1312808428@qq.com> 1754538398 +0800

Initial commit
```