- git commit --amend
> 修改上一次提交，将两次提交合并为一次提交。如果上次的提交信息不满意，也可以用此命令。

- git rebase -i HEAD~3
> 此命令可用于合并提交，修改提交信息，丢弃提交等等。如果有多个提交信息都需要修改的时候，会有一个队列的概念，比如第一个edit过程，在执行完git commit --amend和git rebase --continue之后，就会进入第二个edit过程
```
pick：保留该commit（缩写:p）
reword：保留该commit，但我需要修改该commit的注释（缩写:r）
edit：保留该commit, 但我要停下来修改该提交(不仅仅修改注释)（缩写:e）
squash：将该commit和前一个commit合并（缩写:s）
fixup：将该commit和前一个commit合并，但我不要保留该提交的注释信息（缩写:f）
exec：执行shell命令（缩写:x）
drop：我要丢弃该commit（缩写:d）
```

- git push origin local_branch:remote_branch
> 当没有远程分支时，该指令会自动创建一个远程分支。如果local_branch为空，则该指令会删除远程分支remote_branch。


- git reabse  \<branch\>
> 合并分支
```
解决冲突：
使用git add <file-name>来标记冲突已解决，然后执行git rebase --continue继续。
如果中间遇到某个补丁不需要应用，可以用下面命令忽略：
git rebase --skip
如果想回到rebase执行之前的状态，可以执行：
git rebase --abort
```