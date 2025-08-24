## 实际开发案例
通过实际开发案例来解释 `git commit --amend` 和 `git reset` 的使用会更加直观。下面是一些具体的场景：

## <center>`git commit --amend`</center>

### 案例1：修改提交信息

<table><tr><td style='vertical-align:top;'>

提交了一次更改，并且提交信息写错了：

```
commit 3f2a4b9 (HEAD -> main)
Author: 你
Date:   10 minutes ago

    添加了用户登录功能，但信息写错了

commit 2a1b3c8
Author: 你
Date:   2 hours ago

    完成了页面布局
```

</td><td style='vertical-align:top;'>

使用 `git commit --amend` 来修改最近一次提交的提交信息：

```sh
git commit --amend
```

这会打开默认的文本编辑器，让你修改提交信息。修改后的提交信息如下：

```
commit 3f2a4b9 (HEAD -> main)
Author: 你
Date:   10 minutes ago

    添加了用户登录功能
```

</td></tr></table>

---

### 案例2：添加遗漏的文件

<table><tr><td style='vertical-align:top;'>
已经提交了一次更改，但是发现遗漏了一个文件：

```
commit 3f2a4b9 (HEAD -> main)
Author: 你
Date:   10 minutes ago

    添加了用户登录功能

commit 2a1b3c8
Author: 你
Date:   2 hours ago

    完成了页面布局
```

</td><td style='vertical-align:top;'>

你可以先添加遗漏的文件到暂存区：

```sh
git add login.js
```

然后使用 `git commit --amend` 来修改最近一次提交，将遗漏的文件添加进去：

```sh
git commit --amend
```

这会将 `login.js` 添加到最近一次提交中。你可以选择不修改提交信息，直接保存并关闭编辑器。

</td></tr></table>

---

### 案例3：修改最近一次提交中的文件内容

<table><tr><td style='vertical-align:top;'>

假设你已经提交了一次更改，但是发现某个文件的修改不正确。你的提交历史如下：

```
commit 3f2a4b9 (HEAD -> main)
Author: 你
Date:   10 minutes ago

    添加了用户登录功能

commit 2a1b3c8
Author: 你
Date:   2 hours ago

    完成了页面布局
```

</td><td style='vertical-align:top;'>

你可以先修改文件内容：

```sh
# 修改 login.js 文件
vim login.js
```

然后将修改后的文件添加到暂存区：

```sh
git add login.js
```

接着使用 `git commit --amend` 来修改最近一次提交中的文件内容：

```sh
git commit --amend
```

这会将 `login.js` 的修改应用到最近一次提交中。你可以选择不修改提交信息，直接保存并关闭编辑器。

</td></tr></table>


## <center>`git reset`</center>

### 案例1：撤销最近一次提交但保留工作目录中的修改

<table><tr><td style='vertical-align:top;'>

假设你已经提交了一次更改，但是发现提交的内容有误，并且你希望保留所做的修改以便进一步修改。你的提交历史如下：

```
commit 3f2a4b9 (HEAD -> main)
Author: 你
Date:   10 minutes ago

    添加了用户登录功能，但内容有误

commit 2a1b3c8
Author: 你
Date:   2 hours ago

    完成了页面布局
```

</td><td style='vertical-align:top;'>

你可以使用 `git reset --mixed HEAD~1` 来撤销最近一次提交，但保留所做的修改：

```sh
git reset --mixed HEAD~1
```

这会将 HEAD 指针移动到前一个提交，并且重置暂存区，但是工作目录中的修改仍然存在。你可以重新组织更改，然后创建新的提交：

```sh
git add login.js
git commit -m "添加了正确的用户登录功能"
```

</td></tr></table>

---

### 案例2：彻底丢弃最近一次提交及其所有修改

<table><tr><td style='vertical-align:top;'>

假设你已经提交了一次更改，但是发现提交的内容完全错误，并且你希望彻底丢弃这些修改。你的提交历史如下：

```
commit 3f2a4b9 (HEAD -> main)
Author: 你
Date:   10 minutes ago

    添加了用户登录功能，但内容完全错误

commit 2a1b3c8
Author: 你
Date:   2 hours ago

    完成了页面布局
```

</td><td style='vertical-align:top;'>

你可以使用 `git reset --hard HEAD~1` 来彻底丢弃最近一次提交及其所有修改：

```sh
git reset --hard HEAD~1
```

这会将 HEAD 指针移动到前一个提交，并且重置暂存区和工作目录，丢弃所有未提交的修改。请注意，使用 `git reset --hard` 会永久删除未提交的修改，建议操作前确保重要修改已提交或备份。

</td></tr></table>

---

### 案例3：快速回退到之前的版本状态

<table><tr><td style='vertical-align:top;'>

假设你已经提交了多次更改，但是发现某个之前的版本是正确的，希望快速回退到该版本。你的提交历史如下：

```
commit 4g5h6i7 (HEAD -> main)
Author: 你
Date:   5 minutes ago

    添加了用户登录功能，但内容完全错误

commit 3f2a4b9
Author: 你
Date:   10 minutes ago

    添加了用户登录功能，但内容有误

commit 2a1b3c8
Author: 你
Date:   2 hours ago

    完成了页面布局
```

</td><td style='vertical-align:top;'

你可以使用 `git reset --hard <提交哈希>` 来快速回退到之前的版本状态。例如，回退到 `2a1b3c8`：

```sh
git reset --hard 2a1b3c8
```

这会将 HEAD 指针移动到指定的提交，并且重置暂存区和工作目录，丢弃所有未提交的修改。注意，同样会永久删除未提交的修改，建议操作前确保重要修改已提交或备份。

</td></tr></table>

### 总结

- **`git commit --amend`**：适用于仅需调整最近一次提交的情况，不创建新的提交对象，修改最近一次提交的内容。
- **`git reset`**：适用于撤销提交并根据需要保留或丢弃修改的情况，通过不同的参数可以灵活控制 HEAD 指针、暂存区和工作目录的状态。

在实际开发中，选择合适的命令可以有效地管理和调整提交历史，确保代码库的整洁和一致性。