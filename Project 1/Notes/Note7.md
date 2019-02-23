## Project 1 Web for a Rock Band Note 7 站点页面

模板都做完了，接下来要考虑站点中的每个页面了。首先从主页 index.html 开始，这个页面包含一段介绍性文字，放在 `<article>`元素中：

                            ```html
<p id="intro">Welcome to official website of New Rock Band.
Here, you can <a href="about.html" title="About">learn more about the    band</a>,view <a href="photos.html" title="Photos">photos of the band</a>,
find out about <a href="live.html" title="Tour Date">tour dates</a> 
and <a href="contact.html" title="Contact">get in touch with the band</a>.
</p>
                            ```

这样主页 [index.html](https://github.com/Virgil0113/Web-Project/blob/master/Project%201/Code/index.html) 就完成了，这段文字有以个 id 叫 “intro”，利用这个 id 为这段介绍添加特殊的样式。此外还可以利用这个 id 来添加一些 DOM 脚本。

