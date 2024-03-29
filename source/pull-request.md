# Pull Request 流程

本章主要介绍如何修改地震“学”文档的源码并提交 Pull Request（拉取请求，简称 PR）。

若只是对文档做简单的微调，比如修改简单的别字、语句不通或不清晰的描述等，可以直接通过 GitHub [在线修改并提交]。

若需要对文档做大量修改，比如新增章节、调整章节结构等，请先到源码仓库提交 Issue，由维护者一起讨论是否有必要做修改。
如果已存在与您想做的修改相关的 Issue，请直接在该 Issue 下留言，以让我们知道您打算做什么。
相关修改经过讨论确认需要执行后，可选择[线下修改并提交]。

:::{note}
若不熟悉 Markdown 标记语言，可以参考 {doc}`Markdown 教程 <seis101:programming/markdown>`。
:::

:::{note}
地震“学”所有文档源码都开源托管在 [GitHub](https://github.com/) 上，因此读者需要
一个 GitHub 账户才能提交 PR。可以参考 <http://www.worldhello.net/gotgithub/02-join-github/010-account-setup.html>，
注册帐号。
:::

## 注意事项

- 每个 PR 应该是一个较小但内容完整的修改
- 较大的修改应分解为多个小的修改，并分别提交 PR
- 应提交单独的 PR 来修复错误
- 详细描述提交的 PR 做了哪些修改以及为什么需要这些修改
- 不要在提交的 PR 中修改与其无关的文件，如 {file}`.gitignore` 等
- commit 的注释信息应该是描述性的，可以参考 [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
- 希望读者对审稿人/维护者的评论和意见保持开放的心态，并努力改进代码或文档
- 新的 PR 不一定会及时审核，取决于审稿人/维护者的当时的工作时间

## 在线修改并提交

1. 在线修改

   点击文档网页右上角的 “Edit on GitHub”，网页会自动跳转到文档源码文件。点击源码右上方的铅笔符号
   “Edit this file”，即可在线修改。此过程会自动复制（Fork）仓库至个人 GitHub 帐号中。

2. 提交修改

   修改完后，在下方的 “Commit changes” 中输入有关此次修改的标题和具体描述。输入一个简短的新分支名字。
   点击 “Commit changes” 提交修改。

3. 提交 PR

   在 “Open a pull request” 页面中，输入此 PR 的标题和具体描述。点击 “Create pull request” 即可。

## 线下修改并提交

:::{note}
推荐设置并使用 SSH 秘钥在本地计算机和 GitHub 仓库之间进行传输。

若未设置 SSH 秘钥，则需要修改以下步骤中的远程仓库地址：

- git@github.com:seismology-freshman/seismology101.git 替换为 https://github.com/seismology-freshman/seismology101.git
- git@github.com:seismo-learn/seismology101.git 替换为 https://github.com/seismo-learn/seismology101.git
:::

````{dropdown} 安装 git

地震“学”所有文档均使用 [git](https://git-scm.com) 进行版本控制。以下步骤假定
用户已安装 git。若未安装，可以使用以下命令安装或更新 git：

::::{tab-set}

:::{tab-item} Fedora
```
$ sudo dnf install git
```
:::

:::{tab-item} Ubuntu/Debian
```
$ sudo apt install git
```
:::

:::{tab-item} macOS
```
$ brew install git
```
:::

:::{tab-item} Windows
打开 [https://git-scm.com/downloads]，下载并安装 Git for Windows。
:::

::::

安装完成后，还需设置个人信息。打开终端，运行以下命令
（将 "seismo-learn" 和 "seismo-learn@gmail.com" 替换成个人对应的信息）:
```
# 设置用户姓名和邮箱
$ git config --global user.name "seismo-learn"
$ git config --global user.email "seismo-learn@gmail.com"

# 查看 ~/.gitconfig
$ cat ~/.gitconfig
[user]
    name = seismo-learn
    email = seismo-learn@gmail.com
```
````

```{dropdown} git 和 GitHub 学习资料

以下修改文档并提交的步骤中使用了 git 的一些常用选项，可以参考以下资料学习更多用法：

- [git 简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)
- [廖雪峰的 Git 教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [GotGitHub](http://www.worldhello.net/gotgithub/index.html)
- [How to Use Git and Git Workflows – a Practical Guide](https://www.freecodecamp.org/news/practical-git-and-git-workflows/amp/)
- [Pro Git](https://git-scm.com/book/zh/)

GitHub 相关资料：

- [GitHub 中文文档](https://docs.github.com/cn/github)
- [Understanding the GitHub flow](https://guides.github.com/introduction/flow/)
```

### 克隆和复制仓库

:::{note}
以下步骤假定读者的 GitHub 用户名为 `seismology-freshman`。

以下步骤以[地震“学”科研入门教程](https://seismo-learn.org/seismology101/)为例，修改其他文档时做简单替换即可：

- 修改文档[地震“学”软件](https://seismo-learn.org/software/): 将 `seismology101` 改成 `software`
- 修改文档[地震“学”参考书](https://seismo-learn.org/seismology/): 将 `seismology101` 改成 `seismology`
:::

1. 复制仓库至个人 GitHub 帐号

   点击项目主页 <https://github.com/seismo-learn/seismology101> 右上角的 Fork 按钮，将该项目复制到个人 GitHub 账户下。
   复制完成后，个人 GitHub 帐号下便有了 <https://github.com/seismology-freshman/seismology101> 仓库。

2. 克隆个人 GitHub 帐号下的复制仓库到本地计算机（复制仓库默认是本地克隆仓库的远程 origin）:

   ```
   # 进入 ~/Downloads 目录，也可以选择其他目录存放文档源码
   $ cd ~/Downloads

   # 克隆仓库
   $ git clone git@github.com:seismology-freshman/seismology101.git
   ```

3. 添加官方仓库作为本地克隆仓库的另一个远程，并命名为 upstream:

   ```
   # 进入 ~/Downloads/seismology101 目录
   $ cd ~/Downloads/seismology101/

   # 添加官方仓库作为另一个远程 upstream
   $ git remote add upstream git@github.com:seismo-learn/seismology101.git
   ```

:::{note}
上述三个步骤只需在第一次修改代码时执行一次。一旦复制或克隆某仓库后，就无需再次复制或克隆。
:::

### 修改文档

1. 在本地创建并切换至新分支，假定新分支名为 `pr-workflow`（分支名需简短、描述性且独特）:

   ```
   # 若不在 main 分支，需先切换至该分支
   $ git checkout main

   # 创建并切换至 pr-workflow 分支
   $ git checkout -b pr-workflow
   ```

2. 在新建分支中对文档做修改，并提交 commit（此过程可以循环多次）:

   ```
   # 查看仓库当前的状态
   $ git status
   # 添加所有修改
   $ git add --all

   # 查看仓库当前的状态
   $ git status
   # 提交添加的修改
   $ git commit -m "此处填写本次提交的注释信息"
   ```

   :::{warning}
   切忌不要直接在 main 分支中进行修改和提交
   :::

3. 修改过程中，可以随时在本地构建文档并检查修改效果

   使用以下命令构建教程文档，生成的文档位于本地仓库的 {file}`build/html/` 目录下，直接用浏览器打开
   {file}`build/html/index.html` 即可预览:

   ```
   # 进入仓库主目录
   $ cd ~/Downloads/seismology101/

   # 编译生成 HTML 格式的文档
   $ make html
   ```

:::{note}
开发 pr-workflow 分支的过程中，官方 main 分支可能已经更新。可以经常同步最新版的官方
main 分支，也可以定期同步。

1. 同步本地和官方 main 分支:

   ```
   # 切换到 main 分支
   $ git checkout main

   # 获取官方 main 分支，并合并到本地 main 分支
   $ git pull upstream main
   ```

2. 更新个人 GitHub 帐号下的复制仓库 main 分支:

   ```
   $ git push origin main
   ```

提交 PR 后，一般会收到评论和修改建议，有些修改建议可能直接在远程（origin）pr-worflow
分支中就接收了。有时，还会在 PR 中选择同步最新版的官方 main 分支到远程的 pr-worflow
分支。这两种情况下，我们都需要同步修改过的远程 pr-worflow 分支和本地 pr-worflow 分支:

```
# 切换到 pr-workflow 分支
$ git checkout pr-workflow

# 获取远程 pr-workflow 分支，并合并到本地 pr-workflow 分支
$ git pull origin pr-workflow
```

本地 main 分支和 pr-worflow 分支一般不需要同步。如果确实需要同步时，请确保自己有足够
的能力和精力解决可能的冲突。
:::

:::{note}
有时候，我们需要复制一些 commit 到某分支，推荐使用 `git cherry-pick` 命令。可以
参考 [git cherry-pick 教程](https://www.ruanyifeng.com/blog/2020/04/git-cherry-pick.html)
学习其基本用法。

除了 `git merge` 命令外，`git rebase` 命令也可以用来整合来自不同分支的修改，
它比 `git cherry-pick` 命令更强大。但是变基（rebase）会修改提交历史，因此你首先
需要了解该命令的详细用法，知道自己在做啥。可以参考[变基](https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E5%8F%98%E5%9F%BA)
学习其基本用法。总的原则是，**只对尚未推送给别人的本地修改执行变基操作清理历史，从不对
已推送至别处的提交执行变基操作**。
:::

### 提交 PR

1. 推送 pr-workflow 分支至个人 GitHub 帐号下的复制仓库:

   ```
   $ git push origin pr-workflow
   ```

2. 提交 PR

   进入个人 GitHub 帐号下的复制仓库（即 <https://github.com/seismology-freshman/seismology101>）。
   一般 GitHub 会自动提示有可提交的 PR，点击 “Compare & pull request”，输入此 PR 的标题和具体描述，
   最后点击 “Create pull request” 即可。

3. 审核、评论以及修改 PR

   地震“学”维护者收到 PR 后，会对代码进行审核、评论以及修改，并决定是否接受或结束该 PR。

   提交的 PR 在接收前可能需要读者多次修改。这种情况并不要创建新 PR，只需继续本地 pr-workflow 分支中
   修改并提交，然后再次推送 pr-workflow 分支至远程 origin 即可，修改将自动添加到已提交的 PR 中。
   推送新的修改后，可以选择在该 PR 中留言，以通知维护者已提交新的修改。

4. PR 被接受并合并至官方 main 分支后，则可以更新 main 分支，并删除 pr-workflow 分支

   更新本地和个人 GitHub 中的 main 分支:

   ```
   # 切换回本地 main 分支
   $ git checkout main

   # 获取官方 main 分支，并合并到本地 main 分支
   $ git pull upstream main

   # 更新个人 GitHub 中的 main 分支
   $ git push origin main
   ```

   删除本地和个人 GitHub 中的 pr-workflow 分支:

   ```
   # 删除本地 pr-workflow 分支
   $ git branch -D pr-workflow

   # 删除个人 GitHub 上的远程 pr-workflow 分支，也可以在 GitHub 上点击按钮删除分支
   $ git push origin :pr-workflow
   ```
