本地强制上传到远程仓库git push -u origin master -f

git log --oneline

git log -n 3

git log --stat -1

git dif xxx.xx

git config --global alias.st status
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.br branch
git config --global alias.rs reset

git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"

git diff 6f647f79a39 HEAD

git diff 6f647f79a39^!

git log --graph --oneline

git status --short

git reset HEAD    重置暂存区

git reset HEAD blash.txt    将blash移出暂存区

git branch xxx 6f647f79a39





##.gitignore

```
#
#Simple file path
#
somehow/xxx.txt
#
#
#
generated/
#
#
#
*.bak
#
#
#
!demo.bak
```
















##创建裸仓库

裸仓库通常可被用来充当开发者们传递提交的汇聚点，以便其他人可以从中拉回他们所做的修改。

git clone --bare /program/first-steps    创建裸仓库





##工作区与版本库

工作区是一个包含.git子目录（内含版本库）中的目录。用git init命令在当前目录中创建版本库。



git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"





















