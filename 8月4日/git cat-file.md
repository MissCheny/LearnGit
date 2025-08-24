<table>
<tr>
<td style="vertical-align: top;">

```Bash
$ git commit -m "first commit"
[main (root-commit) 1608b19] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 file.txt
```

```powershell
objects
   ├───14162d（tree）
   ├───1608b1（commit）
   └───789819（以blob类型存储的文件内容blob）
```

```powershell
>git cat-file -t 1608b1
commit

>git cat-file -p 1608b1
tree 14162d6c68b9fe5a7ffd21108888bfe66c92f948
author MissCheny <1312808428@qq.com> 1754284999 +0800
committer MissCheny <1312808428@qq.com> 1754284999 +0800

first commit


>git cat-file -t 14162d
tree

>git cat-file -p 14162d
100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    file.txt
```

</td>
<td style="vertical-align: top;">

1. **Blob 对象**:
   - Blob 是 Git 中表示文件内容的一种对象。
   - `789819` 是一个 Blob 对象，其内容是简单的字符 `a`。

2. **Tree 对象**:
   - Tree 对象表示目录结构，它记录了文件（blob）和子目录（其他 tree）的信息。
   - `14162d` 是一个 Tree 对象，它描述了一个目录结构，其中包含一个文件 `file.txt`。这个文件的内容是由 `789819` 这个 Blob 对象提供的。

3. **Commit 对象**:
   - Commit 对象记录了某一时刻的快照，它指向一个 Tree 对象，表示在这个提交时刻的文件目录结构。
   - `1608b1` 是一个 Commit 对象。这个提交对象指向的 `tree` 的 SHA-1 哈希值是 `14162d`，这意味着这个提交保存的文件目录结构是由 `14162d` 这个 Tree 对象表示的。
   - 同时，Commit 对象还包含了作者、提交者的信息，以及提交时的注释。

简单来说，这些对象之间的关系是：
- **Blob** 存储文件的实际内容。
- **Tree** 存储文件和子目录的结构信息，它引用 Blob 对象来存储文件内容。
- **Commit** 存储一个特定的更改快照，它指向一个 Tree 对象来描述这个快照的文件目录结构。

因此，`14162d` 是一个 Tree 对象，它描述了一个目录结构，其中包含 `file.txt` 文件；而 `1608b1` 是一个 Commit 对象，它指向 `14162d` 这个 Tree 对象，并记录了这个提交的元数据（如作者、时间、提交信息等）。


</td>
</tr>
</table>

---


<table>
<tr>
<td style="vertical-align: top;">

```powershell
objects
   ├───14162d（tree）
   ├───1608b1（commit）
   └───789819（blob）
```
**commit → tree → blob**
</td>
<td style="vertical-align: top;">

`789819` **(Blob)**
- `-p` 内容是文件内容 `a`

    ```powershell
    a
    ```

`14162d` **(Tree)**
- `-p` 内容是指向 `789819` 的指针

    ```powershell
    100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    file.txt
    ```

`1608b1` **(Commit)**
- `-p` 内容是指向 `14162d` 的指针，并记录了提交信息

    ```powershell
    tree 14162d6c68b9fe5a7ffd21108888bfe66c92f948
    author MissCheny <1312808428@qq.com> 1754284999 +0800
    committer MissCheny <1312808428@qq.com> 1754284999 +0800

    first commit
    ```
</td>
</tr>
</table>