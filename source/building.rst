构建网站
========

Sphinx 构建网站
---------------

地震“学”所有教程网站都使用文档生成工具 `Sphinx <http://www.sphinx-doc.org/>`__ 构建。
读者可以按照如下步骤在自己的计算机上构建网站。

.. dropdown:: :fa:`exclamation-circle,mr-1` 安装 git 和 Python
   :container: + shadow
   :title: bg-info text-white font-weight-bold 

    以下步骤假定用户已安装版本控制工具 git 和 Python。

    若未安装 git，可以使用以下命令安装或更新 git：

    .. include:: install-git.rst_

    若未安装 Python，建议通过 :doc:`Anaconda <software:anaconda/index>`  来安装和管理 Python。

.. note::

    以下步骤以\ `地震“学”科研入门教程 <https://seismo-learn.org/seismology101/>`__\ 为例。
    构建其他文档时只需做简单替换即可：

    - 构建文档\ `地震“学”软件 <https://seismo-learn.org/software/>`__: 将 ``seismology101`` 改成 ``software``
    - 构建文档\ `地震“学”参考书 <https://seismo-learn.org/seismology/>`__: 将 ``seismology101`` 改成 ``seismology``

1.  下载文档源码

    ::

        # 假设将源码下载到 ~/Downloads/ 目录下，切换至该目录
        $ cd ~/Downloads/

        # 克隆源码
        $ git clone --depth=50 https://github.com/seismo-learn/seismology101.git

2.  安装 Sphinx 等文档所需依赖

    ::

        # 进入下载的源码目录
        $ cd ~/Downloads/seismology101/

        # 安装依赖
        $ pip install -r requirements.txt

3.  编译生成 HTML 格式的文档

    ::

        $ make html

4.  生成的文档位于 :file:`build/html/` 目录下，直接用浏览器打开
    :file:`build/html/index.html` 即可在本地预览。


Hugo 构建网站
-------------

`地震学主站 <https://seismo-learn.org/>`__\ 和\ `地震“学”链接 <https://seismo-learn.org/links/>`__\
是由静态网站生成器 `Hugo <https://gohugo.io/>`__ 构建生成的，具体构建方法请参考他们
源码网址里的 :file:`README.md` 文件。此外，`地震“学”链接 <https://seismo-learn.org/links/>`__\
使用的主题是我们基于 `Bootstrap <https://getbootstrap.com/>`__ 框架和 `Font Awesome <https://fontawesome.com/>`__
精美图标自定义的。
