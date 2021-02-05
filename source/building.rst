构建网站
========

地震“学”的网站使用文档生成工具 `Sphinx <http://www.sphinx-doc.org/>`__ 构建。
读者可以按照如下步骤在自己的计算机上构建网站。

.. note::

    以下步骤以 `地震“学”科研入门教程 <https://seismo-learn.org/seismology101/>`__ 为例。
    构建其他文档时只需做简单替换即可：

    - 构建文档 `地震“学”软件 <https://seismo-learn.org/software/>`__: 将 ``seismology101`` 改成 ``software``
    - 构建文档 `地震“学”基础 <https://seismo-learn.org/software/>`__: 将 ``seismology101`` 改成 ``seismology``

1.  下载文档源码

    ::

        $ git clone --depth=50 https://github.com/seismo-learn/seismology101.git

2.  安装 Sphinx

    可以使用 ``pip`` 安装 Sphinx::

        $ pip install sphinx

3.  安装文档所需依赖

    ::

        $ cd seismology101/
        $ pip install -r requirements.txt

4.  编译生成 HTML 格式的文档

    ::

        $ make html

5.  生成的文档位于 :file:`build/html/` 目录下，可以直接用浏览器打开
    :file:`build/html/index.html` 即可在本地预览。
