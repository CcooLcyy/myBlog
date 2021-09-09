---
title: HTML
date: 2021-06-27 23:06:45
tags:
---

# 浏览器内核

指的是渲染引擎，包括渲染引擎和JS引擎

## Trident

Trident，国内双核浏览器其中一核就是IE的trident内核，在win10发布之后，新内核为EdgeHTML内核

## Gecko

火狐内核，开源，但是flash慢

## webkit

苹果内核

## blink

谷歌内核，是webkit内核的分支。

## Presto

早期的opera使用的内核，现在使用的是blink内核

# web标准

不是某一个标准，是由W3C制定的。有三部分组成，结构、表现、行为构成的。

## 结构标准

对网页元素进行整理和分类，包含HTML和XML

## 样式标准

设置网页元素的板式、颜色、大小等样式外观，主要用CSS

## 行为标准

定义交互式，包括DOM和JS

# 什么是HTML

HTML是用来描述网页的一种语言。HTML（Hyper Text Markup Language）他并不是一种编程语言，是一种标记语言

# 一些概念

## 标签

标签是由尖括号包围的关键词，比如`<html></html>`，他有开始标签和结束标签，但并不是所有的标签都有开始和结束标签，比如`<br>`换行标签

HTML就是网页，里面包含了其他的东西，可以描述网页，可以制定网页的标题等等。也就是说标签`<html></html>`，并不是里面所有东西都能显示出来。

通常来说，如果忘记了结束标签，浏览器也能正确渲染，但是十分不建议忘记结束标签，在之后的XHTML中会对结束标签进行严格检查。

**需要注意的是，没有结束标签的标签比如`<br>`正确的写法是`<br />`，尽管我们只写`<br>`浏览器也能识别，但是规范就是规范，存在不是没有意义的。**

## 元素

开始标签到结束标签的所有代码。注意和元素内容做区分，元素内容是开始标签和结束标签之间的所有内容。

大多数HTML可以进行进行嵌套，最简单的就是

```html
<html>
  <head>
  </head>

  <body>
  </body>
</html>
```

可以看到，在`<html>`标签之间还嵌入了`<head>`和`<body>`标签。我们允许空的元素，也就是元素在开始标签中就关闭了，最常见的换行标签`<br>`。另外，标签最好使用小写，在XHTML中强制使用小写。

关于空元素的其他要点，在XHTML和XML不允许使用没有结束标签的HTML元素，虽然`<br>`在浏览器中可以正常渲染，但是最好还是使用`<br/>`

## 网站源码

对于一个网站可以使用查看网站源码的方式来看这个网站的源码。

## 属性

属性可以为标签提供更多的信息，并且属性总是以键值对的形式出现，而且是在开始标签中规定的。

**属性的值要始终在引号，另外要注意单引号和双引号，当值中有单引号则外侧要使用双引号，反之。**

链接标签`<a herf="url"></a>`就是一个很好的例子。

### 布尔属性

有些没有值的属性，他么是合法的，这些属性被称为布尔属性，他们的值和他们的属性名一致。`disabled`就是这样的属性。

```html
<input type="test" disabled></input>
```

这个属性可以标记表单不可用。

## 浏览器渲染效果

我们无法确定HTML在不同浏览器中的确切效果，因此我们不能使用类似段落等方式进行换行。而且，使用`<p>`进行换行的话，之后会空一行，同样我们可以使用CSS来调整格式，但这纯属脱裤子放屁。要换行就是用`<br>`换行。

## 样式

HTML使用style属性改变样式。

## 颜色



# 标签用法

## `<HTML>`标签

根标签，这个标签就是整个网页，所有的标签都在这个标签中。所有元素必须是此元素的后代。

## 注释

`<!--这是一个注释-->`

注释内容不会被浏览器渲染，开始标签有一个惊叹号，但是在结束的标签中没有。注释可以帮助记录信息。

## `<head>`

head里面可以有`meta`，元数据。这是用来描述数据的数据。

```html
<meta charset="utf-8">
<meta name="author" content="Daniel">
```

指定页面描述可以让页面在搜索引擎的相关描述里出现的更多。

`<meta name="keyword" content="many keywords">`这种方法已经不再适用，搜索引擎会忽略。

## `<base>`标签

这个标签全文只有一个，而且在`<head>`标签中。如果有多个`<base>`元素，只会使用第一个定义的`target`和`herf`的值。

## `<link>`

用于链接外部资源。

使用属性`herf`设置外部资源的路径，用`rel`（关系）设置值为`stylesheet`

除了链接样式表之外还可以链接网站图标

```html
<link rel="icon" herf="./favicon.ico">
```

在不同的移动平台上的特殊图表类型。

```html
<link rel="apple-touch-icon-precomposed" sizes="114x114"
      href="apple-icon-114.png" type="image/png">
```

`size`表示图标大小`type`包含链接资源的MIME类型。

## `<title>`

在`<head>`标签中，用于显示页面的标题

## `<style>`

在这里面插入css格式，也就是内部样式表，这个我还是更喜欢用外联样式。这是一种用来改变元素样式的属性。他是从HTML4开始支持的，现代的浏览器基本都能支持style属性。

对页面的效果要用样式CSS来渲染而不是使用标签

## `<meta>`

这是一个空元素，用于不能由其他HTML元相关元素表示的任何元数据信息。

`charset`属性，使用了这个属性，值必须是`utf-8`。

### 使用`http-equiv`自动刷新页面

首先我们要用`http-equiv`来指定`refresh`使用`<meta>`的`content`来指定刷新时间和刷新的地址，刷新时间单位是秒

```html
<meta http-equiv="refresh" content="3;url=https://example.com">
```

每三秒钟刷新一次网页，指向的地址是;url=后的地址。要注意的是，设置自动刷新之后可能会影响网站的可读性。

## 主体

`<body></body>`

定义了HTML文档的主体，也就是网页的页面部分。

## 段落

`<p></p>`

指出在这组标签当中是段落，同样，也不应使用段落来进行换行

## 段内换行

`<br>`

同样这是一个没有结束标签的标签，

## 水平线

`<hr>`

在HTML页面创建一根水平线，用于分割内容。

## <span id='anchor'>链接</span>

`<a></a>`

既然是浏览器中使用的语言那肯定得能让浏览器进行跳转，超链接就是这样定义的，a是anchor也就是锚。

值得注意的是，在链接的后面一定要添加一个斜杠`/`，不然服务器会进行两次HTTP请求，也就是要这么写`<a href="http://www.danielsblogs.top/">`，这样可以减小服务器的压力。

```html
<a herf="http://www.danielsblogs.top/">个人博客链接</a>
```

属性herf后面是超链接链接到的站点，而标签中间的文字是在网页中显示出来的文字。

### target属性

可以控制页面在何处打开`<a href="url" target="_blank"></a>`这样可以使网页在新的页面打开。

### name属性

这个属性可以规定anchor的名称，在属性中创建HTML页面的书签，同样浏览器也是不渲染书签的，但是我们可以通过书签来进行跳转。我们可以使用这种操作来让使用者不必不停滑动页面来浏览需要的信息。

```html
<a href="url" name="label">
</a>
```

同样我们可以使用id属性来代替name属性，命名锚同样有效。当然因为name是靠#来进行引用，因此我们的定向链接应该这么写。

```html
<!--定向链接-->
<a herf="#tips"></a>

<!--目标链接-->
<a herf="url" id]="tips"></a>
```

同时如果找不到定义的命名锚则会定位到文档的顶端。

## 电子邮件链接

发送电子邮件的链接。

```html
<a href="mailto:Cheng_mmm@iCloud.com">向我发邮件</a>
```

邮件地址是可选的，如果只写了`mailto`会打开邮件客户端，但是没有收件人地址信息。

## 图像

`<img></img>`

这是一个空标签，也就是说没有闭合标签。

顾名思义就是在网页上显示图像我们通过属性：src来定位图像的位置，并且可以使用width和height来制定图像的大小。img标签也没有结束标签

同时加载图片需要时间，而且还要考虑使用纯文本浏览器的用户。

```html
<img src="url.jpg" width="xx" height="xx">
```

### alt属性

如果图片是无法显示那么就会显示替换文本，只有当图片无法显示的时候会出现替换文本。

```html
<img src="url" alt="imagetext">
```

### title属性

## 引用

### 短引用

`<q></q>`

通常是在段落中的一段话

### 长引用

`blockquote`

通常就是用来引用节，同时浏览器会对长引用元素进行缩进处理。

## 引用出处

`<cite>`

在W3C标准中允许在次元素中包含作者信息，但是WHATWG规范不允许出现人名。浏览器默认使用斜体来展示此元素中的内容。

## 缩略词

`<abbr></abbr>`

可以提供额外的信息。

## 定义著作的标题

`<cite></cite>`

定义一个著作的标题，通常也会使用斜体来进行显示。

## 插入层叠样式表CSS

### 外部样式表

可以通过一个文件来改变整个网站的样式，外部样式表要在头部插入。

```html
<head>
<link rel="style" type="text/css" href="<cssname.css>">
</head>
```

### 内部样式表

内部样式表同样也得在`<head>`进行定义

```html
<head>
<style type="text/css">
	body{background-color: red}
</style>
</head>
```

### 内联样式

特殊的样式需要使用的时候，可以使用内联样式直接改变特定的属性。

## 表格

`<table></table>`

在表格中的内容，行用`<tr></tr>`来定义，在行内使用`<td></td>`来定义每一个列

我们要注意，就算表格有空个也要用`<td></td>`来进行占位。

### 边框属性

`<table border="1"></border>`

这样会让表格带有一个边框属性。

### 表格的表头

`<th></th>`

将表头放在表格的第一行

## 列表

列表分为有序列表和无序列表

### 无序列表

`<ul></ul>`

无序列表是用粗体的远点进行标记

​	`<li></li>`

​	中间的项目用上面的标记

### 有序列表

`<ol></ol>`

有序列表就是用数字进行标记的列表

​	同样的，每一个列表内容都是用`<li></li>`来进行标记

## 无语意元素`<div><span>`

`<div>`是块级元素，通用性流内容容器，在不适用CSS的情况下对内容布局没有影响。可以用于组合其他html元素，他们没有特别的定义，一般用于对大的内容块联合CSS来进行样式的设置。

主要的作用就是将内容进行分组。仅当没有其他语意元素的情况下使用。

`<span>`是html元素的内联元素，用作文本的容器，他也没有特定的含义，这是联合CSS设置部分文本的样式属性。

## 类与id

类和id或者name类似，也是一种命名标签的方法，区别就是，id是唯一的，但是类（class）可以在多个标签中命名同样的类

id的大小写是敏感的，并且至少包含一个字符，不能有空白字符，制表符或者空格。

另外在<a href='#anchor'>链接</a>那一节当中也有写过，我们可以使用id在同一页内进行锚定。

## 在网页中显示其他网页

`<iframe></iframe>`

### 设置宽度高度属性

属性值默认的单位是像素

```html
<iframe src="url" width="200px" height="200px">
```

### 边框属性

```html
<iframe src="url" frameborder="0"></iframe>
```

## 为文档设定语言

通过`long`属性在`<html>`标签中设置语言，

```html
<html lang="zh-CN">
```

## 表单

提供了可以提交到网站或者应用程序的表单。

### 按钮

`<button>`用于表示一个可以点击的按钮，可通过CSS来改变按钮样貌。

## 视频

`<video>`可以在标签中制定多个源，浏览器会使用第一个支持的源。

```html
<video controls>
  <souce src=".mp4" type="video/mp4">  
</video>
```

如果没有制定控件属性，视频不会展示浏览器自带的控件，可以用js来创建自己的控件。

如果指定了`controls`属性，那么可以使用`controlslist`来定义一下浏览器播放控件常用的值有`nodownload nofullscreen noremoteplayback`

## canvas

可以通过js绘制图形或图形动画。此标签需要闭合。在CSS中`width`和`height`属性用来调整渲染期间缩放图像以适应样式大小，如果元素展示变形，要使用html中的自带的`height 和 width`聊调整。

`height`该元素占用的空间高度，CSS像素表示默认150

`moz-opaque`控制元素是否半透明

`width`元素占用空间宽度，默认300

# 构建网页的HTML

一般的网页规划。

## 页眉

`<header></header>`，是简介形式的内容，如果是`<body>`的子目录那么他就是网站的全局页眉，如果是`<article>`中的那么就是这部分的特有页眉。

## 导航栏

`<nav></nav>`：包含主页的导航功能，不应包含二级链接等内容。

## 主内容

`<main></main>`主内容中还有各种子内容区段`<article><section><div>`

用于存放每个页面独有的内容，每个页面只能用一次，并且直接位于`<body>`中，不要把他嵌套进其他元素中。

`<article>`：包围的内容是每一篇文章，与页面其他内容无关

`<section>`：用于组织页面使其按照功能分块。

## 侧边栏

`<aside></aside>`侧边栏经常嵌套在`<main>`中。侧边栏可以放其他东西，作者简介相关链接等。

## 页脚

`<footer></footer>`

## 标题

`<h1~6></h1~6>`

一共有六个标题，虽然标题会让文本加粗加大，但是不能通过标题来控制文本的加粗或大字体，标签的作用是用来告诉浏览器或者搜索引擎他们的性质，而不是让浏览器渲染出加粗或者是大字号。

## 地址

`<address></address>`

表示其中HTML提供了某个人或组织的联系信息。










