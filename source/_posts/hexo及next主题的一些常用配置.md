---
title: hexo及next主题的一些常用配置
tags:
    - hexo
---

#

<!-- more -->

## 启用标签链接时手动创建页面

使用 next 主题时，可以添加“主页”、“分类”、“标签”、“归档”等链接，除了“主页”和“归档”这两个链接以外，“分类”、“标签”及其他链接都需要有一个单独的页面，这个页面需要手动创建出来。以“标签”链接为例，点击该链接会访问`/tags/`这个路径，如果不创建的话会看到一个报错信息。

在根目录下使用`hexo new page tags`创建页面，并将页面内容改动如下：

```
---
title: 标签
type: tags
---
```

即可。

## 隐藏首页文章预览，使其显示为“标题+阅读全文”

默认情况下，next 会在首页展示文章的题目、预览内容和一个“阅读全文”的按钮，这个预览内容优先显示文章的`description`属性，如果没有该属性，会显示文章的内容，直到文章过长时会截断，显示一个“阅读全文”的按钮，而如果文章很简短，则会全部在首页预览出来，不显示“阅读全文”。

如果要达到一个“空预览”的效果，即主页上每篇文章都只显示“标题+阅读全文”，那么将每一篇博文的开头部分都写成如下形式：

```
---
title: 文章的标题
description: ‘’
---

#

<!-- more -->

文章的正文

## 文章的第一个内容标题
```

在上面的示例中，`<!-- more -->`是 hexo 提供的手动截断预览的功能代码，在这行代码前面的内容将被视为文章的预览内容，而后面则被视为是“阅读全文”按钮打开的内容。hexo 官方推荐用这种方法手动控制到底文章的哪些部分是要预览的。

但是如果要实现“空预览”的效果，直接将这行代码添加到文章的开头是不行的，必须在前面加上一个空的标题符号，让 hexo 生成一个空的一级标题，再将`description`属性置空，即可达成“空预览”的效果。

> 其实这个改动完全是借助 hexo 自身的功能完成，并没有修改任何 next 主题的配置。

## 隐藏 next 文章的创建和修改时间

在 next 的配置文件`_config.next.yml`当中改动如下配置：

```yml
# Post meta display settings
post_meta:
    item_text: true
    created_at: false # 不显示发布时间
    updated_at:
        enable: false # 不显示修改时间
        another_day: true
    categories: true
```

## 打开复制代码功能

在 next 的配置文件`_config.next.yml`当中改动如下配置：

```yml
# Add copy button on codeblock
copy_button:
    enable: true # 打开复制代码功能
    # Available values: default | flat | mac
    style:
```
