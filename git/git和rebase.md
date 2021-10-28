### 用法
git rebase/merge B 都是将B分支合并到当前分支

### 解决冲突
- rebase
  - 修改冲突
  - git add
  - git rebase --continue/ --skip
  - git rebase --abort 终止合并，并回到合并前状态
遇到冲突后，解决完, 再次提交，merge 是需要一个commit，而rebase没有重复的提交

如果要求git log查看的更好，用merge(不会合并提交的历史记录),rebase 会把B分支的提交记录都会合并到当前分支



