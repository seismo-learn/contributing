# 构建网站

## Jupyter Book 构建网站

地震“学”所有教程网站都使用文档生成工具 [Jupyter Book](https://jupyterbook.org/) 构建。
读者可以按照如下步骤在自己的计算机上构建网站。

````{dropdown} 安装 git 和 Python
以下步骤假定用户已安装版本控制工具 git 和 Python。

若未安装 git，可以使用以下命令安装或更新 git：

若未安装 Python，建议通过 :doc:`Anaconda <software:anaconda/index>`  来安装和管理 Python。
````

:::{note}
以下步骤以[地震“学”科研入门教程](https://seismo-learn.org/seismology101/)为例。
构建其他文档时只需做简单替换即可：

- 构建文档[地震“学”软件](https://seismo-learn.org/software/): 将 `seismology101` 改成 `software`
- 构建文档[地震“学”参考书](https://seismo-learn.org/seismology/): 将 `seismology101` 改成 `seismology`
:::

1. 下载文档源码
   ```
   # 克隆源码，并进入源码目录
   $ git clone --depth=50 https://github.com/seismo-learn/seismology101.git
   $ cd seismology101
   ```

2. 创建虚拟环境
   ```
   $ conda env create -f environment.yml
   ```

3. 编译生成 HTML 格式的文档
   ```
   $ conda activate seismo-learn
   $ make html
   ```

4. 生成的文档位于 {file}`_build/html/` 目录下，直接用浏览器打开
   {file}`_build/html/index.html` 即可在本地预览。

## Hugo 构建网站

[地震学主站](https://seismo-learn.org/)和[地震“学”链接](https://seismo-learn.org/links/)是由静态网站生成器 [Hugo](https://gohugo.io/) 构建生成的，具体构建方法请参考他们
源码网址里的 {file}`README.md` 文件。此外，[地震“学”链接](https://seismo-learn.org/links/)使用的主题是我们基于 [Bootstrap](https://getbootstrap.com/) 框架和 [Font Awesome](https://fontawesome.com/)
精美图标自定义的。
