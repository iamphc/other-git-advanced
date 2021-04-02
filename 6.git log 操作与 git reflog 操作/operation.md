[toc]

### 概念👩‍🦲
[git log](https://git-scm.com/docs/git-log)

[git reflog](https://git-scm.com/docs/git-reflog)

### 常用操作👨‍🦲
**这两个命令的参数都比较多，请自行查阅**

*** 

- 显示提交日志
```
git log 
```

- 常用参数（从使用频率由高到低排序）
```
// 每个提交一行显示，以下两个略有不同
--online 
--pretty=oneline

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

***

- 显示提交日志+**被删除的commit记录和reset记录**
```
git reflog
```

- 常用参数
```
// 自行查阅
```

***

### 两者的比较

||git log|git reflog|
|---|---|---|
|存在的所有记录|☑️|☑️|
|被删除的commit记录|❌|☑️|
|被删除的reset记录|❌|☑️|

### 常见实际操作 & 碰到的问题说明👨‍🦲

- 场景一：需要进行git reset / git cherry-pick操作。在这之前，我们需要获取相关的<commitHASH>
```
git log [--oneline]
```

- 场景二：需要查看某个人（往往是自己，因为记不住🐶）的提交记录
```
git log --author=panghaidhuan [--oneline]
```

- 场景三：需要查看某个人删除的commit或者reset记录
```
git reflog --author=panghaichuan [--oneline]
```