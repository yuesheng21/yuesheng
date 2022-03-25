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

​	`git log -1`显示最近的一次提交

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

21. 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

    当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场；但`git stash pop`会删除stash内容，可用`git stash list`查看工作现场的列表。一是用`git stash apply`恢复，但是恢复后，stash内容并不删除，你需要用`git stash drop`来删除；

    在master分支上修复的bug，想要合并到当前dev分支，可以用`git cherry-pick <commit>`命令，把bug提交的修改“复制”到当前分支，避免重复劳动。

    ## 远程多人协作

22. 因此，多人协作的工作模式通常是这样：

    1. 首先，可以试图用`git push origin <branch-name>`推送自己的修改；
    2. 如果推送失败，则因为远程分支比你的本地更新，需要先用`git pull`试图合并；
    3. 如果合并有冲突，则解决冲突，并在本地提交；
    4. 没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功！

    如果`git pull`提示`no tracking information`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>`。

23. 查看远程库信息，使用`git remote -v`；

    本地新建的分支如果不推送到远程，对其他人就是不可见的；

    从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；

    在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；

    建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；

    从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。

    【多人协作部分理解还有点问题，下次找找视频看看】

    ## 标签管理

24. 命令`git tag <tagname>`用于新建一个标签，默认为`HEAD`，即最新的`commit`版本，也可以指定一个commit id；用`git log --pretty=online --abbrev-commit`查看历史提交的id

    命令`git tag -a <tagname> -m "blablabla..."`可以指定标签信息；

    命令`git tag`可以查看所有标签。标签一般都保存在本地，所以可以用`git tag -d v0.1`来删除某个标签，要推送某个标签到远程，用`git push origin v1.1`,或者一次性推送，所有尚未完成的本地标签`git push origin --tags`，若要删除一个远程标签，先在本地删除，再用`git push origin :refs/tags/<tagname>`来删除一个远程标签

    ## 其他

25. github中点fork即可自己的主页中克隆一个别人的库，然后即可下载至自己的本地仓库，在github上发起pull request可以申请官方库接受你的更改

26. 对不同的远程库分别命名，即可与多个远程库链接

27. 配置别名，例如：`git config --global alias.st status`那么以后st即可代表status，参数--global是全局参数，这台电脑的所有git仓库即可使用。要管理配置文件，可打开.git/config中，别名在alias后面，可直接再次修改，或直接删除

28. 利用linux搭建git服务器  [教程](https://www.liaoxuefeng.com/wiki/896043488029600/899998870925664)

29. 推荐图形化编程工具sourcetree[官网](https://www.sourcetreeapp.com/)

30. 常用命令表格[Git Cheat Sheet](https://liaoxuefeng.gitee.io/resource.liaoxuefeng.com/git/git-cheat-sheet.pdf)

    ## linux中常用的linux命令

31. git Bash :unix和linux风格的命令行。

32. Git CMD：Windows风格的命令行。

33. Git GUI： 图形界面的GIt，不建议初学者使用，尽量先熟悉常用命令

34. `cd readme`改变目录

35. `cd..`回退到上一目录，直接`cd`进入默认目录

36. `pwd`显示当前所在的目录路径

37. `ls(II)`都是列出当前目录中的所有文件，只不过加II显示的内容更为详细

38. `touch readme.txt ` 在当前目录新建一个文件

39. `rm readme.txt` 删除一个文件

40. `mkdir filename`新建一个文件夹，命名为filename

41. `rm-r filename`:删除一个文件夹

42. `mv readme.txt filename`:移动文件，即移动readme文件到filename目录下

43. `reset`重新初始化终端/清屏

44. `clear`清屏

45. `history`查看命令历史

46. `help`帮助

47. `exit`退出

    ## git flow 常用分支名称

48. * Production 分支

      也就是我们经常使用的Master分支，这个分支最近发布到生产环境的代码，最近发布的Release， 这个分支只能从其他分支合并，不能在这个分支直接修改

    * Develop分支

      这个分支是我们是我们的主开发分支，包含所有要发布到下一个Release的代码，这个主要合并与其他分支，比如Feature分支

    * Feature分支

      这个分支主要是用来开发一个新的功能，一旦开发完成，我们合并回Develop分支进入下一个Release

    * Release分支

      当你需要一个发布一个新Release的时候，我们基于Develop分支创建一个Release分支，完成Release后，我们合并到Master和Develop分支

    * Hotfix分支

      当我们在Production发现新的bug时，我们需要创建一个该分支，完成后，再合并回Develop，所有Hotfix的改动会进入下一个Release

49. ![img](https://upload-images.jianshu.io/upload_images/1366859-091b03e7e4a6daa3.png?imageMogr2/auto-orient/strip|imageView2/2/format/webp)

50. 一般使用规则 

    1. 所有在Master分支上的Commit应该打上Tag，一般情况下Master不存在Commit，Devlop分支基于Master分支创建
    2. Feature分支做完后，必须合并回Develop分支, 合并完分支后一般会删点这个Feature分支，毕竟保留下来意义也不大。
    3. Release分支基于Develop分支创建，打完Release分支之后，我们可以在这个Release分支上测试，修改Bug等。同时，其它开发人员可以基于Develop分支新建Feature (记住：一旦打了Release分支之后不要从Develop分支上合并新的改动到Release分支)发布Release分支时，合并Release到Master和Develop， 同时在Master分支上打个Tag记住Release版本号，然后可以删除Release分支了。
    4. hotfix分支基于Master分支创建，开发完后需要合并回Master和Develop分支，同时在Master上打一个tag。