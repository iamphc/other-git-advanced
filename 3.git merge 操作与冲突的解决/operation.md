[toc]

### 概念
[git merge](https://git-scm.com/docs/git-merge)

### 常用操作


### 常见实际操作 & 碰到的问题说明
- 更新主分支代码后，在自己的分支上继续修改
```
git checkout 主分支
git pull
...
git checkout 自己的分支
git merge 主分支 // 为什么这么做？为了立刻解决存在的冲突
// 情况一：有冲突，在编辑器/ide中解决冲突
// 情况二：无冲突
```

- git merge能够解决代码冲突。
通常的冲突标记<<<<<<<和括起来>>>>>>>。
```
// merge request 后，发现有冲突
// 方法一：在gitlab/github上直接解决冲突，适合代码量小的情况
// 方法二：在本地解决冲突，解决之后，再次提交
git checkout 主分支
git pull
git checkout 自己的分支
git pull // 这个地方可有可无，加上，是防止其他人在这个分支上做了新的提交
git merge 主分支
// 提示合并有冲突->在本地编辑器/ide中解决冲突
git add .
git commit // -> 进入vim编辑界面，command / ctrl + x 退出
git push
// 去本地 gitlab 上，发现没有冲突，完成
```