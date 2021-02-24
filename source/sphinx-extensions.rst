Sphinx 扩展
============

地震“学”文档使用了一些 Sphinx 扩展，以便简洁而有效地组织文档内容。本章主要介绍常用扩展的
常用用法。

sphinx-panels
--------------

`sphinx-panels <https://github.com/executablebooks/sphinx-panels>`__ 扩展的指令
在组织文档内容方面具有十分强大的功能。这里主要介绍几个常用指令的常用用法，更多指令及其用法
请参考\ `官方文档 <https://sphinx-panels.readthedocs.io/en/latest/>`__\ 。
一些指令使用的一些参数的具体含义需要了解 `Bootstrap <https://getbootstrap.com/>`__\ 。

dropdown 指令
^^^^^^^^^^^^^^

.. raw:: html

   <div style="float: left; width:98%">

.. literalinclude:: sphinx-panels-dropdown.rst_

以上内容的显示效果：

.. raw:: html

   <div style="float: left; width:98%">

.. include:: sphinx-panels-dropdown.rst_

.. raw:: html

   </div>

tabbed 指令
^^^^^^^^^^^^^

使用 ``tabbed`` 指令可以使文档内容以选项卡的形式显示。例如，不同操作系统下安装 git：

.. raw:: html

   <div style="float: left; width:98%">

.. literalinclude:: sphinx-panels-tabbed.rst_

以上内容的显示效果：

.. raw:: html

   <div style="float: left; width:98%">

.. include:: sphinx-panels-tabbed.rst_

panels 指令
^^^^^^^^^^^^

使用 ``panels`` 指令可以使文档内容以网格布局的形式显示。例如，使用卡片布局（card layout）：

.. raw:: html

   <div style="float: left; width:98%">

.. literalinclude:: sphinx-panels-panels.rst_

以上布局的显示效果：

.. raw:: html

   <div style="float: left; width:98%">

.. include:: sphinx-panels-panels.rst_

简要介绍该指令中使用的一些参数。container 参数：

- ``container-lg``\ ：控制内容的总宽度（详细请参考 `Bootstrap: containers <https://getbootstrap.com/docs/4.4/layout/overview/#containers>`__\ ）
- ``pb-3``\ ：行之间的空白距离（pb 即 bottom padding）是某常数的 3 倍（详细请参考 `Bootstrap: spacing <https://getbootstrap.com/docs/4.0/utilities/spacing/>`__\ ）

column 参数中 lg、md、sm、xs 分别表示不同大小的设备（即大型、中型、小型、超小型），
而 Bootstrap 将每行分成 12 个部分，因此：

- ``col-lg-3``\ ：对于大型设备，每一列占 3 个部分，所以每行有 4 列
- ``col-md-3``\ ：对于中型设备，每一列占 3 个部分，所以每行有 4 列
- ``col-sm-4``\ ：对于小型设备，每一列占 4 个部分，所以每行有 3 列
- ``col-xs-6``\ ：对于超小设备，每一列占 6 个部分，所以每行有 2 列
- ``p-2``\ ： 列之间的空白距离是某常数的 3 倍
