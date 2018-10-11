---
title: git
tags: git
---
# git
## 一、新建代码库

    git init                                                             //初始化
    git add README                                                       //更新README文件 .为所有文件
    git commit -m 'first commit'                                         //提交更新，并注释信息“first commit”
    git remote add origin git@github.com:yeayee/helloworld.git           //连接远程github项目
    git push origin master                                               //将本地项目更新到github项目上去
    git clone git@github.com:yeayee/helloworld.git helloworld            //把仓库复制到自己的电脑上
    git remote rm origin                                                 //删除源origin
    git pull origin master                                               //将github上的项目拉下来
    git config --global core.editor Notepad++                            //设置编辑器
    git config user.name                                                 //查看配置信息
    git help <verb>                                                      //查看帮助信息
    git status                                                           //查看文件当前处于什么状态
    git log                                                              //回顾提交历史
    git diff                                                             //查看尚未暂存文件更新了哪些部分
    git remote -v                                                        //查看你当前项目远程连接的是哪个仓库地址
    git fetch origin                                                     //取得远程更新，这里可以看做是准备要取了
    git merge origin/master                                              //把更新的内容合并到本地分支origin/master
    git rm src/com/hzh/hibernate/dao/aaa.java                            //移除我们删除了的那个文件aaa.java
    git rm src/com/hzh/hibernate/bbb/ -r                                 //-r会把bbb/目录下的所有内容一次性移除
    git branch testbranch                                                //命名分支
    git checkout testbranch                                              //将testbranch分支设置为当前工作分支

## 二、配置

    Git的设置文件为.gitconfig，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。
    cd ~/.ssh                                                             //查看计算机ssh密钥
    ssh-keygen -t rsa -C "85362057@qq.com"                                //填写email地址，生成密钥
    ssh -T git@github.com                                                 //测试连接是否成功
    git config --global github.token e97279836f0d415a3954c1193dba522f     //配置token
    # 显示当前的Git配置
    $ git config --list
      git config --global user.email "1726448967@qq.com"
      git config --global user.name "bolearnpython"
    $ git help
    $ git help config
    # 防止http协议每次都要输入密码：
    $ git config --global credential.helper 'cache --timeout=36000000'      #秒数
    # 编辑Git配置文件
    $ git config -e [--global]

    # 设置提交代码时的用户信息
    git config --global user.name "jake"
    git config --global user.email jake@gmail.com
    #配置你的编缉器
    $ git config --global core.editor emacs
    关闭Ignore文件的功能
    git config core.fileMode false
    删除全局设置
    git config --global --unset <entry-name>
    清除.gitignore文件中记录的文件
    git clean -X -f
    git clean <file_name> -f
    把某一个分支到导出成一个文件
    git bundle create <file> <branch-name>
    查看两个星期内的改动
    git whatchanged --since='2 weeks ago'
## 三、增加/删除文件

    # 添加指定文件到暂存区
    $ git add [file1] [file2] ...

    # 添加指定目录到暂存区，包括子目录
    $ git add [dir]

    # 添加当前目录的所有文件到暂存区
    $ git add .

    # 删除工作区文件，并且将这次删除放入暂存区
    $ git rm [file1] [file2] ...

    # 停止追踪指定文件，但该文件会保留在工作区
    $ git rm --cached [file]

    # 改名文件，并且将这个改名放入暂存区
    $ git mv [file-original] [file-renamed]
## 四、代码提交
    git commit --amend
    查看commit历史

    # 提交暂存区到仓库区
    $ git commit -m [message]

    # 提交暂存区的指定文件到仓库区
    $ git commit [file1] [file2] ... -m [message]

    # 提交工作区自上次commit之后的变化，直接到仓库区
    $ git commit -a

    # 提交时显示所有diff信息
    $ git commit -v

    # 使用一次新的commit，替代上一次提交
    # 如果代码没有任何新变化，则用来改写上一次commit的提交信息
    $ git commit --amend -m [message]

    # 重做上一次commit，并包括指定文件的新变化
    $ git commit --amend [file1] [file2] ...

## 五、分支
    1、在本地创建新分支：git branch newbranch
    2、在本地切换到新分支：git checkout newbranch
    3、将新分支推送到github：git push origin newbranch
    4、在本地删除一个分支：git branch -d newbranch
    5、在Github远端删除一个分支：git push origin :newbranch
    重命名本地分支名。
    git branch -m xue xueweihan

    # 列出所有本地分支
    $ git branch

    # 列出所有远程分支 -r参数相当于：remote
    $ git branch -r

    # 列出所有本地分支和远程分支 -a参数相当于：all
    $ git branch -a

    # 新建一个分支，但依然停留在当前分支
    $ git branch [branch-name]

    # 新建一个分支，并切换到该分支
    $ git checkout -b [branch]

    # 新建一个分支，指向指定commit
    $ git branch [branch] [commit]

    # 新建一个分支，与指定的远程分支建立追踪关忽略系
    $ git branch --track [branch] [remote-branch]

    # 切换到指定分支，并更新工作区
    $ git checkout [branch-name]

    # 建立追踪关系，在现有分支与指定的远程分支之间
    $ git branch --set-upstream [branch] [remote-branch]

    # 合并指定分支到当前分支
    $ git merge [branch]

    # 选择一个commit，合并进当前分支
    $ git cherry-pick [commit]

    # 删除分支
    $ git branch -d [branch-name]

    # 删除远程分支
    $ git push origin --delete [branch-name]
    $ git branch -dr [remote/branch]
## 六、标签

    # 列出所有tag
    $ git tag

    # 新建一个tag在当前commit
    $ git tag [tag]

    # 新建一个tag在指定commit
    $ git tag [tag] [commit]

    # 删除本地tag
    $ git tag -d [tag]

    # 删除远程tag
    $ git push origin :refs/tags/[tagName]

    # 查看tag信息
    $ git show [tag]

    # 提交指定tag
    $ git push [remote] [tag]

    # 提交所有tag
    $ git push [remote] --tags

    # 新建一个分支，指向某个tag
    $ git checkout -b [branch] [tag]
## 七、查看信息

    # 显示有变更的文件
    $ git status
    展示忽略的文件
    git status --ignored
    # 显示当前分支的版本历史
    $ git log

    # 显示commit历史，以及每次commit发生变更的文件
    $ git log --stat

    # 显示某个文件的版本历史，包括文件改名
    $ git log --follow [file]
    $ git whatchanged [file]

    # 显示指定文件相关的每一次diff
    $ git log -p [file]

    # 显示指定文件是什么人在什么时间修改过
    $ git blame [file]

    # 显示暂存区和工作区的差异
    $ git diff

    # 显示暂存区和上一个commit的差异
    $ git diff --cached [file]

    # 显示工作区与当前分支最新commit之间的差异
    $ git diff HEAD

    # 显示两次提交之间的差异
    $ git diff [first-branch]...[second-branch]

    # 显示某次提交的元数据和内容变化
    $ git show [commit]

    # 显示某次提交发生变化的文件
    $ git show --name-only [commit]

    # 显示某次提交时，某个文件的内容
    $ git show [commit]:[filename]

    # 显示当前分支的最近几次提交
    $ git reflog
## 八、远程同步

    # 下载远程仓库的所有变动
    $ git fetch [remote]

    # 显示所有远程仓库
    $ git remote -v

    # 显示某个远程仓库的信息
    $ git remote show [remote]

    修改远程仓库的url
    git remote set-url origin <URL>

    # 增加一个新的远程仓库，并命名
    $ git remote add [shortname] [url]

    # 取回远程仓库的变化，并与本地分支合并
    $ git pull [remote] [branch]

    git pull origin master     # 拉取更新

    # 上传本地指定分支到远程仓库
    $ git push [remote] [branch]

    # 强行推送当前分支到远程仓库，即使有冲突
    $ git push [remote] --force

    # 推送所有分支到远程仓库
    $ git push [remote] --all
## 九、撤销
    $ git checkout master    # 切到master

    # 恢复暂存区的指定文件到工作区
    $ git checkout [file]

    # 恢复某个commit的指定文件到工作区
    $ git checkout [commit] [file]

    创建并切换到该分支
    git checkout -b <branch-name>

    2.git checkout -b newBranch origin/master
    拷贝一份远程分支origin/master的内容到本地，并新建一个名为newBranch的分支。

    # 恢复上一个commit的所有文件到工作区
    $ git checkout .

    # 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
    $ git reset [file]

    # 重置暂存区与工作区，与上一次commit保持一致
    $ git reset --hard

    # 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
    $ git reset [commit]

    # 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
    $ git reset --hard [commit]

    # 重置当前HEAD为指定commit，但保持暂存区和工作区不变
    $ git reset --keep [commit]

    # 新建一个commit，用来撤销指定commit
    # 后者的所有变化都将被前者抵消，并且应用到当前分支
    $ git revert [commit]
    git revert master~2     回滚
    git revert <commit_id> -m <parent_id> 回滚合并
    抛弃本地仓库的所有版本(commit)，回到远程仓库的状态。
    git fetch --all && git reset --hard origin/master

## 十、其他

    # 生成一个可供发布的压缩包
    $ git archive
    [git]git忽略文件
        可以通过创建~/.gitignore_global并添加到git全局配置以减少每层目录的规则重复定义。
        使用命令git config --global core.excludesfile ~/.gitignore_global即可
        .gitignore_global文件中写入要忽略的文件后缀：
        如要忽略“.pyc”的文件，就在.gitignore_global文件中写入 “*.pyc”就ok了。
    [git]git add 增加文件，文件名乱码
        在bash提示符下输入：
        git config --global core.quotepath false

    展示所有tracked的文件
    git ls-files -t
    展示所有untracked的文件
    git ls-files --others
    展示所有忽略的文件
    git ls-files --others -i --exclude-standard

    git stash -u
    展示所有stashes
    git stash list
    回到某个stash的状态
    git stash apply <stash@{n}>
    回到最后一个stash的状态，并删除这个stash
    git stash pop
    删除所有的stash
    git stash clear
    从stash中拿出某个文件的修改
    git checkout <stash@{n}> -- <file_path>
## 使用http代理

    $ git config --global http.proxy http://proxyuser:proxypwd@proxy.server.com:8080

    $ git config --global http.proxy http://127.0.0.1:8787  # lantern

    查看使用代理：

    $ git config --global --get http.proxy

    取消http代理：

    $ git config --global --unset http.proxy

    使用socks代理

    $ git config --global https.proxy 'socks5://proxyuser:proxypwd@proxy.server.com:8080'

    取消socks代理：

    $ git config --global --unset https.proxy
## 常用 git 命令清单。几个专用名词的译名如下。

    Workspace：      工作区
    Index / Stage：  暂存区
    Repository：     仓库区（或本地仓库）
    Remote：         远程仓库
    master分支， 即主分支。任何项目都必须有个这个分支。对项目进行tag或发布版本等操作，都必须在该分支上进行。
    develop分支，即开发分支，从master分支上检出。团队成员一般不会直接更改该分支，而是分别从该分支检出自己的feature分支，开发完成后将feature分支上的改动merge回develop分支。同时release分支由此分支检出。
    release分支，即发布分支，从develop分支上检出。该分支用作发版前的测试，可进行简单的bug修复。如果bug修复比较复杂，可merge回develop分支后由其他分支进行bug修复。此分支测试完成后，需要同时merge到master和develop分支上。
    feature分支，即功能分支，从develop分支上检出。团队成员中每个人都维护一个自己的feature分支，并进行开发工作，开发完成后将此分支merge回develop分支。此分支一般用来开发新功能或进行项目维护等。
    fix分支，  即补丁分支，由develop分支检出，用作bug修复，bug修复完成需merge回develop分支，并将其删除。所以该分支属于临时性分支。
    hotfix分支， 即热补丁分支。和fix分支的区别在于，该分支由master分支检出，进行线上版本的bug修复，修复完成后merge回master分支，并merge到develop分支上，merge完成后也可以将其删除，也属于临时性分支。