_# 合并分支_

git merge <分支名>

_# 变基操作_

git rebase <分支名>

_# 拉取远程更新_

git pull

_# 推送到远程_

git push

_# 推送到指定远程分支_

git push origin <分支名>

_# 撤销工作区修改_

git checkout -- <文件名>

_# 撤销暂存区修改_

git reset HEAD <文件名>/.

_# 撤销commit提交_
撤销 commit，代码保留在暂存区	git reset --soft HEAD~1
撤销 commit，代码保留在工作区（未暂存）	git reset HEAD~1
撤销 commit，同时丢弃代码改动	git reset --hard HEAD~1 ⚠️

git stash 把当前工作区（和索引）里所有未提交的改动先藏起来
git stash pop 把最近一次藏的东西拿回来，并从 stash 列表里删除
git stash apply stash@{1}  git stash pop stash@{1}
git reset --merge 撤销pop
git stash list
先 git stash apply（只恢复不删除），看效果；没问题再 git stash drop stash@{n}删除
git fsck --lost-found 撤销drop


_# 撤销到某一HEAD版本_
git reflog -num
git reset --hard HEAD@{n}





输入station ID 前端校验->无效
                     ->检查 station 状态-》校验通过-》输入staffID 
                                      -》不通过-》station ID不存在报错
                                              =》station被占用-》弹窗 此包装站正在进行会话。恢复会话？=》cancle-> 输入staffID 
                                                                                              =》confirm->切换页面

