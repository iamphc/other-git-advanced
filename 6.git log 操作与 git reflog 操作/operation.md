[toc]

### 概念👩‍🦲
[git log](https://git-scm.com/docs/git-log)
[git reflog](https://git-scm.com/docs/git-reflog)

### 常用操作👨‍🦲
**参数比较多，请自行查阅**

*** 

- 显示提交日志
```
git log 
```

- 常用参数（从使用频率由高到低排序）
```
// 每个提交一行显示
--online 

// 显示作者为author的所有提交
--author=<author>
--committer=<author>

// 限制显示的日志数量
-number / -n <number> / --max-count=<number>

// 从最新提交开始，跳过指定个数的提交
--skip=<number>

// 显示在某个提交之前的所有提交
--until=<date>
--before=<date>

// 显示在某个提交之前的所有提交
--since=<date>
--after=<date>

// 其他参数，请自行查阅
```

- 
```
git reflog
```

- 常用参数
```
```

### 常见实际操作 & 碰到的问题说明👨‍🦲

- 场景一：需要进行git reset / git cherry-pick操作。在这之前，我们需要获取相关的<commitHASH>
```
```

- 场景二：
```
```