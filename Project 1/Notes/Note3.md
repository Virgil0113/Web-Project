## Project 1 Web for a Rock Band Note 3 页面结构

站点的每个页面都要分成几个区域：

1. 头部区域包含站点的品牌信息，也是放 logo 的地方。这个区域要使用 `<header>`元素。
2. 导航区域中包含一组链接，指向各个页面。这个区域使用 `<nav>`元素。
3. 内容区域包含每一项的实质性内容，这个区域使用 `<article>`元素。

因为要使用 HTML5 元素，所以也要在文档的 `<header>`元素中包含 Modernizr 库，并将其放到 scripts 文件夹中。

模板代码为：

```
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="utf-8" />
   <title>New Rock Band</title>
   <script src="scripts/modernizr-1.6.min.js"><script>
</head>
<body>
   <header>
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
   </article>
</body>
</html>
```

