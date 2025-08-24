## 疑问由来
<table><tr><td style='width:30%';>

这里的 **commit对象** 指向<br> **1个tree对象** 和 **1个parent对象**

</td><td>

```bash
$ git commit -m "second commit"
    [main a1083fc] second commit
    1 file changed, 1 insertion(+), 1 deletion(-)

$ git cat-file -t a1083fc
    commit

$ git cat-file -p a1083fc
    tree 9e96e773eadd7f038e14d7d426a3e3aee3ae32e5     ( tree[新] )
    parent 1608b1978e3442ee36ffec630d46d5f9b6000b7a   (commit[旧] )
    author MissCheny <1312808428@qq.com> 1754456691 +0800
    committer MissCheny <1312808428@qq.com> 1754456691 +0800
    second commit
```

</td></tr></table>


## 关于 commit 对象的 parent 指针说明
在 Git 中，commit 对象的 parent 指针通常指向另一个 commit 对象。这是因为在 Git 的提交历史中，每个 commit 都代表了一个项目的快照，并且通常是从一个已有的 commit 基础上进行修改而产生的。

然而，在某些特殊情况下，commit 可能 **没有parent**，或者 **有多个parent**的情况：

| <center>特殊情况</center> | <center>parent 指针</center> | 
| --- | --- | 
| 初始提交（Initial Commit） |commit 对象的 **没有parent** 指针 | 
| 合并提交（Merge Commit） |commit 对象的 **有多个parent** 指针 | 

## 用命令执行验证
### 一、验证初始提交
假设我有一个新的 Git 仓库，可以按照以下步骤验证初始提交没有父 commit：

<table><tr><td style='vertical-align:top;'>

1. 创建并初始化 Git 仓库：
    ```bash
    $ mkdir test_repo
    $ cd test_repo
    $ git init
    ```

</td><td style='vertical-align:top;'>

2. 创建文件并提交：
    ```bash
    $ echo "Hello, World!" > README.md
    $ git add README.md
    $ git commit -m "Initial commit"
    ```

</td><td style='vertical-align:top;'>

3. 查看 commit 对象的详细信息：
    ```bash
    $ git cat-file -p HEAD
        tree <tree-hash>
        author Your Name <your.email@example.com> <timestamp> <timezone>
        committer Your Name <your.email@example.com> <timestamp> <timezone>
        Initial commit
    ```

    你会发现，初始提交没有 `parent` 字段。

</td></tr></table>

### 二、验证合并提交
假设你有两个分支并进行合并，可以按照以下步骤验证合并提交有两个 parent：

1. 创建一个新的分支并进行一些修改：
    ```bash
    $ git checkout -b feature
    $ echo "Feature branch" >> README.md
    $ git add README.md
    $ git commit -m "Add feature branch content"
    ```

2. 切换回主分支并进行一些不同的修改：
    ```bash
    $ git checkout main
    $ echo "Main branch" >> README.md
    $ git add README.md
    $ git commit -m "Add main branch content"
    ```

3. 合并 feature 分支到 main 分支：
    ```bash
    $ git merge feature
    ```

4. 查看合并提交的详细信息：
    ```bash
    $ git cat-file -p HEAD
        tree <tree-hash>
        parent <main-branch-commit-hash>
        parent <feature-branch-commit-hash>
        author Your Name <your.email@example.com> <timestamp> <timezone>
        committer Your Name <your.email@example.com> <timestamp> <timezone>
        Merge branch 'feature' into main
    ```

    你会看到合并提交有两个 `parent` 字段，分别指向主分支和 feature 分支的最新 commit。