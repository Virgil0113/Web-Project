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

