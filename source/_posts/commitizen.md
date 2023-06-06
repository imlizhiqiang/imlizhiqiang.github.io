---
title: commitizen:git提交信息规范工具
tags: git
---

#

<!-- more -->

本地全局安装：

```sh
npm install -g commitizen
npm install -g cz-conventional-changelog
```

（如果是 mac 或 linux 系统）在 home 目录下创建`.czrc`文件，并执行：

```sh
echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
```

完毕后即可在任何 git 项目中使用，只需把提交命令改成`git cz`，而不再是以前的`git commit`.

新命令会开启一个交互式的命令行，在最简单的情况下，只需要在`Write a short, imperative tense description of the change (max 94 chars)`这一步填写一个简短的提交说明，其他步骤一律无脑回车跳过即可。
