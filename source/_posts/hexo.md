---
title: 使用hexo在github上写博客(2023)
tags:
    - hexo
---

#

<!-- more -->

## 博客工具：hexo+next 主题

1. 在根目录下执行：`npm install hexo-theme-next@latest --save`.
2. 在`_config.yml`中改动：`theme: next`.
3. 在根目录下创建 next 的配置文件：`cp node_modules/hexo-theme-next/_config.yml _config.next.yml`.

## 博客托管（github pages）/自动构建（github actions）

1. 确保自己的 github 中已经创建名为`<github用户名>.github.io`的仓库。
2. 将本地博客目录的远程 git 仓库地址修改为上述仓库。
3. 添加`.gitignore`文件，`node_modules`和`public`都要包含在该文件中，不要上传到远端。
4. 在根目录下创建`.github/workflows/pages.yml`，并填写如下内容：

```yml
name: Pages

on:
    push:
        branches:
            - main # 注意早期版本可能是master

jobs:
    pages:
        runs-on: ubuntu-latest
        permissions:
            contents: write
        steps:
            - uses: actions/checkout@v2
            - name: Use Node.js 18.x # 与本地node版本一致
              uses: actions/setup-node@v2
              with:
                  node-version: '18' # 与本地node版本一致
            - name: Cache NPM dependencies
              uses: actions/cache@v2
              with:
                  path: node_modules
                  key: ${{ runner.OS }}-npm-cache
                  restore-keys: |
                      ${{ runner.OS }}-npm-cache
            - name: Install Dependencies
              run: npm install
            - name: Build
              run: npm run build
            - name: Deploy
              uses: peaceiris/actions-gh-pages@v3
              with:
                  github_token: ${{ secrets.GITHUB_TOKEN }}
                  publish_dir: ./public
```

注意将上述代码中的 node 版本修改为与本地一致。

最后，在 github 网站上前往存储库的 Settings > Pages > Source，并将 branch 改为 gh-pages。

## 添加自定义域名

1. 在博客目录的`source`文件夹下（注意不是根目录！）添加一个`CNAME`文件，里面的内容是你的域名，比如`www.xxx.com`.
2. 修改 github 仓库的 Settings > Pages > Custom domain 为你的域名，与上述文件中的内容保持一致。
