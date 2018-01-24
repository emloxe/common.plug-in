# 常用插件整理

## 目录
* [jQuery Lazy Load 图片延迟加载](#lazyLoad)
* [jQuery Echo 图片延迟加载](#echo)
* [jQuery 无缝向上滚动](#rolling)
* [OwlCarousel2 轮播](#OwlCarousel)
* [masonry 瀑布流插件](#masonry)





## <a id="lazyLoad" href="jquery_lazyload">jQuery Lazy Load 图片延迟加载</a>
依赖jquery，图片延迟加载

### 使用方法

载入js文件
```html
<script src="jquery.js"></script>
<script src="jquery.lazyload.js"></script>
```

修改 HTML 代码中需要延迟加载的 IMG 标签
```html
<!--
将真实图片地址写在 data-original 属性中，而 src 属性中的图片换成占位符的图片（例如 1x1 像素的灰色图片或者 loading 的 gif 图片）
添加 class="lazy" 用于区别哪些图片需要延时加载，当然你也可以换成别的关键词，修改的同时记得修改调用时的 jQuery 选择器
添加 width 和 height 属性有助于在图片未加载时占满所需要的空间
-->
<img class="lazy" src="grey.gif" data-original="example.jpg" width="640" heigh="480">
```

调用 Lazy Load
```js
$('img.lazy').lazyload();
```


### 参数配置

| 名称          | 默认值        |说明  |
|:-------------:|:-------------:|:-----|
| container     |	window      |	父容器。延迟加载父容器中的图片 |
| event     	|'scroll'       |	触发加载的事件 |
| effect        |	'show'      |	加载使用的动画效果，如 show, fadeIn, slideDown 等 jQuery 自带的效果，或者自定义动画。 |
|effectspeed    |	undefined   |	动画时间。作为 effect 的参数使用：effect(effectspeed)|
| data_attribute|	'original'  |	真实图片地址的 data 属性后缀|
| threshold 	|    0          | 	灵敏度。默认为 0 表示当图片出现在显示区域中的立即加载显示；设为整数表示图片距离 x 像素进入显示区域时进行加载；设为负数表示图片进入显示区域 x 像素时进行加载。|
| failure_limit |    0          |	容差范围。页面滚动时，Lazy Load 会遍历延迟加载的图片，检查是否在显示区域内，默认找到第 1 张不可见的图片时，就终止遍历。因为 Lazy Load 认为图片的排序是与 HTML 中的代码中的排序相同，但是也可能会出现例外，通过该值来扩大容差范围 |
| skip_invisible|	 true       |	跳过隐藏的图片。图片不可见时（如 display:none），不强制加载。|
|appear 	    |    null       |	图片加载时的事件 (Function)，有 2 个参数：elements_left（未加载的图片数量）、settings（lazyload 的参数）|
|load       	|    null       |	图片加载后的事件 (Function)，有 2 个参数，同 appear |


### 预览
[demo展示](https://emloxe.github.io/common.plugin/jquery_lazyload/demo/index.html)


**备注**
[详细信息](https://github.com/tuupola/jquery_lazyload/)









## <a id="echo" href="echo">Echo 图片延迟加载</a>

和 Lazy Load 一样，Echo.js 也是一个用于图像延迟加载 JavaScript。不同的是 Lazy Load 是基于 jQuery 的插件，而 Echo.js 不依赖于 jQuery 或其他 JavaScript 库，可独立使用。并且 Echo.js 非常小巧，压缩后不足 1KB。


### 使用方法

载入js文件
```html
<script src="echo.min.js"></script>
```

修改 HTML 代码中需要延迟加载的 IMG 标签
```html
<!--
blank.gif 是一个 1 x 1 的图片，用做默认图片，data-echo 的属性值是图片的真实地址。同样最好给图片设置宽度和高度，或者在 CSS 中设置也可以，否则似乎很底部很底部的图片才会延迟加载。
-->
<img src="images/blank.gif" alt="pic" data-echo="img/pic.jpg" width="640" height="480">
```

调用 Echo
```js
echo.init({
    offset: 100,
    throttle: 250, 
  });
```


### 参数配置

| 名称          | 默认值        | 说明  |
|:-------------:|:-------------:| :-----|
| offset        |	0           |	离可视区域多少像素的图片可以被加载 |
| throttle     	|   250         |	图片延迟多少毫秒加载 |
| debounce      |	true        |	By default the throttling function is actually a debounce function so that the checking function is only triggered after a user stops scrolling. To use traditional throttling where it will only check the images every throttle milliseconds, set debounce to false. |
| unload        |	false       |	This option will tell echo to unload loaded images once they have scrolled beyond the viewport (including the offset area).
callback |
| callback      |	传入函数    |	图片加载时的事件 (Function)，有 2 个参数：element（已更新的元素）、op（更新操作）|


### 预览
[demo展示](https://emloxe.github.io/common.plugin/echo/demo/index.html)

**备注**
[详细信息](https://github.com/toddmotto/echo)









## <a id="rolling" href="jQuery-rolling">jQuery 无缝向上滚动</a>
基于 jQuery 的简单的向上滚动效果插件


### 使用方法

载入js文件
```html
<script src="js/jquery.min.js"></script>
<script src="js/scroll.js"></script>
```

html结构
```html
<!-- 类名可以随便写 -->
<div class="myscroll">
    <ul>
        <li>用FlexSlider制作支付宝2013版幻灯片</li>
        <li>扁平化UI/Flat UI Kit(PSD)</li>
        <li>童趣卡通圣诞老人矢量素材(EPS)</li>
    </ul>
</div>
```

css中必填
```css
/* class名需要和div类名对应 */
.myscroll {
    width: 300px;
    height: 260px;
    overflow: hidden;
}
```

调用 myScroll
```js
//这里$('.myscroll')要和html中对应上
$('.myscroll').myScroll({
    speed: 40, //数值越大，速度越慢
    rowHeight: 26 //li的高度
});
```


### 参数配置

| 名称          | 默认值        | 说明  |
|:-------------:|:-------------:| :-----|
| speed         |	40          |	滚动速度，值越大速度越慢 |
| rowHeight    	|   24          |	每行的高度，单位为 px |


### 预览
[demo展示](https://emloxe.github.io/common.plugin/jQuery-rolling/demo/index.html)








## <a id="OwlCarousel" href="OwlCarousel2">OwlCarousel2 轮播</a>
强大的轮播插件，移动设备上的触摸支持，弹性布局
[官方展示](http://owlcarousel2.github.io/OwlCarousel2/demos/demos.html)
[官方配置文档](http://owlcarousel2.github.io/OwlCarousel2/docs/started-welcome.html)
支持IE7+

### 使用方法

引入css文件
```css
<link rel="stylesheet" href="owlcarousel/owl.carousel.min.css">
<link rel="stylesheet" href="owlcarousel/owl.theme.default.min.css">
```

载入js文件
```html
<script src="jquery.min.js"></script>
<script src="owlcarousel/owl.carousel.min.js"></script>
```

HTML结构
```html
<!-- 
owl-carousel 对应默认样式
owl-theme 对应主题样式
 -->
<div class="owl-carousel owl-theme">
  <div> Your Content </div>
  <div> Your Content </div>
  <div> Your Content </div>
  <div> Your Content </div>
  <div> Your Content </div>
  <div> Your Content </div>
  <div> Your Content </div>
</div>
```

调用
```js
$(".owl-carousel").owlCarousel();
```


### 参数配置

| 名称          | 默认值        |说明  |
|:-------------:|:-------------:|:-----|
| items         |	3           | 展示几个item |
| margin     	  | 0           | item右边距 |
| loop          |	false       | 自动切换时，是否不停的切换 |
| mouseDrag     |	ture        | 鼠标是否可以拖动item |
| touchDrag 	  | ture        | |
| pullDrag      | ture        | |
| freeDrag      |	false       | |
| stagePadding 	| 0           | 将显示区域左右留白，可以看到旁边的一部分内容 |
| autoWidth     | false       | 内部用元素自身的宽度，自适应 |
| startPosition | 0           | 切换起始的位置，从0开始计算 |
| nav           | false       | 是否显示左右切换按钮 |
| navText       | [next,prev] | 左右切换按钮 显示的文字 |
| navElement    | 'div'       | 左右切换按钮 display方式 |
| dots          | true        | 是否显示下部切换的小圆点 |
| autoplay      | false       | 是否自动切换 |
| autoplayTimeout| 5000       | 切换停顿时间 |
| autoplayHoverPause| false   | 鼠标移上切换是否暂停 |
| autoplaySpeed | false       | 自动切换时是速度 |
| navSpeed      | false       | 点击左右切换的按钮时的切换速度 |
| dotsSpeed     |             | 点击小圆点的切换速度|

### 预览
[demo展示](https://emloxe.github.io/common.plugin/OwlCarousel2/demo/index.html)


**备注**
[github详细信息](https://github.com/OwlCarousel2/OwlCarousel2)



## <a id="masonry" href="masonry">masonry 瀑布流插件</a>
不依赖jquery，瀑布流插件
[官方网站](https://masonry.desandro.com/)

### 使用方法


载入js文件
```html
<script src="https://unpkg.com/masonry-layout@4/dist/masonry.pkgd.min.js"></script>
```

HTML结构
```html
<div class="grid">
  <div class="grid-item"> Your Content </div>
  <div class="grid-item"> Your Content </div>
  <div class="grid-item"> Your Content </div>
</div>
```

调用jquery使用方式
```js
$('.grid').masonry({
  // options...
  itemSelector: '.grid-item'
});
```

调用js使用方式
```js
var grid = document.querySelector('.grid');
var msnry = new Masonry( grid, {
  // options...
  itemSelector: '.grid-item'
});
// 或者
var msnry = new Masonry( '.grid', {
  // options...
  itemSelector: '.grid-item'
});
```

调用html使用方式
```html
<div class="grid" data-masonry='{ "itemSelector": ".grid-item"}'>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  ...
</div>
```



### 参数配置

### 添加项目
```
// does not work
$.get( 'page2', function( content ) {
  // HTML string added, but items not added to Masonry
  $grid.append( content ).masonry( 'appended', content );
});

// does work
$.get( 'page2', function( content ) {
  // wrap content in jQuery object
  var $content = $( content );
  // add jQuery object
  $grid.append( $content ).masonry( 'appended', $content );
});
```


**备注**
[github详细信息](https://github.com/desandro/masonry)
