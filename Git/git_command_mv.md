@[TOC](Git 重命名文件/文件夹的mv 方法)

# 问题复现

使用gitbash 输入以下指令：
```bash
git mv docker Docker
```
然后出现了这种情况，这里的docker 是docker 文件夹。
```
PS C:\github_blog\RyanCatalina.github.io> git mv docker Docker
Rename from 'docker' to 'Docker/docker' failed. Should I try again? (y/n) y
Rename from 'docker' to 'Docker/docker' failed. Should I try again? (y/n) n
fatal: renaming 'docker' failed: Permission denied
```
# 查看git 帮助信息

使用`git help` 命令查看git 的命令相关信息，从终端给的反馈信息可知

```
PS C:\github_blog\RyanCatalina.github.io> git help
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
   init      Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add       Add file contents to the index
   mv        Move or rename a file, a directory, or a symlink
   restore   Restore working tree files
   rm        Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect    Use binary search to find the commit that introduced a bug
   diff      Show changes between commits, commit and working tree, etc
   grep      Print lines matching a pattern
   log       Show commit logs
   show      Show various types of objects
   status    Show the working tree status

grow, mark and tweak your common history
   branch    List, create, or delete branches
   commit    Record changes to the repository
   merge     Join two or more development histories together
   rebase    Reapply commits on top of another base tip
   reset     Reset current HEAD to the specified state
   switch    Switch branches
   tag       Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   pull      Fetch from and integrate with another repository or a local branch
   push      Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.
```
`mv` 命令的有作用：
 
 * 移动一个文件、文件目录、符号链接
 * 重名一个文件、文件目录、符号链接
 
 由此可知问题复现中没有逻辑错误。
 通过翻阅官方文档、各种博客，从中得出蛛丝马迹，最后通过实践得出我用的win10 专业版使用git mv 重命名文件目录时对名字是**大小敏感的**。
 
**值得一提的是对文件目录大小写敏感，对文件名不敏感**。

可以模仿使用以下命令来进行文件夹的重命名
```
git mv docker tmp
git mv tmp Docker
```

##  准备提交
当一切修改完成之后，使用`git add *`或者`git add .` 

然后`git push` 或者`git push -u origin master`
 