# 维护者备忘单

以下总结地震“学”维护者的部分注意事项。

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
