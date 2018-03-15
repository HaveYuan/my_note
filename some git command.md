# 一些常用的git命令
### 1.与远程仓库连接
* `git remote add origin https://github.com/YoruProject.git` 

### 2.取消远程仓库连接
* `git remote rm origin` 

### 3.强制推送
* `git push -u origin master -f`

### 4.创建新的分支并切换到该分支
* `git checkout -b new-branch-name`  
他是以下两条命令的简写  
`$ git branch new-branch-name`  
`$ git checkout new-branch-name`  

### 5.合并分支
* `git merge dev`  
git merge命令用于合并指定分支到当前分支   

### 6.删除分支
* `git branch -d branch-name`

### 7.查看分支
* `git branch`
