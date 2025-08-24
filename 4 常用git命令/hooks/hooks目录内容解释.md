<table><tr><td style='vertical-align:top;'>

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

1. **applypatch-msg.sample**  
   用于补丁应用操作，在应用补丁时验证提交信息格式（较少使用）

2. **commit-msg.sample**  
   在提交消息被创建后触发，常用于验证/修改提交信息格式（重要）

3. **fsmonitor-watchman.sample**  
   文件系统监控集成，用于加速Git操作（高级优化用途）

4. **post-update.sample**  
   服务端 hook，在仓库接收 push 后触发（常用于CI/CD）

5. **pre-applypatch.sample**  
   应用补丁前的检查（较少使用）

6. **pre-commit.sample**  
   提交前触发，用于运行测试/代码检查（最常用）⭐

7. **pre-merge-commit.sample**  
   合并提交前的检查（较少使用）

8. **pre-push.sample**  
   在 push 前触发，用于运行集成测试（重要）⭐

9. **pre-rebase.sample**  
   变基操作前的检查（中级使用场景）

10. **pre-receive.sample**  
    服务端 hook，在接收 push 前验证（企业级部署重要）

11. **prepare-commit-msg.sample**  
    提交消息编辑器打开前触发，用于自动生成提交模板

12. **push-to-checkout.sample**  
    服务端 push 同步机制（高级部署使用）

13. **sendemail-validate.sample**  
    邮件补丁发送验证（特殊工作流使用）

14. **update.sample**  
    服务端按分支验证 push（企业级权限控制）

</td></tr></table>


### 推荐学习路径
#### 第一阶段：基础必备
1. **pre-commit**  
   - 学习编写代码规范检查（ESLint）
   - 自动运行单元测试
   - 防止提交调试代码（如console.log）

2. **commit-msg**  
   - 强制遵守提交信息规范（如 Conventional Commits）
   - 示例：`/^[feat|fix|docs|style|refactor|test|chore]\(.*\): .{5,50}/`

3. **pre-push**  
   - 运行集成测试
   - 检查代码覆盖率
   - 重要保护机制的最后防线

#### 第二阶段：进阶使用
1. **prepare-commit-msg**  
   - 自动生成提交模板
   - 关联issue追踪系统（如JIRA ID）

#### 第三阶段：特殊场景
1. **pre-rebase**  
   - 防止危险操作   - 记录变基日志