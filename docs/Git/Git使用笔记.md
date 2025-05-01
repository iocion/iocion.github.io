## Git 使用笔记

#### 1.网络连接问题

无法连接的时候可以使用clash-verge的全局代理
Git配置参考：[Git配置文档参考](https://git.javaliu.com/02_config/03_remote_config.html)。
<img src="C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20250421011829645.png" alt="image-20250421011829645" style="zoom:30%;" />

```bash
复制bash环境变量类型:like this ,then excute it in wsl bash
export https_proxy=http://127.0.0.1:7897 http_proxy=http://127.0.0.1:7897 all_proxy=socks5://127.0.0.1:7897
# 修改 ~/.bashrc
# 增加上面的语句
```

```bash
# 主要分为 global 和 local 两种 ,这里个人开发就选择 global 比较简单
git config --global --unset https.proxy
git config --global --unset http.proxy
```

***

#### 2.diverged(分叉问题)

本地分支和远程分支已经分叉（diverged），也就是说，它们各自有了独立的提交历史。Git 不知道你希望如何处理这种分歧：是通过合并（merge）还是通过变基（rebase）来整合这些更改。

```bash
由于git默认的merge策略，我采用rebase(这种方式可以是提交呈现线性的)，不会导致merge的分支看起来太乱
git config pull.rebase true # 修改默认改为rebase
git pull --rebase origin update # 手动指定rebase
# 出现rebase conflict
git rebase --continue # 手动解决冲突
```





#### 4.分支clone问题

```bash
# 一般情况下，clone项目地址后，只会clone main 分支的内容
# 如何clone 其他指定分支呢 eg: brach -> myfeature
git clone -b myfeature https://github.com/pwxiao/AutoOJ.git
```



#### 3.Git工作流

```bash
# github workflow
git clone **
git checkout -b myfeature
# git diff  # check what change you did 
git add .
git commit "filename" -m "提交信息"
git push origin myfeature
git checkout main
git pull origin main
git checkout myfeature
git rebase main
# may be had rebase conflict
# you should choice what segement you need.
git push -f origin myfeature
git checkout myfeature
# everthing ready!
# pull request
# main branch user will use squash and merge
# update2
**delete branch** 
**git checkout main**
**git branch -D myfeature**
git pull origin master   **new result**
```

#### 4.对Git进行代码打包->zip,tar.gz,

```bash
git archive --format=zip --output=/home/han/OJ/Autooj.zip HEAD
# 在当前分支的head位置进行代码打包，这里的格式是zip
git log main --oneline # 查看main分支的hash值
```

#### 5.对于git修改当前分支，切换分支不变的情况

问题描述：我在A分支上面做了修改，然后切换到B分支的时候，发现B分支上也存在A分支上面的修改
问题原因：如果当前分支所作的修改没有提交就切换其他的分支的话，那么分支上也会看到相同的修改

```bash
1：解决方法一
git add .
git commit -m "commit_message"
git status # 检查工作区和暂存区是不是干净的
# 如下图所示
```

<img src="C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20250501122834883.png" alt="image-20250501122834883" style="zoom:80%;" />

```bash
2：解决方法二
# 如果在当前的分支工作还没有做完，不能提交，但是又想去其他的分支，这时可以把当前分支的工作现场隐藏起来。使用git stash隐藏当前的工作现场，这时候使用git status查看工作区是否是干净的，就可以放心去其他分支的部分了。使用git stash list 可以查看隐藏的工作现场
恢复工作现场的两种方式
1.用 git stash apply 恢复。恢复后，stash list 中并不删除恢复的stash，需要使用 git stash drop 来删除。
2.用 git stash pop,恢复的时候，先用 git stash list 查看，然后使用 git stash apply stash@{0}
or git stash pop stash@{0} 来恢复指定的 stash
```

![image-20250501130220636](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20250501130220636.png)


