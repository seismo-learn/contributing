# 维护者备忘单

以下总结地震“学”维护者的部分注意事项。

## 新建 Sphinx 文档

新建文档时，可以直接复制已存在文档的配置和相关目录及文件（如[地震“学”科研入门教程](https://github.com/seismo-learn/seismology101)），
并做进一步修改。例如，{file}`Makefile`、{file}`make.bat`、
{file}`requirements.txt`、{file}`source/conf.py`、{file}`source/_static/`、
{file}`source/_templates/`、{file}`source/index.rst`、{file}`.gitignore`、
{file}`.github/`、{file}`README.md` 等。

也可以使用 `sphinx-quickstart` 命令新建文档，再参考已存在文档进行配置。简要介绍该命令
的一些常见选项:

```
# 新建文档
$ sphinx-quickstart
...
> Separate source and build directories (y/n) [n]: y
> Author name(s): seismo-learn
> Project release []:
> Project language [en]: zh_CN

# 查看新建文档
$ ls
build  make.bat  Makefile  source
$ ls source
conf.py  index.rst  _static  _templates
```

## GitHub 仓库设置

地震“学”所有文档源码托管在 [GitHub](https://github.com/seismo-learn) 上。
我们一般对 GitHub 上托管的文档仓库做一定设置。可以参考已存在的仓库进行配置，如[地震“学”科研入门教程](https://github.com/seismo-learn/seismology101)。

在 “Settings” 的 “Options” 选项中：

- “Features” 不使用 Wikis、Projects、Sponsorships
- “Merge button” 选择 Allow squash merging、Allow auto-merge、Automatically delete head branches
- “GitHub Pages” 的 Source 选择 gh-pages 分支，并勾选 Enforce HTTPS

在 “Settings” 的 “Branches” 选项中，设置 main 分支的保护规则。

在 “Settings” 的 “Secrets” 选项中，设置 Organization secrets。

## 命令行工具

我们使用 git 进行版本控制，一些编辑器或 IDE 也集成了 git。此外，也可以使用一些高效的
命令行工具。

[GitHub CLI](https://cli.github.com/) 是 GitHub 官方命令行工具，可以在终端中处理
Pull Request、Issue 等，例如:

```
# 提交 Pull Request
$ gh pr create

# 提交 Pull Request，并申请 Reviewers
$ gh pr create -r core-man,seisman
```

[hub](https://hub.github.com/) 是 git 的一个扩展，常用于同步本地和远程分支:

```
$ hub sync
```
