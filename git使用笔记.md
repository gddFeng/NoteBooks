# 初次使用

## 配置用户及邮箱

* git config --global user.name "gddFeng"
  * 设置用户名为gddFeng
* git config --global user.email "gddFeng@gddFeng.com"
  * 设置email为gddFeng@gddFeng.com

## 配置ssh以连通
检查目录下的`.ssh`文件，如果没有要新建

* ssh-keygen -t rsa -C "gddFeng@gddFeng.com"

新建后将公钥 `id_rsa.pub`提交到GitHub上的`ssh`中

测试连通性

* ssh -T git@github.com

## 配置远程仓库

将当前分支命名为master
* git branch -M master
  
设置远程仓库地址
* git remote add origin github.com:gddFeng/NoteBooks.git

## 提交更改

将项目中所有文件更改提交至缓冲区
* git add .

提交至`HEAD区域`中
* git commit -m "注释"

上传至远程仓库中
* git push -u origin master

