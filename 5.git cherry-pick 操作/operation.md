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
// 详细见「常见实际操作 & 碰到的问题说明👨‍🦲」
git cherry-pick (--continue | --skip | --abort | --quit)
```

### 常见实际操作 & 碰到的问题说明👨‍🦲

**场景一：cherry-pick 过程中发生代码冲突，cherry-pick会停止，让用户决定如何继续操作**

***

- 冲突情况一：解决冲突，继续合并
```
// 第一步：解决冲突
// 第二步：git add .
// 第三步：git cherry-pick --continue
```

- 冲突情况二：放弃合并，回到操作前
```
git cherry-pick --abort
```

- 冲突情况三：退出cherry-pick，但是不会倒操作前的样子
```
git cherry-pick --quit
```

***

**场景二：使用cherry-pick处理merge-request到错误的的目标分支**

- 解决方法一：关闭merge request / 编辑merge request

- 解决方法二：cherry-pick
```
// 第一步：cherry-pick
git checkout 正确的目标分支
git cherry-pick <commitHASH>
// 第二步：解决可能产生的冲突，请参考场景一中的处理方法
```

**场景三：在某分支上修复了bug/增加了需求。但是，需要在新的分支上修复同样的bug/增加同样的需求**
```
```