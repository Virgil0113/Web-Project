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

                                            ```html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="utf-8" />
   <title>New Rock Band</title>
   <script src="scripts/modernizr-1.6.min.js"><script>
   <link rel="stylesheet" media="screen" href="styles/basic.css">
</head>
<body>
   <header>
        <img src="images/logo.gif" alt="New Rock Band" />
       <nav>
	  <ul>
	     <li><a href="index.html">Home</a></li>
	     <li><a href="about.html">About</a></li>
	     <li><a href="photos.html">Photos</a></li>
	     <li><a href="live.html">Live</a></li>
	     <li><a href="contact.html">Contact</a></li>
          </ul>
       </nav>
   </header>
   <article>
       <h1>New Rock Band</h1>
       <p>An introduction to New Rock Band Mike and Brad have known each other since 7th grade, they both went to Agoura high school, Brad was Phoenix's room mate in college, and Brad and Rob met when they both joined a band together. Mike met Joe at Art College. The origins of New Rock Band date right back to around 1994, To a band called 'Relative Degree', This band featured Brad and Rob, they played a few live shows, recorded some demo's and then fell apart. 
   </article>
</body>
</html>
                                            ```

如此一来基本的网页模型就完成了。

---

### 颜色

样式表 color.css 是最直观的，为了避免某些看不到文本的意外，不管哪个元素应用什么颜色，都要给它一个背景颜色。

编写完后的代码为——[code](https://github.com/Virgil0113/Web-Project/blob/master/Project%201/Code/styles/color.css)

---

