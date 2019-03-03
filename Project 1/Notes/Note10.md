## Project 1 Web for a Rock Band Note 10 内部导航

站点的下一页是 About 页面。 在 about.html 的 `<article>`元素中添加如下标记：

```html
<h1>About the Band</h1>
       <nav>
          <ul>
            <li><a href="#jay">Jay Skript</a></li>
            <li><a href="#domsters">The Domsters</a></li>
          </ul>
       </nav>
       <section id="jay">
          <h2>Jay Skript</h2>
            <p>Jay Skirpt is going to rock your world!</p>
            <p>Together with his compatriots the Domsters,
           Jay is set for world domination. Just you wait and see</p> 
       </section>
       <section id="domsters">
          <h2>The Domsters</h2>
            <p>The Domsters have been around, in one form or another,
            for almost as long. It's only in the past few years that the Domsters
            have settled down to their current, stable lineup.
            </p> 
       </section>
```

在 `<nav>`元素中包含内部链接是为了解决页面过长的问题。单击 `<nav>`中的每个链接，都会跳到带有相应 id 属性的 `<section>`。

使用 JavaScript 和 DOM 可以选择性地每次只显示其中一个部分（section）。把下面这个函数添加到 global.js 中，它能够根据指定的 id 显示相应的 `<section>`，同时隐藏其他部分：

```js
function showSection(id) {
  var sections = document.getElemensByTagName("section");
  for (var i=0; i<sections.length; i++) {
    if (sections[i].getAttribute("id") != id) {
      sections[i].style.display = "none";
    } else {
      sections[i].style.display = "block";
    }
  }
}
```

这个 showSection 函数的用途是修改每个部分的 display 样式属性。除了与作为参数传入的 id 对应的部分，其他部分的 display 属性都将被设置为”none“，而与传入 id 对应的哪个部分的 display 属性则被设置伪"block"。

然后还需要在 `<article>`中的 `<nav>`所包含的链接被单击时调用 showSection 函数。创建一个名为 prepareInternalnav 的函数：

```js
function prepareInternalnav() {
  if (!document.getElemensByTagName) return false;
  if (!document.getElementById) return false;
  var articles = document.getElementsByTagName("article");
  if (article.length == 0) return false;
  var navs = articles[0].getElementsByTagName("nav");
  if (navs.length == 0) return false;
  var nav = navs[0];
  var links = nav.getElementsByTagName("a");
  for (var i=0; i<links.length; i++) {
    var sectionId = links[i].getAttribute("href").split("#")[1];
    if (!document.getElementById(sectionId)) continue;
    document.getElementById(sectionId).style.display = "none";
    links[i].destination = sectionId;
    links[i].onclick = function() {
      showSection(this.destination);
      return false;
    }
  }
}
```



  这样就完成了隐藏页面的功能，页面越长这个功能的效果越明显。