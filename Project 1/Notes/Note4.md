## Project 1 Web for a Rock Band Note 4 CSS

现在有了基本的 HTML 模板同过模板应用 CSS 可以在 Web 上实现设计的方案。把所有的 CSS 分别放在几个文件中，一个保存与整体布局有关的样式，一个作为专门的颜色样式表，第三个来保存与版式有关的样式：

- layout.css
- color.css
- typography.css

这些样式表都可以导入到一个基本的样式表中：

`@import url(layout.css)`

`@import url(color.css)`

`@import url(typography.css)`

把包含这三行代码的文件保存为 basic.css，并放在 styles 文件夹中。如果想要添加一个新的样式表或者删除一个，只要编辑 basic.css 即可。

可以在模板的 `<head>`元素中通过 `<link>`元素引入这个基本样式。然后再在页面 `<header>`中添加一个 `<img>`标签指向 logo 图片，此时在 `<article>`中添加一些临时性的填充文本。