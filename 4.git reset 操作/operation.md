[toc]

### 概念👨‍🦲
[git reset](https://git-scm.com/docs/git-reset)

### 常用操作👨‍🦲
- git reset [--soft/hard/mixed/merge/keep] [HEAD^/HEAD~n]

|比较项|soft|hard|mixed|merge|keep|
|---|---|---|---|---|---|
||||默认值|||
|index|❌||||👩‍🦲|
|working-tree|❌|❌|❌|🐒|🐒|

***
- ❌：不变 
- 🐒：更新工作树中<commit>和HEAD之间不同的文件
- 👩‍🦲：重置索引项。如果<commit>和HEAD之间不同的文件有本地更改，则reset被中止。
- index：
- HEAD：
- working-tree：
***

  - 没有给参数，默认是mixed
  - mixed：不改变任何文件，但是对回退到某版本的之前的提交的所有文件，将它们所属的hashid丢掉【不太常用】
  - merge【不太常用】

### 常见实际操作 & 碰到的问题说明👨‍🦲
- 在分支上版本回退
```
// 找到你要回退到的版本：提交的hashid
// 方法一：在gitlab上查询merge request
// 方法二：查询提交日志
git log [--oneline]

// 版本回退
git reset [--soft/--hard] hashid
```