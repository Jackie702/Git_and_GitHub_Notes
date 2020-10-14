<!--
 * @Author: Ciyuan Yu
 * @Date: 2020-09-25 11:37:01
 * @LastEditTime: 2020-09-29 16:23:10
 * @LastEditors: Please set LastEditors
 * @Description: Notes of Git commands
-->
### 从创建一个新的git分支到上传本地文件 ###
$ git status                //查看当前目录下文件被git管理的情况
$ git add <client-new/>     //将client-new/下所有文件交给git管理
$ git reset <client-new/public/*>   //将目录下所有文件移出git管理
$ git remote add <ciyuan> <git@git.biomind.com.cn:YUCIYUAN/Biomind-GraphTools.git>  //将该远程目录(分支)命名为ciyuan
$ git checkout -b <feature/client_new>      //创建一个新的分支,路径为feature/client_new
$ git commit -m "New client with material ui"   //提交当前分支到暂存区   
$ git remote //查看所有远程分支
$ git push <ciyuan> <feature/client_new>    //将暂存区中feature/client_new提交到别名为ciyuan的git目录


### 零散的git命令 ###
$ git clone <username@host:/path/to/repository>

$ git status        //查看在上次提交之后是否有修改
$ git status -s     //输出精简信息

$ git remote        //列出已经存在的远程分支
$ git remote -v     //列出远程分支详细信息
$ git remote add <server name> git@<url>.git    //添加一个远程仓库

$ git fetch <server name>

$ git diff
$ git diff <file name>
$ git diff <source_branch> <target_branch>  //预览两个分支间的差异

$ git add .     //将现目录下所有文件添加至git进行管理

$ git stash
$ git stash list

$ git checkout 
$ git checkout -a
$ git checkout <branch>

$ git rebase
$ git rebase --countinue

$ git log   //获取提交ID

$ git reset <id>

$ git merge
$ git merge --abort
$ git merge <server name> <branch>

$ git show <id>