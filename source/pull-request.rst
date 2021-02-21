Pull Request 流程
==================

本章主要介绍如何修改地震“学”文档的源码并提交 Pull Request（拉取请求，简称 PR）。

若只是对文档做简单的微调，比如修改简单的别字、语句不通或不清晰的描述等，可以直接通过 GitHub `在线修改并提交`_\ 。

若需要对文档做大量修改，比如新增章节、调整章节结构等，请先到项目主页提交 Issue，由维护者一起讨论是否有必要做修改。
如果已存在与您想做的修改相关的 Issue，请直接在该 Issue 下直接留言，以让我们知道您打算做什么。
相关修改经过讨论确认需要执行后，可选择\ `线下修改并提交`_\ 。

注意事项
---------

- 每个 PR 应该是一个较小但内容完整的修改
- 较大的修改应分解为较小的，并分别提交 PR
- 应提交单独的 PR 来修复错误
- 详细描述提交的 PR 做了哪些修改以及为什么需要这些修改
- 不要在提交的 PR 中修改与其无关的文件，如 :file:`.gitignore` 等
- commit 的注释信息应该是描述性的，可以参考 `How to Write a Git Commit Message <https://chris.beams.io/posts/git-commit/>`__
- 希望读者对审稿人/维护者的评论和意见保持开放的心态，并努力改进代码或文档
- 新的 PR 不一定会及时审核，取决于审稿人/维护者的当时的工作时间

在线修改并提交
---------------

读者需要一个 GitHub 账户。可以参考 http://www.worldhello.net/gotgithub/02-join-github/010-account-setup.html，注册帐号。

1.  在线修改

    点击文档网页右上角的 “Edit on GitHub”，网页会自动跳转到文档源码文件。点击源码右上方的铅笔符号
    “Edit this file”，即可在线修改。此过程会自动复制（Fork）仓库至个人 GitHub 帐号中。

2.  提交修改

    修改完后，在下方的 “Commit changes” 中输入有关此次修改的标题和具体描述。输入一个简短的新分支名字。
    点击 “Commit changes” 提交修改。

3.  提交 PR

    在 “Open a pull request” 页面中，输入此 PR 的标题和具体描述。选择 Reviewers。点击 “Create pull request” 即可。

线下修改并提交
--------------

准备工作
^^^^^^^^

1.  注册 GitHub 账户

    地震“学”所有文档源码都开源托管在 `GitHub <https://github.com/>`__ 上，因此读者需要注册一个 GitHub 账户。
    
    可以参考 http://www.worldhello.net/gotgithub/02-join-github/010-account-setup.html，注册帐号。
    
    推荐设置并使用 SSH 秘钥在本地计算机和 GitHub 仓库之间的进行传输。若未设置，则需要修改以下步骤中的远程仓库地址：

    - git@github.com:seismology-freshman/seismology101.git 替换为 https://github.com/seismology-freshman/seismology101.git
    - git@github.com:seismo-learn/seismology101.git 替换为 https://github.com/seismo-learn/seismology101.git

2.  安装版本控制工具 git

    地震“学”所有文档均使用 `git <https://git-scm.com/>`__ 进行版本控制。使用以下命令安装或更新 git：

    .. tabbed:: Fedora

        ::

            $ sudo dnf install git

    .. tabbed:: CentOS

        ::

            $ sudo yum install git

    .. tabbed:: Ubuntu/Debian

        ::

            $ sudo apt install git

    .. tabbed:: macOS

        ::

            $ brew install git

    .. tabbed:: Windows

        打开 https://git-scm.com/downloads，下载并安装 Git for Windows。

    安装完成后，还需设置个人信息。打开终端，运行以下命令（替换 Your Name 和 youremail@example.com，
    例如 “seismo-learn” 和 “seismo-learn@gmail.com”）::

        $ git config --global user.name "Your Name"
        $ git config --global user.email "youremail@example.com"

    以下文档修改并提交步骤中使用了 git 的一些常用选项，可以参考以下资料学习更多用法：

    - `git 简明指南 <http://rogerdudler.github.io/git-guide/index.zh.html>`__
    - `GotGitHub <http://www.worldhello.net/gotgithub/index.html>`__
    - `廖雪峰的 Git 教程 <http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000>`__
    - `Pro Git <https://git-scm.com/book/zh/>`__

3.  安装 Python、Sphinx 以及文档所需依赖包

    地震“学”所有文档均使用文档生成工具 `Sphinx <http://www.sphinx-doc.org/>`__ 构建。因此，若想要在本地构建文档并检查修改效果，
    需要安装 Python、Sphinx 以及文档所需依赖包。

    强烈建议不要使用系统自带的 Python，而建议通过 :doc:`Anaconda <software:anaconda/index>`  来安装和管理 Python。

    参考\ :doc:`building`\ ，安装 Sphinx 和文档所需依赖包。

克隆和复制仓库
^^^^^^^^^^^^^^

.. note::

    以下步骤假定读者的 GitHub 用户名为 ``seismology-freshman``\ 。

    以下步骤以\ `地震“学”科研入门教程 <https://seismo-learn.org/seismology101/>`__\ 为例，修改其他文档时做简单替换即可：

    - 修改文档\ `地震“学”软件 <https://seismo-learn.org/software/>`__\ : 将 ``seismology101`` 改成 ``software``
    - 修改文档\ `地震“学”基础 <https://seismo-learn.org/software/>`__\ : 将 ``seismology101`` 改成 ``seismology``

1.  复制仓库至个人 GitHub 帐号

    点击项目主页 https://github.com/seismo-learn/seismology101 右上角的 Fork 按钮，将该项目复制到个人 GitHub 账户下。
    复制完成后，个人 GitHub 帐号下便有了 https://github.com/seismology-freshman/seismology101 仓库。

2.  克隆个人 GitHub 帐号下的复制仓库到本地计算机（复制仓库默认是本地克隆仓库的远程 origin）::

        # 进入 ~/Downloads 目录，也可以选择其他目录存放文档源码
        $ cd ~/Downloads

        # 克隆仓库
        $ git clone git@github.com:seismology-freshman/seismology101.git

3.  添加官方仓库作为本地克隆仓库的另一个远程，并命名为 upstream::

        # 进入 ~/Downloads/seismology101 目录
        $ cd ~/Downloads/seismology101/

        # 添加官方仓库作为另一个远程 upstream
        $ git remote add origin git@github.com:seismo-learn/seismology101.git

.. note::

   上述三个步骤只需在第一次修改代码时执行一次。一旦复制或克隆某仓库后，就无需再次复制或克隆。

修改文档
^^^^^^^^

1.  在本地创建并切换至新分支，假定新分支名为 ``pr-workflow``\ （分支名需简短、描述性且独特）::

        # 若不在 main 分支，需先切换至该分支
        $ git checkout main

        # 创建并切换至 pr-workflow 分支
        $ git checkout -b pr-workflow

2.  在新建分支中对文档做修改，并提交 commit（此过程可以循环多次）::

        # 查看仓库当前的状态
        $ git status
        # 添加所有修改
        $ git add --all

        # 查看仓库当前的状态
        $ git status
        # 提交添加的修改
        $ git commit -m "此处填写本次提交的注释信息"

    .. warning::

       切忌不要直接在 main 分支中进行修改和提交

3.  修改过程中，可以随时在本地构建文档并检查修改效果

    使用以下命令构建文档，生成的文档位于本地仓库的 :file:`build/html/` 目录下，直接用浏览器打开
    :file:`build/html/index.html` 即可预览::

        # 进入仓库主目录
        $ cd ~/Downloads/seismology101/

        # 编译生成 HTML 格式的文档
        $ make html

.. note::

   开发 pr-workflow 分支的过程中，官方 main 分支可能已经更新。因此，需要经常同步最新版的官方 main 分支。

   1.  同步本地和官方 main 分支::

           # 切换到 main 分支
           $ git checkout main

           # 获取官方 main 分支，并合并到本地 main 分支
           $ git pull upstream main

   2.  更新个人 GitHub 帐号下的复制仓库 main 分支::

           $ git push origin main

   3.  将 pr-workflow 分支基于最新的 main 分支::

           # 切换到 pr-workflow 分支
           $ git checkout pr-workflow

           # 将 pr-workflow 分支基于最新的 main 分支
           $ git rebase main

.. note::

   分支开发的过程中，可能会有很多次 commit，某些 commit 可能不那么重要。可以将多个 commit
   压缩成一个或若干个 commit，这样不仅清晰，也容易管理::

       $ git rebase -i main

提交 PR
^^^^^^^^

1.  推送 pr-workflow 分支至个人 GitHub 帐号下的复制仓库::

        $ git push origin pr-workflow

2.  提交 PR

    进入个人 GitHub 帐号下的复制仓库（即 https://github.com/seismology-freshman/seismology101）。
    一般 GitHub 会自动提示有可提交的 PR，点击 “Compare & pull request”，输入此 PR 的标题和具体描述，
    选择 Reviewers。最后点击 “Create pull request” 即可。

3.  审核、评论以及修改 PR

    地震“学”维护者收到 PR 后，会对代码进行审核、评论以及修改，并决定是否接受或结束该 PR。

    提交的 PR 在接收前可能需要读者多次修改。这种情况并不要创建新 PR，只需继续本地 pr-workflow 分支中修改并提交，
    然后再次推送 pr-workflow 分支至远程 origin 即可，修改将自动添加到已提交的 PR 中。
    推送新的修改后，可以选择在该 PR 中留言或再次请求 Reviewers，来通知 Reviewers 已提交新的修改。

4.  PR 被接受并合并至官方 main 分支后，则可以更新 main 分支，并删除 pr-workflow 分支

    更新本地和个人 GitHub 中的 main 分支::

        # 切换回本地 main 分支
        $ git checkout main

        # 获取官方 main 分支，并合并到本地 main 分支
        $ git pull upstream main

        # 更新个人 GitHub 中的 main 分支
        $ git push origin main

    删除本地和个人 GitHub 中的 pr-workflow 分支::

        # 删除本地 pr-workflow 分支
        $ git branch -D pr-workflow

        # 删除个人 GitHub 上的远程 pr-workflow 分支，也可以在 GitHub 上点击按钮删除分支
        $ git push origin :pr-workflow
