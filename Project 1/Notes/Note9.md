## Project 1 Web for a Rock Band Note 9 JavaScript 幻灯片

主页还需要美化一下，在其中添加一些酷炫的功能是非常有必要的。在 "intro" 那一段[文字](Note7.md)中有指向其他页面的所有链接。如果在访客把鼠标放到相应链接上的时候，能够让他们得到有关页面的一点信息是非常不错的，可以显示相应页面头部图像的缩小版。

把每一幅图像缩小为 150 x 150px，然后并为 750px 长的一张图，命名为 slideshow.gif。把这张图片放在 images 文件夹中。

为了实现幻灯片功能，需要更新 global.js 文件。在文件中添加 moveElement 函数：

```js
function moveElement(elementID,final_x,final_y,interval) {
  if (!document.getElementById) return false;
  if (!document.getElementById(elementID)) return false;
  var elem = document.getElementById(elementID);
  if (elem.movement) {
    clearTimeout(elem.movement);
  }
  if (!elem.style.left) {
    elem.style.left = "Opx";
  }
  if (!elem.style.top) {
    elem.style.top = "Opx";
  }
  var xpos = parseInt(elem.style.left);
  var ypos = parseInt(elem.style.top);
  if (xpos == final_x && ypos == final_y) {
    return true;
  }
  if (xpos < final_x) {
    var dist = Math.ceil((fianl_x - xpos)/10);
    xpos = xpos + dist;
  }
  if (xpos > final_x) {
    var dist = Math.ceil((xpos - final_x)/10);
    xpos = xpos - dist;
  }
  if (ypos < final_y) {
    var dist = Math.ceil((final_y - ypos)/10);
    ypos = ypos + dist;
  }
  if (ypos > fianl_y) {
    var dist = Math.ceil((ypos - final_y)/10);
    ypos = ypos - dist;
  }
  elem.style.left = xpos + "px";
  elem.style.top = ypos + "px";
  var repeat = "moveElement('"+elementID+"',"+fianl_x+","+fianl_y+","+interval+")";
  elem.movement = setTimeout(repeat,interval);
}
```

现在应该创建幻灯片的元素并准备相应的链接了，把幻灯片直接放在文档中的 “intro” 段落后面。

```js
function prepareSlideshow() {
  if (!document.getElementsByTagName) return false;
  if (!document.getElementById) return false;
  if (!document.getElementById("intro")) return false;
  var intro = document.getElementById("intro");
  var slideshow = document.createElement("div");
  slideshow.setAttribute("id","slideshow");
  var frame = document.createElement("img");
  frame.setAttribute("src","images/frame.gif");
  frame.setAttribute("alt","");
  frame.setAttribute("id","frame");
  slideshow.appendChild(frame);
  var preview = document.createElement("img");
  preview.setAttribute("src","images/slideshow.gif");
  preview.setAttribute("alt","a glimpse of what awaits you");
  preview.setAttribute("id","preview");
  slideshow.appendChild(preview);
  insertAfter(slideshow,intro);
```

接着循环遍历 “intro” 段落中的所有链接，并根据当前鼠标所在的链接来移动 preview 元素。如果链接的 href 值中包含字符串 “about.html”，就把 preview 元素移动到 -150px 的位置上；如果链接的 href 值中包含字符串 “photos.html”，就把 preview 元素移动到 -300px 的位置上，以此内推。

为了让动画效果更加好看，给 moveElement 函数传入仅为5毫秒的 interval 值：

```js
 var links = document.getElementsByTagName("a");
  var destination;
  for (var i=0; i<links.length; i++) {
    links[i].onmouseover = function() {
      destination = this.getAttribute("href");
      if (destination.indexOf("index.html") !=-1) {
        moveElement("preview",0,0,5);
      }
      if (destination.indexOf("about.html") !=-1) {
        moveElement("preview",-150,0,5);
      }
      if (destination.indexOf("photos.html") !=-1) {
        moveElement("preview",-300,0,5);
      }
      if (destination.indexOf("live.html") !=-1) {
        moveElement("preview",-450,0,5);
      }
      if (destination.indexOf("contact.html") !=-1) {
        moveElement("preview",-600,0,5);
      }
    }
  }
}
```

还要通过 addLoadEvent 调用这个函数：

`addLoadEvent(prepareSlideshow);`

保存 global.js 文件。还得更新样式，在 layout.css 中添加如下声明：

```css
#slideshow {
  width: 150px;
  height: 150px;
  position: relative;
  overflow: hidden;
}
#preview {
  position: absolute;
  border-width: 0;
  outline-width: 0;
}
```

这样，把鼠标放在导航链接上，也将会触发幻灯片。

