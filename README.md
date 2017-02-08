README.md
# 常用插件整理

## 目录
* [jQuery Lazy Load 图片延迟加载](#lazyLoad)
* [jQuery Echo 图片延迟加载](#echo)


## <a id="lazyLoad" href="jquery_lazyload">jQuery Lazy Load 图片延迟加载</a>

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
| ------------- |:-------------:|:-----|
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
[demo展示](https://emloxe.github.io/common.plug-in/jquery_lazyload/demo/index.html)


** 备注 **
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
| ------------- |:-------------:| :-----|
| offset        |	0           |	离可视区域多少像素的图片可以被加载 |
| throttle     	|   250         |	图片延迟多少毫秒加载 |
| debounce      |	true        |	By default the throttling function is actually a debounce function so that the checking function is only triggered after a user stops scrolling. To use traditional throttling where it will only check the images every throttle milliseconds, set debounce to false. |
| unload        |	false       |	This option will tell echo to unload loaded images once they have scrolled beyond the viewport (including the offset area).
callback |
| callback      |	传入函数    |	图片加载时的事件 (Function)，有 2 个参数：element（已更新的元素）、op（更新操作）|


### 预览
[demo展示](https://emloxe.github.io/common.plug-in/echo/demo/index.html)

** 备注 **
[详细信息](https://github.com/toddmotto/echo)
