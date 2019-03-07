## Project 1 Web for a Rock Band Note 11 JavaScript 图片库

接下来要制作的是 photos.html，这个页面的作用是使用 JavaScript 构建图片库。

在 image 文件夹里创建一个名为 photos 的文件夹，把所有的照片（大小为 400x300px）添加到里面：

- concert.jpg
- bassist.jpg
- guitarist.jpg
- crowd.jpg

同时为每张照片分别创建 100x100px 的缩略图：

- thumbnail_concert.jpg
- thumbnail_bassist.jpg
- thumbnail_guitarist.jpg
- thumbnail_crowd.jpg

创建一组链接，指向全尺寸照片。为这个列表指定 id 为 “imagegalery”。在每个链接中添加一个 `<image>`标签，各个标签的 src 属性分别指向不同的缩略图。

```html
<h1>Photos of the band</h1>
       <ul id="imagegalery">
         <li>
           <a href="images/photos/concert.jpg" title="The crowd goes wild">
             <img src="images/photos/thumbnail_concert.jpg" alt="the band in concert" />
           </a>
         </li>
         <li>
           <a href="images/photos/bassist.jpg" title="An atmospheric moment">
             <img src="images/photos/thumbnail_bassist.jpg" alt="the bassist" />
           </a>
         </li>
         <li>
           <a href="images/photos/guitarist.jpg" title="Rocking out">
             <img src="images/photos/thumbnail_guitarist.jpg" alt="the guitarist" />
           </a>
         </li>
         <li>
           <a href="images/photos/crowd.jpg" title="Encore!">
             <img src="images/photos/thumbnail_crowd.jpg" alt="the audience" />
           </a>
         </li>
       </ul>
```

更新 layout.css 文件，让缩略图从垂直排列变成水平排列：

```css
#imagegallery li {
    display:inline;
}
```

为了让图片库的脚本正常运行，还需要再制作一个占位符图片。把这个图片命名为 placeholder.gif 并放到 images 文件中。

接下来更新 scripts 文件夹中的 global.js 文件：

