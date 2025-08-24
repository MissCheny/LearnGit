```cmd
D:\>mkdir learngit

D:\>cd learngit

D:\learngit>dir
 Volume in drive D is Data
 Volume Serial Number is C498-F61E

 Directory of D:\learngit

2025/08/19  下午 12:30    <DIR>          .
               0 File(s)              0 bytes
               1 Dir(s)  181,616,619,520 bytes free

D:\learngit>git init
Initialized empty Git repository in D:/learngit/.git/

D:\learngit>(echo Git is a version control system. & echo Git is free software.) > readme.txt

D:\learngit>type readme.txt
Git is a version control system.
Git is free software.

D:\learngit>git add readme.txt

D:\learngit>git commit -m "wrote a readme file"
[main (root-commit) 9a20565] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt

D:\learngit>(echo Git is a distributed version control system. & echo Git is free software.) > readme.txt

D:\learngit>type readme.txt
Git is a distributed version control system.
Git is free software.

D:\learngit>git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

D:\learngit>git diff readme.txt
diff --git a/readme.txt b/readme.txt
index 4c95930..a14450e 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.

D:\learngit>git add readme.txt

D:\learngit>git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   readme.txt


D:\learngit>git commit -m "add distributed"
[main 5c50446] add distributed
 1 file changed, 1 insertion(+), 1 deletion(-)

D:\learngit>git status
On branch main
nothing to commit, working tree clean

D:\learngit>(echo Git is a distributed version control system. & echo Git is free software distributed under the GPL.) > readme.txt

D:\learngit>type readme.txt
Git is a distributed version control system.
Git is free software distributed under the GPL.

D:\learngit>git commit -am "append GPL"
[main 6fdf424] append GPL
 1 file changed, 1 insertion(+), 1 deletion(-)

D:\learngit>git mylog
* 6fdf424 (56 seconds ago) append GPL  (HEAD -> main)
* 5c50446 (4 minutes ago) add distributed
* 9a20565 (10 minutes ago) wrote a readme file
```