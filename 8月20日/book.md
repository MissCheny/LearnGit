Most, but not all, Git commands that require the revision parameter, default to using HEAD. For example, git log and git log HEAD will show the same information.

大多数（但不是全部）需要修订参数的Git命令默认使用HEAD。例如，git log和git log HEAD将显示相同的信息。

---

The HEAD denotes the current branch, or in other words the commit that was checked out into the working directory, and forms a base of a current work.

HEAD表示当前分支，或者换句话说，表示被检出到工作目录的提交，并构成当前工作的基础

---
During a merge, before creating a merge commit, the MERGE_HEAD records the commit(s) that you are merging into your branch. It vanishes after creating a merge commit.During a cherry-pick, before creating a commit that copies picked changes into another branch, the CHERRY_PICK_HEAD records the commit that you have selected for cherry-picking.

在合并过程中，在创建合并提交之前，MERGE_HEAD记录了你合并到当前分支的提交。在创建合并提交之后，它就消失了。在 cherry-pick 过程中，在创建将所选更改复制到另一个分支的提交之前，CHERRY_PICK_HEAD 记录了你选择进行 cherry-pick 的提交。

---

ORIG_HEAD：  
记录当前分支的上一个位置；这个引用是通过移动当前分支的命令（创建一个新的提交不会设置ORIG_HEAD）来创建的，用于记录HEAD命令在操作前的位置。如果你想撤销或终止这样的操作，它非常有用；尽管现在可以使用reflogs来完成同样的事情，它们存储了额外的信息，可以在使用时进行检查。