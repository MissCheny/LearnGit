### 总结流程图
```
工作区修改 → git restore file.txt（撤销工作区改动）
   ↓
git add → git restore -S file.txt（撤销暂存）
   ↓
git commit → git reset HEAD~1（撤销提交）
```

---

```bash
git init && echo 111 > file1.txt && echo 222 > file2.txt && git add . && git commit -m "file123.txt"
```

```bash
rm file1.txt file2.txt
```

```bash
echo 333 > folder1.txt && echo 444 > folder2.txt
```