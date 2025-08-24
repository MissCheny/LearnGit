### `git commit --amend` 内部结构

<table>
<tr><td style='vertical-align:bottom;'>

```bash
$ git mylog
* e595fdb (16 minutes ago) append GPL  (HEAD -> main)
* 262aa9f (17 minutes ago) add distributed
* 5c48241 (17 minutes ago) wrote a readme file
```

</td><td style='vertical-align:top;'>

```bash
$ git commit --amend -m "add GPL"
[main 77a2f0c] add GPL
 Date: Thu Aug 21 13:15:28 2025 +0800
 1 file changed, 1 insertion(+), 1 deletion(-)
```

```bash
$ git mylog
* 77a2f0c (11 seconds ago) add GPL  (HEAD -> main)
* abc24e0 (2 minutes ago) add distributed
* dd1169d (2 minutes ago) wrote a readme file
```

<tr><td style='vertical-align:top;'>

```cmd
D:\LearnGitCommitAmend>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGITCOMMITAMEND\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   HEAD
│   index
│
├───hooks
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
│   ├───41
│   │       1c5c2654fe24749d9c24df848dbebd2a01521f
│   │
│   ├───46
│   │       d49bfabb79a25385fb8f46a0953c22ad2cd6a2
│   │
│   ├───53
│   │       676267be4e4d738fd1e02717f4fbaecdfdc7d1
│   │
│   ├───5a
│   │       fe4901613907cd76aa346a882362bf47ee7fe0
│   │
│   ├───84
│   │       43d230a5fda3c1f1cc18a586a6a860d0a2537b
│   │
│   ├───ab
│   │       c24e0d8235105c34ccab4a52e04566423966e6
│   │
│   ├───c4
│   │       e90dabd35e5f20bbec8610c344871524b78d01
│   │
│   ├───dd
│   │       1169dcff31ebb8d1171a837a74d9bdd0ddca59
│   │
│   ├───e4
│   │       c19d30e909249b9fda123aad08ec8ed4114dce
│   │
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags
```


</td><td style='vertical-align:top;'>

```cmd
D:\LearnGitCommitAmend>tree /f .git
Folder PATH listing for volume Data
Volume serial number is C498-F61E
D:\LEARNGITCOMMITAMEND\.GIT
│   COMMIT_EDITMSG
│   config
│   description
│   FETCH_HEAD
│   HEAD
│   index
│
├───hooks
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
│   ├───41
│   │       1c5c2654fe24749d9c24df848dbebd2a01521f
│   │
│   ├───46
│   │       d49bfabb79a25385fb8f46a0953c22ad2cd6a2
│   │
│   ├───53
│   │       676267be4e4d738fd1e02717f4fbaecdfdc7d1
│   │
│   ├───5a
│   │       fe4901613907cd76aa346a882362bf47ee7fe0
│   │
│   ├───77 (新增)
│   │       a2f0cb04d47a9d22adb03592cfcc955c605818
│   │
│   ├───84
│   │       43d230a5fda3c1f1cc18a586a6a860d0a2537b
│   │
│   ├───ab
│   │       c24e0d8235105c34ccab4a52e04566423966e6
│   │
│   ├───c4
│   │       e90dabd35e5f20bbec8610c344871524b78d01
│   │
│   ├───dd
│   │       1169dcff31ebb8d1171a837a74d9bdd0ddca59
│   │
│   ├───e4
│   │       c19d30e909249b9fda123aad08ec8ed4114dce
│   │
│   ├───info
│   └───pack
└───refs
    ├───heads
    │       main
    │
    └───tags
```

</td></tr></table>