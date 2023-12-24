如果仓库只有一个提交即root提交(?最新提交算吗)
```shell
git rebase -i --root
```

使用步长rebase
```shell
git rebase -i HEAD~1
```

修改commit信息
```shell
//使用系统设置好的
git commit --amend --reset-author
//使用手动设置的
git commit --amend --author="otheruser <otheremail@github.com>"
```

提交rebase
```shell
git rebase --continue
```

再次进入rebase交互

```shell
git rebase --continue-todo
```
撤销此次rebase
```shell
git rebase --abort
```