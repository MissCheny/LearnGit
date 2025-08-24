# Question

可能是由于我提交的就只有一个file.txt文件没有子目录，目录结构过于简单以至于我看不出14162d (Tree)的存在有什么意义。 

```powershell
git cat-file -p 14162d
100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    file.txt
```

这是只有一个file.txt文件的`git cat-file -p`命令的返回内容，请你提供复杂点的目录结构的`git cat-file -p`命令的返回内容

# Answer

明白了，你希望看到一个更复杂的目录结构来更好地理解 Tree 对象的作用。下面将展示一个包含多个文件和子目录的复杂项目结构，并提供相应的 `git cat-file -p` 命令输出。

假设我们有一个项目结构如下：

```
prac/
├── README.md
├── src/
│   ├── main.c
│   ├── utils/
│       ├── helper.c
│       └── helper.h
└── include/
    └── config.h
```

我们先将这个项目提交到 Git 仓库中，然后查看相应的 Tree 对象。

### 提交步骤

1. **初始化仓库并添加文件**：
    ```powershell
    D:\prac> git init
    Initialized empty Git repository in D:/prac/.git/

    D:\prac> git add .

    D:\prac> git commit -m "Initial commit"
    [main (root-commit) 1234567] Initial commit
     4 files changed, 10 insertions(+)
     create mode 100644 README.md
     create mode 100644 src/main.c
     create mode 100644 src/utils/helper.c
     create mode 100644 src/utils/helper.h
     create mode 100644 include/config.h
    ```

2. **查看提交对象**：
    ```powershell
    D:\prac> git cat-file -t 1234567
    commit

    D:\prac> git cat-file -p 1234567
    tree 14162d6c68b9fe5a7ffd21108888bfe66c92f948
    author MissCheny <1312808428@qq.com> 1754284999 +0800
    committer MissCheny <1312808828@qq.com> 1754284999 +0800

    Initial commit
    ```

3. **查看根目录的 Tree 对象**：
    ```powershell
    D:\prac> git cat-file -t 14162d6c68b9fe5a7ffd21108888bfe66c92f948
    tree

    D:\prac> git cat-file -p 14162d6c68b9fe5a7ffd21108888bfe66c92f948
    100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    README.md
    100644 blob 14162d6c68b9fe5a7ffd21108888bfe66c92f948    include
    100644 blob 14162d6c68b9fe5a7ffd21108888bfe66c92f948    src
    ```

实际上，Git 的 Tree 对象不会直接指向其他文件或目录的内容，而是指向其他 Tree 对象或 Blob 对象。因此，我们应该看到类似以下的输出：

### 查看根目录的 Tree 对象

```powershell
D:\prac> git cat-file -p 14162d6c68b9fe5a7ffd21108888bfe66c92f948
100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    README.md
040000 tree 87654321fedcba987654321fedcba987654321    include
040000 tree 123456789abcdef123456789abcdef123456    src
```

### 查看 `include` 目录的 Tree 对象

假设 `include` 目录的 Tree 对象的 SHA-1 哈希值是 `87654321fedcba987654321fedcba987654321`：

```powershell
D:\prac> git cat-file -p 87654321fedcba987654321fedcba987654321
100644 blob 987654321fedcba987654321fedcba987654321    config.h
```

### 查看 `src` 目录的 Tree 对象

假设 `src` 目录的 Tree 对象的 SHA-1 哈希值是 `123456789abcdef123456789abcdef123456`：

```powershell
D:\prac> git cat-file -p 123456789abcdef123456789abcdef123456
100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    main.c
040000 tree 54321fedcba987654321fedcba987654321    utils
```

### 查看 `src/utils` 目录的 Tree 对象

假设 `src/utils` 目录的 Tree 对象的 SHA-1 哈希值是 `54321fedcba987654321fedcba987654321`：

```powershell
D:\prac> git cat-file -p 54321fedcba987654321fedcba987654321
100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    helper.c
100644 blob 78981922613b2afb6025042ff6bd878ac1994e85    helper.h
```

### 总结

通过这些命令输出，我们可以看到 Tree 对象是如何组织目录结构的：

- 根目录的 Tree 对象 (`14162d6c68b9fe5a7ffd21108888bfe66c92f948`) 指向 `README.md` 文件的 Blob 对象和两个子目录 `include` 和 `src` 的 Tree 对象。
- `include` 目录的 Tree 对象 (`87654321fedcba987654321fedcba987654321`) 指向 `config.h` 文件的 Blob 对象。
- `src` 目录的 Tree 对象 (`123456789abcdef123456789abcdef123456`) 指向 `main.c` 文件的 Blob 对象和一个子目录 `utils` 的 Tree 对象。
- `src/utils` 目录的 Tree 对象 (`54321fedcba987654321fedcba987654321`) 指向 `helper.c` 和 `helper.h` 文件的 Blob 对象。

这种层次结构使得 Git 能够精确地跟踪文件和目录的变化。即使项目简单，Tree 对象仍然存在，以保持一致性和完整性。在更复杂的项目中，这种结构更为明显和重要。