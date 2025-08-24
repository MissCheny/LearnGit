## <center>`git log`  VS `Git reflog`</center>
`git log` 和 `git reflog` 确实看起来有些相似，但它们的设计目的和实际作用有本质区别。以下是主要差异对比（附记忆技巧）：

| 特性                | git log                          | git reflog                          |
|---------------------|----------------------------------|-------------------------------------|
| **作用对象**         | 提交历史（仅存活提交）            | 引用变更记录（包括"死"提交）         |
| **记录范围**         | 当前分支的祖先链                | HEAD和分支指针的所有移动轨迹         |
| **数据保留**         | 永久存储                        | 临时记录（默认90天）                 |
| **典型使用场景**     | 查看项目演进历史                 | 找回被覆盖/删除的提交                |
| **显示格式**         | 完整的提交信息                  | 简写操作记录（包含操作类型）         |
| **重置操作可见性**   | 不显示reset等操作               | 会记录checkout/reset/rebase等操作   |

**记忆技巧**：把`git log`想象成历史博物馆（只展示官方认可的历史），而`git reflog`是监控录像（记录所有发生过的操作）。

**经典使用场景**：
1. 当用 `git reset --hard` 回退后想找回最新提交：
```bash
# 先用reflog找到被覆盖的commit hash
git reflog show
# 再reset回去
git reset --hard HEAD@{1}
```

2. 误删分支时恢复：
```bash
# 通过reflog找到分支最后的位置
git reflog | grep 'moving from' 
# 根据记录重建分支
git branch recovered-branch HEAD@{2}
```

**底层原理**：reflog实际存储在.git/logs/目录下，每个引用（包括HEAD）都有对应的reflog文件，这也是为什么它不受分支切换影响的原因。而git log本质是通过commit对象之间的parent指针遍历历史。