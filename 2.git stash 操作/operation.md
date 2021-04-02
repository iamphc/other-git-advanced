[toc]
### 概念👨‍🦲
[git stash](https://git-scm.com/docs/git-stash)

### 常用的基本命令👨‍🦲
```
git stash 

git stash save 'stashName'

git stash list

git stash apply 'stashId'

git stash clear

git stash pop ‘stashId’
```

### 常见实际操作 & 碰到的问题说明👨‍🦲
- git stash会暂存工作目录中的更改，并清空当前工作目录中的更改
```
git stash
```
- git stash pop ‘stashId’会应用stash堆栈中的顶部记录，并将它从顶部清除
```
git stash pop
```
- 暂存工作目录中的更改、并应用某个stash堆栈中的记录
```
git stash / git stash save 'name'
git stash list
git stash apply 'id'
```
- git stash -u可以暂存未跟踪的文件
```
git stash save -u
git stash save --include-untracked
```

- git stash 可以用于更新当前分支，预先处理冲突的场景
```
git checkout 主分支
git pull 
git checkout 自己分支
git stash save name
git merge 主分支
git stash apply id
// 情况一：提示代码有冲突,在编辑器/ide中处理冲突
// 情况二：一切正常
```