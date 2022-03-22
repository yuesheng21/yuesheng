# 学习git

	## 前奏

1. Unix的哲学是“没有消息是最好的消息”；

2. 创建库

   ```git
   $ mkdir learngit
   $ cd learngit
   $ pwd
   /Users/michael/learngit
   ```

   创建git库后多了.git目录，请不要随意改动该文件，用于追踪管理版本库的

3. 两步将文件提交到仓库，`git add`和`git commit -m`“附加说明”；注意，`commit`一次提交所有文件，故可多次add，只用一次commit

   ##   时光机穿梭

   

4. > `git status`// 查看文件状态
   >
   > `git diff readme.txt`// 查看更改细节

5. ~~~c++
   	git log；//查看版本更改历史记录
      	git log --pretty=oneline;//信息简略的历史记录
      	git reset --hard HEAD^;//返回上一版本，或使用HEAD~100，返回上一百个版本
      	cat readme.txt//check detailed content打印内容
      	git reset --hard//+版本号即刻来到’未来‘的版本
       git reflog//查看每一次的命令，查看版本号
       git diff HEAD --readme.txt//可以查看工作区与版本库最新的区别
   ~~~

6. 因此`-m`后的备注不要随便打

7. - HEAD指向的版本就是当前版本，因此，git允许我们在版本的历史之间穿梭，使用命令 `git reset --hard commit_id' `
   - 穿梭前，用`git log `可以查看提交历史，以便确定要回退到哪个版本
   - 要重返未来，用 `git reflog `查看历史命令，以便确定要回到未来的版本

8. learngit就是一个工作区；可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。
9. 要区分暂存区和工作区
10. 

```c++
$ git checkout -- readme.txt//
```

11.场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。 

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)一节，不过前提是没有推送到远程库。

12. 命令`git rm`用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失**最近一次提交后你修改的内容**。

    ## 远程仓库

    

13. 要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；

    关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名；

    关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；

    此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；

    ### 删除远程库

    如果添加的时候地址写错了，或者就是想删除远程库，可以用`git remote rm <name>`命令。使用前，建议先用`git remote -v`查看远程库信息：

    ```c++
    $ git remote -v
    origin  git@github.com:michaelliao/learn-git.git (fetch)
    origin  git@github.com:michaelliao/learn-git.git (push)
    ```

    然后，根据名字删除，比如删除`origin`：

    ```c++
    $ git remote rm origin
    ```

15. 要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。

    Git支持多种协议，包括`https`，但`ssh`协议速度最快。

    ## 其他命令符

16. ~~~
    ls//list查看路径内的文件
    	ls -a//all:do not ignore entries starting with
    	ls -l//long:use a long listing format
        ls -la//
    ~~~

17. 

17.[Git的常用命令及其作用](https://www.cnblogs.com/jakii/p/4442979.html)



​	Git是一种分布式文件管理系统。

​	<code>git help</code> :获取git基本命令

​	<code>Git init</code>  :

​	创建一个空的Git库。在当前目录中产生一个.git 的子目录。以后，所有的文件变化信息都会保存到这	个目录下。

​	`Git add` ：

​	将当前工作目录中更改或者新增的文件加入到Git的索引中，加入到Git的索引中就表示记入了版本历	史中，这也是提交之前所需要执行的一步。

​	`Git rm` ：
​	从当前的工作目录中和索引中删除文件。 
​	可以递归删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文       件。

​	`Git status`：查看版本库的变化。

​	`Git log `：查看历史日志，包含每次版本变化

​	`Git merge`： 
​	把服务器上下载下来的代码和本地代码合并。或者进行分支合并。

​	`Git diff` ：
​	把本地的代码和index中的代码进行比较，或者是把index中的代码和本地仓库中的代码进行比较。

​	`Git-ls-files` ：
​	查看当前的git库中有那些文件

​	`Git mv` ：
​	重命名一个文件、目录或者链接。

​	` git branch` ：

​	列出本地git库中的所有分支。在列出的分支中，若分支名前有*，则表示此分支为当前分支。

​	`git branch` 分支名 ：创建分支

​	`git checkout` 分支名 ：切换到某个分支上

​	`git branch –D` 分支名 ：删除分支

​	`git diff master `分支名：比较主分支与目标分支的区别

​	`git-show-branch` ：查看分支历史

 	`git whatchanged` ：查看分支操作记录

​	`Git revert`：还原某次对版本的修改 

​	`Git config` ：新增更改git的各种设置

​	`Git show `：显示对象的各种类型

​	`Git pull `：
​	从服务器的仓库中获取代码，和本地代码合并。

​	`Git push` ：
​	将本地commit的代码更新到远程版本库中，例如 “git push origin”就会将本地的代码更新到名为orgin的远程版本库中。 

​	`Git fetch` ：
​	从服务器的仓库中下载代码。

## 分支管理策略

18. Git鼓励大量使用分支：

    查看分支：`git branch`

    创建分支：`git branch <name>`

    切换分支：`git checkout <name>`或者`git switch <name>`

    创建+切换分支：`git checkout -b <name>`或者`git switch -c <name>`

    合并某分支到当前分支：`git merge <name>`

    删除分支：`git branch -d <name>`

19. 当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

    解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

    用`git log --graph`命令可以看到分支合并图。

20. ```linux
    $ git merge --no-ff -m "merge with no-ff" dev
    $ git log --graph --pretty=oneline --abbrev-commit
    ```

    Git分支十分强大，在团队开发中应该充分应用。

    合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并。

21. 