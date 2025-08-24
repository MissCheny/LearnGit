# <center><code>git switch</code></center>
### 一、基本用法

<table><tr><td style='vertical-align:top'>

1. **切换到现有分支**

   ```bash
   git switch featue
   ```

</td><td style='vertical-align:top'>

2. **创建并切换到新分支**

   ```bash
   git switch -c new-feature
   ```

</td><td style='vertical-align:top'>

3. **从某个提交创建并切换到新分支**

   ```bash
   git switch -c new-feature a1b2c3d
   ```

</td></tr></table>

### 三、注意事项

- **分离头指针状态**：`git switch` 不会直接进入分离头指针状态。若要检出特定提交，仍需使用 `git checkout`。
   > HEAD处于分离状态

  ```bash
  git checkout a1b2c3d  # 进入分离头指针状态
  ```