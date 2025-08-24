假设我们有一个简单的目录结构如下：

```
项目目录/
├── 文件1.txt
├── 文件2.txt
└── 子目录/
    └── 文件3.txt
```

<table><tr><td style='vertical-align:top; width:50%'>

### 执行 `git add *`
```bash
git add *
```

```
项目目录/
├── 文件1.txt (已暂存)
├── 文件2.txt (已暂存)
└── 子目录/ (未暂存)
    └── 文件3.txt (未暂存)
```

不暂存子目录，及子目录下的文件

</td><td style='vertical-align:top;'>

### 执行 `git add ./`

```bash
git add ./
```

```
项目目录/
├── 文件1.txt (已暂存)
├── 文件2.txt (已暂存)
└── 子目录/ (已暂存)
    └── 文件3.txt (已暂存)
```

全部暂存

</td></tr></table>