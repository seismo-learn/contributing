# 维护指南

读者可以阅读以下维护指南，以便更快、更有效地参与到文档的维护与更新之中。

## 维护与更新

文档的维护与更新主要包括几个方面：

- 修正错别字、语句不通等
- 修正文档中的错误或不清晰的描述
- 修正 reStructuredText 或 Markdown 文件语法错误导致的显示问题
- 调整章节结构，使文档条理更清晰
- 建议或者编写新章节或新文档

可以通过如下几种方式参与文档的维护与更新：

1. 修改文档源码并提交 Pull Request（不熟悉 Pull Request 的读者可以参考 {doc}`pull-request`）
2. 在 GitHub 上的文档源码仓库下提交 Issue
3. 在 GitHub 上的文档源码仓库下的 Discussions 上留言（也可以直接点击文档网页左下角的“参与讨论”）

## 分支模型

GitHub 上托管的文档仓库中存在如下长期分支：

- `main`: 主分支，对应最新版本的文档源码
- `gh-pages`: 存放文档网页的分支，自动更新，无需人工修改

其它分支均属于短期分支，在合并到 `main` 分支后会删除。

## 文档风格

### 文件命名

每个源文件都会被转换成一个单独的网页。因而，确定文件名时应慎重，一旦确定，尽量不要再改动。
由于 Windows 不区分文件名大小写，故而 {file}`option-B.rst` 和 {file}`option-b.rst`
在 Windows 下会出现冲突。我们使用的文件的命名规则是：

- 文件名一律采用小写字母
- 文件名应尽量使用单词全称，避免使用各种形式的简写
- 若文件名中含多个单词，应使用连字符 (hyphen) {kbd}`-` 连接

### 文件风格

1. 所有教程均采用 [reStructuredText](https://docutils.sourceforge.io/rst.html)
   语言编写，可参考 {doc}`restructuredtext` 学习其常用语法。[地震学主站](https://seismo-learn.org/)和[地震“学”链接](https://seismo-learn.org/links/)使用 [Markdown](https://daringfireball.net/projects/markdown/)
   语言编写，可参考 {doc}`Markdown 教程 <seis101:programming/markdown>` 学习其常用语法。
2. reStructuredText 文档的一级标题、二级标题和三级标题，分别用 `=`、`-` 和 `^`
   符号标识
3. 所有 Bash 命令前应加上 Shell 提示符 `$` 以表示该命令为 Shell 命令
4. 中文字符与英文字符和数字之间应加上空格，如 `中文 ABC 中文` 而非 `中文ABC中文`，
   `中文 123 中文` 而非 `中文123中文`
5. 标点符号采用全角，如 `，`、`。`、`：`、`、`、`？` 等。
   标点符号与中文字符、英文字符以及数字之间不需加空格。
6. 图片应在保证清晰度的前提下尽可能小。可以使用 [squoosh 在线工具](https://squoosh.app/)
   进行压缩。