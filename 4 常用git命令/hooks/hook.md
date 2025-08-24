# Question

请帮助我学习git钩子，hook是什么有什么用？

# Answer

>嗯，用户想学习Git钩子，hook是什么，有什么用处。首先，我需要回忆自己了解的Git钩子的知识。记得Git钩子是在特定事件发生时自动运行的脚本，比如提交代码前或者推送后。这些钩子可以用于自动化任务，比如检查代码风格、运行测试，或者在提交信息不规范时阻止提交。
>
>用户可能刚开始接触Git，所以需要从基础讲起。首先解释什么是钩子，然后举一些常见的例子。可能需要区分客户端钩子和服务端钩子的不同，客户端钩子比如pre-commit，服务端比如pre-receive。然后说明它们的用途，比如自动化测试、代码检查、部署等。
>
>用户可能想知道如何创建和使用钩子，所以应该提到.git/hooks目录下的示例脚本，如何将它们改为可执行文件，或者使用工具像Husky来管理。另外，可能需要提醒用户，钩子默认不保存在版本库中，所以如何共享钩子可能需要额外的方法，比如放在项目中的某个目录然后通过脚本链接。
>
>还要考虑用户的实际使用场景，比如他们可能想用钩子来规范团队代码，或者在部署时自动触发某些流程。可能存在的误区是钩子被绕过的情况，比如使用--no-verify选项跳过pre-commit钩子，这时候需要说明注意事项。
>
>最后，总结一下Git钩子的作用，强调自动化和规范流程的好处，同时提到一些常见的使用案例，让用户更容易理解如何应用到自己的项目中。
>

Git Hook（钩子）是Git版本控制系统中一种自动化工具，允许你在特定事件（如提交代码、推送代码等）发生时触发自定义脚本。它的核心作用是**自动化流程**和**规范开发行为**，帮助团队提高代码质量和开发效率。

---

### **Git Hook 是什么？**
- **本质**：存储在 `.git/hooks` 目录下的可执行脚本文件（Shell、Python、Node.js等均可）。
- **触发时机**：当Git操作（如提交、合并、推送等）到达某个关键节点时，自动触发对应钩子。
- **分类**：
  - **客户端钩子**（本地操作触发，如提交代码时）
  - **服务端钩子**（远程仓库操作触发，如推送代码到服务器时）

---

### **常见钩子及用途**
#### 1. 客户端钩子（常用）

<table><tr><td style='vertical-align:top; width:310px;'>

```cmd
├───hooks
│       applypatch-msg.sample
│       commit-msg.sample
│       fsmonitor-watchman.sample
│       post-update.sample
│       pre-applypatch.sample
│       pre-commit.sample
│       pre-merge-commit.sample
│       pre-push.sample
│       pre-rebase.sample
│       pre-receive.sample
│       prepare-commit-msg.sample
│       push-to-checkout.sample
│       sendemail-validate.sample
│       update.sample
```

</td><td style='vertical-align:top;'>

- **`pre-commit`**  
  - **触发时机**：输入 `git commit` 后，代码提交前  
  - **用途**：检查代码格式（如 ESLint）、运行单元测试、阻止包含`TODO`的提交  
  - **示例**：若测试未通过，提交会被终止

- **`commit-msg`**  
  - **触发时机**：提交信息输入后  
  - **用途**：校验提交信息格式（如必须包含JIRA任务号）  
  - **示例**：强制要求提交信息符合 `fix: 描述` 的规范

- **`post-commit`**  
  - **触发时机**：提交完成后  
  - **用途**：通知CI/CD、发送提醒邮件等后续操作

#### 2. 服务端钩子（需部署在Git服务器）
- **`pre-receive`**  
  - **触发时机**：代码推送到远程仓库前  
  - **用途**：检查提交是否符合规则（如禁止强制推送）

- **`post-receive`**  
  - **触发时机**：代码推送完成后  
  - **用途**：自动部署到生产环境、触发CI/CD流水线

</tr></td></table>

---

### **如何使用Git Hook？**
1. **找到钩子目录**：进入项目根目录的 `.git/hooks`，会看到示例文件（如`pre-commit.sample`）
2. **创建钩子**：移除`.sample`后缀，编写脚本内容并设为可执行权限  
   ```bash
   cp pre-commit.sample pre-commit  # 复制示例文件
   chmod +x pre-commit              # 添加执行权限
   ```
3. **编写脚本**（以`pre-commit`为例）：
   ```bash
   #!/bin/sh
   # 运行ESLint检查
   npm run lint
   if [ $? -ne 0 ]; then
     echo "代码格式错误，提交终止！"
     exit 1
   fi
   ```

---

### **最佳实践**
- **使用工具简化管理**：  
  - [Husky](https://github.com/typicode/husky)（Node.js项目）  
  - [pre-commit](https://pre-commit.com/)（Python项目）
- **共享钩子**：默认钩子不提交到Git仓库，可通过工具或项目目录统一管理
- **注意灵活性**：可通过 `git commit --no-verify` 跳过钩子（慎用！）

---

### **应用场景**
1. **代码规范**：自动格式化代码、检测语法错误  
2. **流程管控**：禁止直接提交到`master`分支  
3. **自动化部署**：推送后自动部署到测试环境  
4. **安全审查**：检查敏感信息（如密码）是否被误提交

通过合理使用Git Hook，你可以将重复性工作自动化，同时确保团队遵循统一的开发规范。