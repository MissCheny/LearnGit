## <center>`git commit -am` VS `git add . && git commit -m`</cetner>

| 变更类型 (看 `git status`) | 使用 `git commit -am`？ | 使用 `git add . && git commit -m`？ | 说明 |
| :--- | :---: | :---: | :--- |
| **修改 (modified)** 已跟踪文件 | ✅ **可以** | ✅ 也可以 | `-a` 的完美场景 |
| **删除 (deleted)** 已跟踪文件 | ✅ **可以** | ✅ 也可以 | `-a` 的完美场景 |
| **新增 (untracked)** 文件 | ❌ **不行** | ✅ **必须** | **最主要的原因** |
| **重命名 (renamed)** 文件 | ❌ **不行** | ✅ **必须** | Git视作“删除+新增” |
| 只想提交**部分**已修改文件 | ❌ **不行** | ❌ 也不行 | 需用 `git add <file>` 单独添加 |