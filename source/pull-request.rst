Pull Request 流程
==================

本章主要介绍如何修改地震“学”文档的源码并提交 Pull Request（拉取请求，简称 PR）:

-  若只是对文档做简单的微调，比如修改简单的别字、语句不通或不清晰的描述等，可以直接 `Github 在线修改并提交`_\ 。
-  若需要对文档做大量修改，比如新增章节、调整章节结构等，请先到项目主页提交 Issue，由维护者一起讨论是否有必要做修改。
   如果已存在与您想做的修改相关的 Issue，请直接在该 Issue 下直接留言，以让我们知道您打算做什么。
   若相关修改经过讨论确认需要执行后，可选择\ `线下修改并提交`_\ 。

Github 在线修改并提交
---------------------

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

以下步骤以\ `地震“学”科研入门教程 <https://seismo-learn.org/seismology101/>`__\ 为例，即修改其他文档时做简单替换即可，例如：

- 修改文档\ `地震“学”软件 <https://seismo-learn.org/software/>`__\ : 将 ``seismology101`` 改成 ``software``
- 修改文档\ `地震“学”基础 <https://seismo-learn.org/software/>`__\ : 将 ``seismology101`` 改成 ``seismology``

以下步骤假定用户的 GitHub 账户名为 ``seismology-freshman``\ 。

以上步骤使用了 git 的常用选项，可以参考以下学习资料学习更多用法：

- `git 简明指南 <http://rogerdudler.github.io/git-guide/index.zh.html>`__
- `GotGitHub <http://www.worldhello.net/gotgithub/index.html>`__
- `廖雪峰的 Git 教程 <http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000>`__
- `Pro Git <https://git-scm.com/book/zh/v2>`__

克隆和复制仓库
^^^^^^^^^^^^^^

1.  复制仓库至个人 GitHub 帐号

    点击项目主页 https://github.com/seismo-learn/seismology101 右上角的 Fork 按钮，将该项目复制到你的 GitHub 账户下。
    复制完成后，你的 GitHub 帐号下便有了 https://github.com/seismology-freshman/seismology101 仓库。

2.  克隆文档源码到本地计算机::

        # 进入 ~/Downloads 目录，也可以选择其他目录存放文档源码
        $ cd ~/Downloads

        # 克隆《地震“学”科研入门教程》源码。官方仓库默认是远程 origin
        $ git clone --depth=50 https://github.com/seismo-learn/seismology101.git

3.  添加个人 GitHub 帐号中的复制仓库作为远程，并命名为 seismology-freshman::

        # 进入 ~/Downloads/seismology101 目录
        $ cd ~/Downloads/seismology101/

        # 添加个人 GitHub 帐号中的复制仓库作为远程，并命名为 seismology-freshman
        $ git remote add seismology-freshman https://github.com/seismology-freshman/seismology101.git

.. note::

   上述三个步骤只需在第一次修改代码时执行一次。一旦复制或克隆某仓库后，就无需再次克隆或复制。

   设置并使用 SSH 秘钥在本地和 GitHub 仓库之间的进行传输的读者，可以使用 git@github.com:seismo-learn/seismology101.git
   和 git@github.com:seismology-freshman/seismology101.git，分别代替 https://github.com/seismo-learn/seismology101.git
   和 https://github.com/seismology-freshman/seismology101.git。

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

3.  修改过程中，可以参考\ :doc:`building`\ ，随时在本地构建文档并检查修改效果

.. note::

   开发 pr-workflow 分支的过程中，官方 main 分支可能已经更新。因此，需要经常同步最新版的官方 main 分支。

   1.  同步本地和官方 main 分支::

           # 切换到 main 分支
           $ git checkout main

           # 获取官方 main 分支，并合并到本地 main 分支
           $ git pull origin main

   2.  将 pr-workflow 分支基于最新的 main 分支::

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

1.  推送 pr-workflow 分支至远程 seismology-freshman（即个人 GitHub 帐号中的复制仓库）::

        $ git push seismology-freshman pr-workflow

2.  提交 PR

    进入个人 GitHub 帐号下的复制仓库 https://github.com/seismology-freshman/seismology101。
    一般 GitHub 会自动提示有可提交的 PR，点击 “Compare & pull request”，输入此 PR 的标题和具体描述，
    选择 Reviewers。最后点击 “Create pull request” 即可。

3.  审核、评论以及修改 PR

    地震“学”维护者收到 PR 后，会对代码进行审核、评论以及修改，并决定是否接受或结束该 PR。

    提交的 PR 在接收前可能需要读者多次修改。这种情况并不要创建新的拉取请求，只需继续本地 pr-workflow 分支中修改并提交，
    然后再次推送 pr-workflow 分支至远程 seismology-freshman 即可，修改将自动添加到已提交的 PR 中。
    推送新的修改后，可以选择在该 PR 中留言或再次请求 Reviewers，来通知 Reviewers 已提交新的修改。

4.  PR 被接受后，则可以更新 main 分支，并删除 pr-workflow 分支::

        # 切换回本地 main 分支
        $ git checkout main

        # 获取官方 main 分支，并合并到本地 main 分支
        $ git pull origin main
        # 更新个人 GitHub 上的 main 分支
        $ git push seismology-freshman main

        # 删除本地 pr-workflow 分支
        $ git branch -D pr-workflow
        # 删除个人 GitHub 上的远程 pr-workflow 分支，也可以在 GitHub 上点击按钮删除分支
        $ git push seismology-freshman :pr-workflow

其他注意事项
-------------

- 每个 PR 应该是一个较小但内容完整的修改
- 较大的修改应分解为较小的，并分别提交 PR
- 错误修复应在单独的 PR 中提交
- 描述您提交的 PR 修改了什么以及为什么需要此 PR，描述越具体越好
- 不要在提交的 PR 中修改与其无关的文件，如 :file:`.gitignore` 等
- commit 的注释信息应该是描述性的，可以参考 `How to Write a Git Commit Message <https://chris.beams.io/posts/git-commit/>`__
- 希望读者对审稿人的评论和意见保持开放的心态，并努力改进代码或文档
- 新的 PR 不一定会及时审核，取决于维护者的当时的工作时间
