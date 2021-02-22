构建网站
========

地震“学”的网站使用文档生成工具 `Sphinx <http://www.sphinx-doc.org/>`__ 构建。
读者可以按照如下步骤在自己的计算机上构建网站。

.. dropdown:: :fa:`exclamation-circle,mr-1` 安装 git 和 Python
   :container: + shadow
   :title: bg-info text-white font-weight-bold 

    以下步骤中，下载文档源码需要版本控制工具 git，安装 Sphinx 和文档所需依赖需要已安装 Python。

    若未安装 git，可以使用以下命令安装或更新 git：

    .. include:: install-git.rst_

    若未安装 Python，建议通过 :doc:`Anaconda <software:anaconda/index>`  来安装和管理 Python。

.. note::

    以下步骤以\ `地震“学”科研入门教程 <https://seismo-learn.org/seismology101/>`__\ 为例。
    构建其他文档时只需做简单替换即可：

    - 构建文档\ `地震“学”软件 <https://seismo-learn.org/software/>`__: 将 ``seismology101`` 改成 ``software``
    - 构建文档\ `地震“学”基础 <https://seismo-learn.org/software/>`__: 将 ``seismology101`` 改成 ``seismology``

1.  下载文档源码

    ::

        # 假设将源码下载到 ~/Downloads/ 目录下，切换至该目录
        $ cd ~/Downloads/

        # 克隆源码
        $ git clone --depth=50 https://github.com/seismo-learn/seismology101.git

2.  安装 Sphinx

    ::

        # 可以使用 Python 自带的工具 pip 来安装 Sphinx
        $ pip install sphinx

3.  安装文档所需依赖

    ::

        # 进入下载的源码目录
        $ cd ~/Downloads/seismology101/

        # 安装依赖
        $ pip install -r requirements.txt

4.  编译生成 HTML 格式的文档

    ::

        $ make html

5.  生成的文档位于 :file:`build/html/` 目录下，可以直接用浏览器打开
    :file:`build/html/index.html` 即可在本地预览。
