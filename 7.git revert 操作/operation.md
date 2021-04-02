[toc]

### 概念👨‍🦲
[git revert](https://git-scm.com/docs/git-revert)

### 基本操作👨‍🦲
请注意：git revert 操作的前提是当前分支clean，没有修改

***

- 
```
git revert
```

### git reset 命令和 git revert 命令的比较
||git reset|git revert|
|---|---|---|
|相同点|都能用来回溯提交|
|提交记录|reset之前的会丢失|不丢失|
|回溯提交的位置|只能从最新的提交开始|可以从任意位置开始|
|操作的安全性|建议使用--soft|建议使用|

### 常见实际操作 & 碰到的问题说明👨‍🦲