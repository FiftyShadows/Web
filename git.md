本地强制上传到远程仓库git push -u origin master -f

git log --oneline

git dif xxx.xx

##创建裸仓库

裸仓库通常可被用来充当开发者们传递提交的汇聚点，以便其他人可以从中拉回他们所做的修改。

git clone --bare /program/first-steps    创建裸仓库





##工作区与版本库

工作区是一个包含.git子目录（内含版本库）中的目录。用git init命令在当前目录中创建版本库。



git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"





















