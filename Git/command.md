# 新建

创建一个新的git 版本库。这个版本库的配置、存储等信息会被保存到.git 文件夹中
```
# 初始化当前项目
git init 

# 新建一个目录，将其初始化为Git 代码库
git init [project-name]

# 在指定目录创建一个空的Git 仓库，运行这个命令会创建一个名为director
git init --bare <directory>

# 下载一个项目和它的整个代码历史
# 这个命令就是将一个版本库拷贝到另一个目录中，同时也将分支都拷贝到新的版本库中。这样就可以在新的版本库中提交到远程分支
git clone [url]
```
# 配置

Git 的配置文件为.gitconfig，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）
更改设置。可以是版本库的设置，也可以是系统的或全局的

```
# 显示当前的Git 配置
git config --list

# 编辑Git 配置文件
git config -e [--global]

# 输出、设置基本的全局变量
git config --global user.email "Ryan@gmail.com"
git config --global user.name "Ryan"

```

# 帮助

git 内置了对命令非常详细的解释，可以供我们快速查阅

```
# 查找可用命令
git help

# 查找所有可用命令
git hele -a

# 在文档中查找特定命令
git help add
git help push
git help pull
git help fetch
```

# 状态

显示索引文件（也就是当前工作空间）和当前的头指针指向的提交的不同

```
# 显示分支，未跟踪文件，更改和其他不同
git status

# 查看其他的git status 的用法
git help status
```
# 信息

获取某些文件，某些文件，某次提交等git 信息
```
# 显示commit 历史，以及每次commit 发生变更的文件
git log --stat

# 搜索提交历史，根据关键词
git log -S [keyword]

# 显示某个commit 之后的所有变动，每个commit 占据一行
git log [tag] HEAD --pretty=format:%s

# 显示某个commit 之后的所有变动，其“提交说明”必须符合搜索条件
git log [tag] HEAD --grep feature

# 显示某个文件的版本历史，包括文件改名
git log --follow [file]
git whatchanged [file]

# 显示指定文件相关的每一次diff
git log -p [file]

# 显示所有提交过的用户，按提交次数排序
git shortlog -sn

# 显示指定是什么人在什么时间修改过
git blame [file]

# 显示暂存区和工作区的差异
git diff

# 显示暂存区和上一个commit 的差异
git diff --cached[file]

# 显示工作区与当前分支最新commit 之间的差异
git diff HEAD

# 显示今天你写了多少行代码
git diff --shortstat "@{0 day ago}
```