[toc]

### 概念👨‍🦲
[git cherry-pick](https://git-scm.com/docs/git-cherry-pick)

### 常用操作👨‍🦲
[git cherry-pick](http://www.ruanyifeng.com/blog/2020/04/git-cherry-pick.html)
- 注意：git cherry-pick 操作的前提是你的工作目录干净，没有修改

- 将<commitHASH>这个提交应用当前分支。在当前分支的这个新提交的<commitHASH>会变
```
git checkout 分支名
git cherry-pick <commitHASH>  
```

- 将分支B的最新提交应用到分支A
```
git checkout 分支B
git cherry-pick 分支A
```

- 将多个提交记录应用到当前分支
```
// 写法一：
git checkout 分支名
git cherry-pick <commitHASH-1> <commitHASH-2> ...

// 写法二：
git checkout 分支名
git cherry-pick <commitHASH-old>...<commitHASH-new>

// 写法三：
git checkout 分支名
git cherry-pick <commitHASH-old>^...<commitHASH-new>
```

- 配置项
```
// 打开外部编辑器，编辑提交信息
-e / --editor

// 只更新工作区和暂存取，不产生新的提交
-n / --no-commit

// 会在提交信息的末尾追加一行：“cherry-pick picked from commit ...”，方便以后查到这个提交是如何产生的
-x

// 在提交信息的末尾追加一行操作者的签名，表示是谁进行了这个操作
-s / --signoff

// 如果原始提交是一个合并节点，来自于两个分支的合并，那么cherry-pick默认将失败。因为它不知道应该采用那个分支的代码变动。
// -m：该配置告诉git，应该采用哪个分支的变动。它的参数parent-number，是一个从1开始的整数，代表原始提交的父分支的编号。
// 一般来说，1号父分支是接受变动（被合并）的分支，2号父分支是作为变动来源（合并）的分支
-m parent-number / --mainline parent-number
```

- 相关子操作
```
git cherry-pick (--continue | --skip | --abort | --quit)
```

### 常见实际操作 & 碰到的问题说明👨‍🦲

- cherry-pick 中发生代码冲突，如何处理
```
```