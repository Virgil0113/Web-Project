## Project 1 Web for a Rock Band Note 8 页面突出显示

在编写 DOM 脚本之前，必须先确定怎么组织 JavaScript 文件。为了减少请求的数量，把所有的脚本都放在一个叫 global.js 的文件里。这样有助于以后缩减代码。

首先在 scripts 文件夹中创建 global.js。然后在其中添加几个整个站点都会用到的函数。

先添加的是 addLoadEvent 函数,文档全部加载后如果想要运行某个函数就要用到它。
```js
function addLoadEvent(func) {
  var oldload = window.onload;
  if (typeof window.onload != 'function') {
    window.onload = function() {
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

