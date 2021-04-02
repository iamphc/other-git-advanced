[toc]

### 概念👨‍🦲
[git revert](https://git-scm.com/docs/git-revert)

### 基本操作👨‍🦲
请注意：
- git revert 操作的前提是当前分支clean，没有修改

***

- 基本
```
git revert
```

- 常用参数
```
// 编辑提交信息。该选项默认
-e / --editor

// 不编辑提交信息
--no-edit

// 通常来说，git revert 操作会创建一个新的commit
// 该选项表示不产生新的提交
-n / --no-commit

// 如果revert的节点是一个两个分支合并的节点。注意，这里的选项与「5.git cherry-pick 操作」的含义相同
// -m：该参数告诉git，应该采用哪个分支的变动
// 参数parent-number：是一个从1开始的整数，代表原始提交的父分支的编号。
// 一般来说，1号父分支是接受变动（被合并）的分支，2号父分支是作为变动来源（合并）的分支
-m parent-number / --mainline parent-number

// 其他选项/参数，自行查阅
```

### git reset 命令和 git revert 命令的比较👨‍🦲
||git reset|git revert|
|---|---|---|
|相同点|都能用来回溯提交|
|提交记录|reset之前的会丢失|不丢失|
|回溯原理|直接将之前的提交从当前分支中删除|产生一个对目标提交的完全的逆反的提交|
|回溯提交的位置|只能从最新的提交开始|可以从任意位置开始|
|操作的安全性|建议使用--soft|建议使用|

### 常见实际操作 & 碰到的问题说明👨‍🦲

- 场景一：开发过程中，发现需要对某个提交的所有文件做一个回撤。但是该提交之后已经有其他新的提交。
```
git revert <commitHASH>
```