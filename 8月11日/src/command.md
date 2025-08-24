```cmd
D:\>cd prac

D:\prac>cd ..

D:\>mkdir learngit && cd learngit

$ git init
    Initialized empty Git repository in D:/learngit/.git/

$ echo Git is a version control system. > readme.txt
$ echo Git is free software. >> readme.txt

$ type readme.txt
    Git is a version control system.
    Git is free software.

$ git add readme.txt

$ git commit -m "wrote a readme file"
    [main (root-commit) e0d376a] wrote a readme file
    1 file changed, 2 insertions(+)
    create mode 100644 readme.txt
```

```cmd
$ git status
    On branch main
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
            modified:   readme.txt

    no changes added to commit (use "git add" and/or "git commit -a")

$ git diff readme.txt
    diff --git a/readme.txt b/readme.txt
    index 00b29f3..f3a3fd1 100644
    --- a/readme.txt
    +++ b/readme.txt
    @@ -1,2 +1,2 @@
    -Git is a version control system.
    +Git is a distributed version control system.
    Git is free software.

$ git mylog
    * e0d376a (49 minutes ago) wrote a readme file  (HEAD -> main)

$ git add readme.txt

$ git status
    On branch main
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
            modified:   readme.txt

$ git commit -m "add distributed"
    [main b8edab1] add distributed
    1 file changed, 1 insertion(+), 1 deletion(-)

$ git status
    On branch main
    nothing to commit, working tree clean
```