<table><tr><td style='vertical-align:top; width:30%'>

HEAD 指针指向的哈希值

`git rev-parse HEAD`：
* **rev** → revision（版本）
* **parse** → 解析
* **HEAD** → 当前指针指向的提交

</td><td style='vertical-align:top'>


 **rev-parse HEAD = 解析当前头指针 → 得到提交的哈希值**  
 想象成 **“翻译 HEAD”**，翻译结果就是那串长长的 40 位 SHA-1。

**rev**（版本） **parse**（翻译） **HEAD**（头） → 版本翻译头。

* **version**（版本） → 更偏向一个软件的发布版本（v1.0, v2.0）
* **revision**（修订/修订版） → **某个具体的提交记录（commit）**

</td></tr></table>

---

```bash
git rev-parse HEAD          # 本地当前 HEAD 提交
git rev-parse origin/main   # 远程分支 origin/main 的提交
```