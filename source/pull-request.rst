Pull Request 流程
==================

本章主要介绍如何修改地震“学”文档的源码并提交 Pull Request（拉取请求，简称 PR）:

-  若只是对文档做简单的微调，比如修改简单的别字、语句不通或不清晰的描述等，可以直接 `Github 在线修改提交`_\ 。
-  若需要对文档做大量修改，比如新增章节、调整章节结构等，请先到项目主页提交 Issue，由众多维护者一起讨论是否有必要做修改。
   若有必要修改，再选择\ `线下修改提交`_\ 。

Github 在线修改提交
-------------------

1.  在线修改

    点击文档网页右上角的 “Edit on GitHub”，网页会自动跳转到文档源码文件。点击源码右上方的铅笔符号
    “Edit this file”，即可在线修改。此过程会自动为维护者 fork 项目仓库。

2.  提交修改

    修改完毕后，在下方的 “Commit changes” 中输入有关此次修改的标题（必填）和具体描述（可选）。输入一个简短的新分支名字。
    点击 “Commit changes” 提交修改。

3.  提交 PR

    最后在 “Open a pull request” 页面中，输入此 PR 的标题和具体描述。选择 Reviewers。点击 “Create pull request” 即可。

线下修改提交
------------

以下步骤以\ `地震“学”科研入门教程 <https://seismo-learn.org/seismology101/>`__\ 为例，即修改其他文档时做简单替换即可，例如：

- 修改文档\ `地震“学”软件 <https://seismo-learn.org/software/>`__\ : 将 ``seismology101`` 改成 ``software``
- 修改文档\ `地震“学”基础 <https://seismo-learn.org/software/>`__\ : 将 ``seismology101`` 改成 ``seismology``

以下步骤假定你的 GitHub 账户名为 ``seismology-freshman``\ 。

克隆和复制仓库
^^^^^^^^^^^^^^

1.  复制仓库至个人 GitHub 帐号

    点击项目主页 https://github.com/seismo-learn/seismology101 右上角的 Fork 按钮，将该项目复制到你的 GitHub 账户下。
    复制完成后，你的 GitHub 帐号下便有了 https://github.com/seismology-freshman/seismology101 仓库。

2.  克隆《地震“学”科研入门教程》源码到本地计算机::

        # 进入 ~/Downloads 目录，也可以选择其他目录存放文档源码
        $ cd ~/Downloads

        # 克隆《地震“学”科研入门教程》源码
        $ git clone --depth=50 https://github.com/seismo-learn/seismology101.git

3.  添加个人 GitHub 帐号中的复制仓库作为远程，并命名为 seismology-freshman::

        # 进入 ~/Downloads/seismology101 目录
        $ cd ~/Downloads/seismology101/

        # 添加个人 GitHub 帐号中的复制仓库作为远程，并命名为 seismology-freshman
        $ git remote add seismology-freshman https://github.com/seismology-freshman/seismology101.git

修改文档
^^^^^^^^

1.  创建并切换至新分支，假定新分支名为 ``myfeature``::

        # 切换到本地的 main 分支
        $ git checkout main

        # 创建并切换至 myfeature 分支
        $ git checkout -b myfeature

2.  在新建分支中对文档做修改，并提交 commit（此过程可以循环多次）::

        $ git status
        $ git add --all

        $ git status
        $ git commit -m "此处填写本次提交的注释信息"

3.  参考\ :doc:`building`\ ，在本地编译生成 HTML 格式的文档并检查

.. note::

   开发 myfeature 分支的过程中，官方 main 分支可能已经更新。因此，需要经常同步最新版的官方 main 分支。

   1.  同步本地和官方 main 分支::

           # 切换到 main 分支
           $ git checkout main

           # 获取官方 main 分支，并合并到本地 main 分支
           $ git pull origin main

   2.  将 myfeature 分支基于最新的 main 分支::

           # 切换到 myfeature 分支
           $ git checkout myfeature

           # 将 myfeature 分支基于最新的 main 分支
           $ git rebase main

.. note::

   分支开发的过程中，可能会有很多次 commit，某些 commit 可能不那么重要。可以将多个 commit
   压缩成一个或若干个 commit，这样不仅清晰，也容易管理::

       $ git rebase -i main

提交 PR
^^^^^^^^

1.  推送 myfeature 分支至个人 GitHub 帐号中（即远程 seismology-freshman）::

        $ git push seismology-freshman myfeature

2.  提交 PR

    进入个人 GitHub 下复制的仓库 https://github.com/seismology-freshman/seismology101。
    一般 GitHub 会自动提示有更新可提交 PR，点击 “Compare & pull request”，输入此 PR 的标题和具体描述，
    选择 Reviewers。最后点击 “Create pull request” 即可。

3.  地震“学”维护者收到 PR 后，会对代码进行审核、评论以及修改，并决定是否接受或结束该 PR
4.  PR 被接受后，则可以删除本地和个人 GitHub 上的 myfeature 分支::

        # 切换回本地 main 分支
        $ git checkout main

        # 获取官方 main 分支，并合并到本地 main 分支
        $ git pull origin main

        # 删除本地 myfeature 分支
        $ git branch -D myfeature

        # 删除个人 GitHub 上的远程 myfeature 分支，也可以在 GitHub 上点击按钮删除分支
        $ git push seismology-freshman :myfeature
