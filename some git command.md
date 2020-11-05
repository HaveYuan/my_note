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

### 8.当第一次git pull失败时使用以下命令
* `git pull --allow-unrelated-histories`
* `git push --force origin master`

### 9.修改git用户名和密码
* `$ git config --global user.name "username"`
* `$ git config --global user.email "email"`

### 10.使用git pull origin报以下错时
>“You asked to pull from the remote 'origin' ,but did not specify a branch.Because this is not the default configured remote for you current branch.”
#### 使用以下命令
```
git branch  --set-upstream master origin/master
```

### 11.使用git reflog查看所有提交纪录，再用git reset恢复
```
git reflog

git reset --hard xxx
```