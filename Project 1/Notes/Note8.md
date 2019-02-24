## Project 1 Web for a Rock Band Note 8 页面突出显示

在编写 DOM 脚本之前，必须先确定怎么组织 JavaScript 文件。为了减少请求的数量，把所有的脚本都放在一个叫 global.js 的文件里。这样有助于以后缩减代码。

首先在 scripts 文件夹中创建 [global.js](https://github.com/Virgil0113/Web-Project/blob/master/Project%201/Code/scripts/global.js)。然后在其中添加几个整个站点都会用到的函数。

先添加的是 addLoadEvent 函数,文档全部加载后如果想要运行某个函数就要用到它。
```js
function addLoadEvent(func) {
  var oldload = window.onload;
  if (typeof window.onload != 'function') {
    window.onload = func;
  }
  else {
    window.onload = function {
      oldonload();
      func();
    }
  }
}

```

还有 insertAfter 函数，它与 inserBefore 方法正好对应。

```js
function insertAfter(newElement,targetElement) {
  var parent = targetElement.parentNode;
  if (parent.lastChild == targetElement) {
    parent.appendChild(newElement);
  }
  else {
    parent.insertBefore(newElement,targetElement.nextSibling);
  }
}
```

接下来是添加 addClass 函数

```js
function addClass(element,value) {
  if (!element.className) {
    element.className = value; 
  }
  else {
    newClassName = element.className;
    newClassName += "";
    newClassName += value;
    element.className = newClassName; 
  }
}
```

要调用整个脚本，需要在模板页面 index.html 结束的 `</body>`标签之前添加一个 `<script>`标签：

 ```html
</article>
<script src="scripts/global.js"></script>
</body>
</html>
 ```

这样，站点中的每个页面都包含 global.js 文件，而其中的函数也可以在这些页面里共享了。

---

### 页面突出

当前页面的导航链接是需要突显示的，通过突出显示，访客就能知道自己“现在在这里”。

修改 color.css 文件，添加为 here 类定义的样式：

```css
header nav a.here:link,
header nav a.here:visited,
header nav a.here:hover,
header nav a.here:active {
  color: #eef;
  background-color: #799;
}
```

为了应用刚刚定义的颜色样式，为指向当前页面的导航链接添加 here 类：

`<li><a href="index.html" class="here">Home</a></li>`

但在实际的网站开发中不太可能一页一页的编辑导航链接，这时就可以使用 JavaScript 来帮忙。首先删除已经添加到导航链接中的所有 class 属性。然后编写一个 hightlightPage 函数，完成下列操作：

1. 取得导航列表中所有链接；
2. 循环遍历这些链接；
3. 如果发现了与当前 URL 匹配的链接，为它添加 here 类

将 hightlightPage 函数添加到 global.js 文件中：

```js
function hightlightPage() {
  if (document.getElementsByTagName) return false;
  if (document.getElementById) return false;
  var headers = docuemnt.getElemensByTagName('header');
  if (headers.length == 0) return false;
  var navs = header[0].getElementsByTagName('nav');
  if (navs.length == 0) return false;
  var links = navs[0].getElementsTagName("a");
  var linkurl;
  for (var i=0; i<links.length; i++) {
    linkurl = links[i].getAttribute("href");
    if (window.location.href.indexOf(linkurl) !=-1){
      links[i].className = "here";
    }
  }
}
addLoadEvent(hightlightPag);
```

这里使用到了 `window.locatio.href`来取得当前页面链接的 URL。并使用 indexOf 方法来比较字符串。因为这里我们只需要知道某个字符串是否被包含在另外一个字符串中，是否是当前 URL 里的链接 URL。运用 `currentul.indexOf(linkurl)`，如果没有匹配到，indexOf 方法将会返回-1，如果返回其他值则表示有匹配。

利用 hightlightPag 函数还可以到达一箭双雕的目的。通过给每个页面的 body 元素添加 id 属性，可以为每个页面应用不同的样式。为了取得并使用当前链接（即添加 here 类的链接）中的文本，需要使用 JavaScript 的 toLowerCase 方法把该文本转换成小写形式：

`var linktext = link[i].lastChild.nodeValue.toLowerCase();`

这样就取得了当前链接最后一个子元素的值，也就是链接的文本，然后把它转换成小写形式。通过下面的语句就可以把这个变量的值设置伪 body 元素的 id 属性了:

`document.body.setAttribute("id",linktext);`

现在的 hightlightPag 函数为：

```js
function hightlightPage() {
  if (document.getElementsByTagName) return false;
  if (document.getElementById) return false;
  var headers = docuemnt.getElemensByTagName('header');
  if (headers.length == 0) return false;
  var navs = header[0].getElementsByTagName('nav');
  if (navs.length == 0) return false;
  var links = navs[0].getElementsTagName("a");
  var linkurl;
  for (var i=0; i<links.length; i++) {
    linkurl = links[i].getAttribute("href");
    if (window.location.href.indexOf(linkurl) !=-1){
      links[i].className = "here";
      var linktext = links[i].lastChild.nodeValue.toLowerCase();
      document.body.setAttribute("id",linktext);
    }
  }
}
addLoadEvent(hightlightPag);
```

于是，index.html 文件中的 body 元素就会有一个值为 “home” 的 id，about.html 文件中的 id 就是 “about”， photos.html 文件中的 id 将是 “photos”，以此类推。

接下来就可以为每个页面制作一幅图像，然后在 layout.css 文件中添加 background-image 声明：

```css
#about header {
  background-image: url(../images/lineup.gif);
}
#photos header {
  background-image: url(../images/basshead.gif);
}
#live header {
  background-image: url(../images/bassist.gif);
}
#contact header {
  background-image: url(../images/drummer.gif);
}
```

这样一来每个页面的头部就会应用不同的背景图像了。