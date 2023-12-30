---
title:  hexo博客中tags与categories用法
tags:  hexo
categories: [hexo,用法]

---

[hexo博客中tags与categories用法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/348131730)

### tags与categories

在hexo中使用tags与categories往往需要使用多标签和多分类,这里记录一下它们的用法。

### tag

用法：

```text
tags:
  - 123
  - 456
tags: [123, 456]
```

多标签写法，这2种都是一样的效果，用哪个都可以，建议使用列表[]式，直观清晰。

### categories

```text
# 这是默认的写法，给文章添加一个分类。
categories: 123
# 这会将文章分类123/456子分类目录下。
categories: [123, 456]
这会将文章分类到123/456子分类目录下。
categories:
   - 123
   - 456
多标签写法，文章被分类到123、456以及123的自分类789这3个分类下面，官方指定写法。
categories:
   - [123]
   - [456]
   - [123, 789]
```

### Tag 插件

#### 便签

在 markdown 中加入如下的代码来使用便签：

```markdown
{% note success %}
文字 或者 `markdown` 均可
{% endnote %}
```

或者使用 HTML 形式：

```html
<p class="note note-primary">标签</p>
```

可选便签：

primary

secondary

success

danger

warning

info

light

WARNING

使用时 `{% note primary %}` 和 `{% endnote %}` 需单独一行，否则会出现问题

#### [#](https://hexo.fluid-dev.com/docs/guide/#行内标签)行内标签

在 markdown 中加入如下的代码来使用 Label：

```markdown
{% label primary @text %}
```

或者使用 HTML 形式：

```html
<span class="label label-primary">Label</span>
```

可选 Label：

primary default info success warning danger

#### [#](https://hexo.fluid-dev.com/docs/guide/#折叠块)折叠块

使用折叠块，可以折叠代码、图片、文字等任何内容，你可以在 markdown 中按如下格式：

```markdown
{% fold info @title %}
需要折叠的一段内容，支持 markdown
{% endfold %}
```

info: 和行内标签类似的可选参数 title: 折叠块上的标题

#### [#](https://hexo.fluid-dev.com/docs/guide/#勾选框)勾选框

在 markdown 中加入如下的代码来使用 Checkbox：

```markdown
{% cb text, checked?, incline? %}
```

text：显示的文字
checked：默认是否已勾选，默认 false
incline: 是否内联（可以理解为后面的文字是否换行），默认 false

示例：

{% cb 普通示例 %}

{% cb 默认选中, true %}

{% cb 内联示例, false, true %} 后面文字不换行

{% cb false %} 也可以只传入一个参数，文字写在后边（这样不支持外联）



#### [#](https://hexo.fluid-dev.com/docs/guide/#按钮)按钮

你可以在 markdown 中加入如下的代码来使用 Button：

```markdown
{% btn url, text, title %}
```

或者使用 HTML 形式：

```html
<a class="btn" href="url" title="title">text</a>
```

url：跳转链接
text：显示的文字
title：鼠标悬停时显示的文字（可选）

[text](javascript:;)

#### [#](https://hexo.fluid-dev.com/docs/guide/#组图)组图

如果想把多张图片按一定布局组合显示，你可以在 markdown 中按如下格式：

```markdown
{% gi total n1-n2-... %}
  ![](url)
  ![](url)
  ![](url)
  ![](url)
  ![](url)
{% endgi %}
```

total：图片总数量，对应中间包含的图片 url 数量
n1-n2-...：每行的图片数量，可以省略，默认单行最多 3 张图，求和必须相等于 total，否则按默认样式

如下图为 `{% gi 5 3-2 %}` 示例，代表共 5 张图，第一行 3 张图，第二行 2 张图。

![Group Images](https://hexo.fluid-dev.com/docs/assets/img/group_image.c1b58381.png)