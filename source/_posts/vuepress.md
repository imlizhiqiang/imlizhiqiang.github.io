# 使用 VuePress 开发静态网站

## 我需要一个统一的静态网站生成器

我想要搭建个人博客，于是我使用 hexo，并搭配 next 主题。

工作和学习中我积累了一些笔记，想要把它们整理成文档库，于是我使用 gitbook。

我想要将它们发布到网上，比如 github.io 或者阿里云自建服务器。

但是在实际的使用过程中，我发现我一直在不同的工具链、插件、主题中来回切换，这让我感觉非常疲倦。

本质上来说，这些工具都是静态网站生成器，它们的产物都是纯粹的静态文件，我希望有一个工具能统一这些需求。

这个工具应该能够：

-   搭建博客，并且提供主题
-   搭建文档库
-   快速编译构建
-   自带部署功能，可发布到常见托管平台，如 github
-   提供一体化的使用体验
-   最好是基于 nodejs

于是我选择 VuePress。

##