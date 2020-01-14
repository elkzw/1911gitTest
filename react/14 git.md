###Git命令

* 安装

> Git平台安装包下载地址为:http://git-scm.com/downloads(下载速度较慢)

* 注册

  `git config --global user.name "用户名"`
  `git config --global user.email "邮箱"`

  `git config --list ` 可以查看用户名、邮箱

* `git init`     初始化一个仓储/仓库.      本质创建了一个名为.git的隐藏目录

      Workspace：工作区
      Index / Stage：暂存区
      Repository：仓库区（或本地仓库）
      Remote：远程仓库

* `git add文件路径.后缀`	添加一个文件
  `git add. `    表示添加全部

* `git rm 文件路径.后缀 --cache  `   从暂存区删除文件 

* `git commit -m "本次提交的简要说明信息" `      提交一个文件(备注)

* `git commit -a -m "提交的信息" `   合并操作(不推荐,管理自己代码时可以这么做)(了解)

* `git diff ` 对比与文件变化

* `git reset --hard Head `      版本回退

  - Head 表示得到最近的一次提交的代码
  - Head^表示上一次提交的代码，Head^^表示上上次提交的代码;
    当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100

  - `git reset --hard 提交的版本号`
    可以回退到指定的版本(根据每次提交的版本的号)

* `git reflog `    可以查看每一次的提交的版本号
* `git log `        命令显示从最近到最远的提交日志

注意:

> 版本回回退后，你如果用git log命令查看就会发现回退前的一个版本不见了，你可以通过git reflog查看所有的版本号，通过git reset --hard 提交的版本号，回到指定的版本。版本号没必要写全，前5位就可以了，Git会自动去找。

* 撤销操作主要有如下几种:

`git commit      --amend  `      撤销上一次提交  并将暂存区文件重新提交
`git checkout    -- 文件路径  `   拉取暂存区文件 并将其替换成工作区文件
`git reset HEAD  -- 文件路径`     拉取最近一次提交到版本库的文件到暂存区  改操作不影响工作区

* gitignore文件    忽略文件

  > 在这个文件里写一些想要被git忽略的文件或者文件夹
  >
  > 可以通过命令`git status`查看仓库状态 

* git branch 分支名   创建分支

  - 列出所有分支:`git branch`,在列出所以分支中,当前分支前会有个*号
  - 切换分支:`git checkout 分支名`
  - 创建和切换分支可以合并为:`git checkout -b 分支名`
  - 切换到主分支:`git checkout master`
  - 合并分支,把新创建的分支的提交合并到主分支中: `git merge 分支名`，把指定分支名的分支合并到当前分支
  - 合并分支之后，我们可以清除之前临时使用的分支：`git branch -d` 分支名 

* 推送(push)与拉取(pull)与克隆（clone）

  * 每天的工作日常:

    1. 下载远程仓库到本地：git clone 远程仓库地址

    2. 使用cd命令进入下载的文件夹(或者双击文件夹)

    3. 切换到你的工作本支并更新分支代码

       git clone是将整个工程复制下来，不需要本地是仓库

    4. 第四:把本地代码提交远程仓库

    git remote add origin https://github.com/cyanrui/hkhk.git
    git push -u origin master

注意:

`git clone`:从远程服务器克隆一个一模一样的版本库到本地,复制的是整个版本库.
（clone是将一个库复制到你的本地，是一个本地从无到有的过程）

`git pull`:从远程服务器获取到一个branch分支的更新到本地，并更新本地库.
（pull是指同步一个在你本地有版本的库内容更新的部分到你的本地库）

