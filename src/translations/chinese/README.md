---
title: 前端工作面试问题
layout: layouts/page.njk
permalink: /translations/chinese/index.html
---

# 前端工作面试问题

本文包含了一些用于考查候选者的前端面试问题。不建议对单个候选者问及每个问题 (那需要好几个小时)。只要从列表里挑选一些，就能帮助你考查候选者是否具备所需要的技能。

**备注：** 这些问题中很多都是开放性的，可以引发有趣的讨论。这比直接的答案更能体现此人的能力。

## <a name='toc'>目录</a>

  1. [常见问题](#general-questions)
  1. [HTML 相关问题](#html-questions)
  1. [CSS 相关问题](#css-questions)
  1. [JS 相关问题](#js-questions)
  1. [测试相关问题](#testing-questions)
  1. [效能相关问题](#performance-questions)
  1. [网络相关问题](#network-questions)
  1. [代码相关问题](#coding-questions)
  1. [趣味问题](#fun-questions)

## 参与协作

  1. [贡献者](#contributors)
  1. [如何参与贡献](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/CONTRIBUTING.md)
  1. [许可协议](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/LICENSE.md)

#### <a name='general-questions'>常见问题：</a>

* 你在昨天/本周学到了什么？
* 编写代码的哪些方面能够使你兴奋或感兴趣？
* 你最近遇到过什么技术挑战？你是如何解决的？
* 在制作一个网页应用或网站的过程中，你是如何考虑其 UI、安全性、高性能、SEO、可维护性以及技术因素的？
* 请谈谈你喜欢的开发环境。
* 你最熟悉哪一套版本控制系统？
* 你能描述当你制作一个网页的工作流程吗？
* 假若你有 5 个不同的样式文件 (stylesheets), 整合进网站的最好方式是?
   根据class命名规则写样式，这样样式不会冲突，提取公共的样式，进行合并，非公共的单独拎出来。然后打包压缩一下就行了，若每个文件都很大，就需要分模块加载。
* 你能描述渐进增强 (progressive enhancement) 和优雅降级 (graceful degradation) 之间的不同吗?
    ```
    //优雅降级 ：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。
    .transition{
      -webkit-transition: all .5s;
        -moz-transition: all .5s;
          -o-transition: all .5s;
              transition: all .5s;  
    }
    //渐进增强 :一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。
    .transition{ 
    　　     transition: all .5s;
    　　  -o-transition: all .5s;
      　-moz-transition: all .5s;
    -webkit-transition: all .5s;
    }
    ```

* 你如何对网站的文件和资源进行优化？
  1. 利用浏览器缓存你的 js 和 CSS 文件：
  这段代码的意思是对 jpg|gif|png|css|js 发送 header 缓存头，进行一年的缓存、在浏览器不使用 ctrl+F5 强制刷新时，会一直缓存到时间时间结束，唯一遗憾的是如果你更改了js或者css文件必须把以前的路径或者文件名更改，可以这样 base.js?ver=(x) 这种方式下次浏览器就会自动读取并缓存。
   ```
　  //　在网站根目录 .htaccess 中加入以下代码
    ExpiresActive on
    ExpiresDefault “access plus 1 year”
    ```
  2. 把你的 .js 库文件地址替换成 Google CDN的地址
  3. 精简和优化你的 js 和 CSS
  4. GZIP 压缩你的 JS 和 CSS 文件
  5. 使用css sprites合并图片
  6. 优化你网站图片


* 浏览器同一时间可以从一个域名下载多少资源？
  [参考](https://www.stevesouders.com/blog/2008/03/20/roundup-on-parallel-connections/)
  浏览器	 	  HTTP / 1.1	HTTP / 1.0
  IE 6,7    	  	2           	4
  IE 8	  		    6           	6
  Firefox2        2          		8
  Firefox3      	6           	6
  Safari 3,4    	4		 	 	 	 	 	 4

* 有什么例外吗？
* 请说出三种减少页面加载时间的方法。(加载时间指感知的时间或者实际加载时间)
  1. 优化图片 
  2. 图像格式的选择（GIF：提供的颜色较少，可用在一些对颜色要求不高的地方）
  3. 优化CSS（压缩合并css，如margin-top,margin-left...)
  4. 网址后加斜杠（如www.campr.com/目录，会判断这个“目录是什么文件类型，或者是目录。） 
  5. 标明高度和宽度（如果浏览器没有找到这两个参数，它需要一边下载图片一边计算大小，如果图片很多，浏览器需要不断地调整页面。这不但影响速度，也影响浏览体验。 当浏览器知道了高度和宽度参数后，即使图片暂时无法显示，页面上也会腾出图片的空位，然后继续加载后面的内容。从而加载时间快了，浏览体验也更好了。）
  6. 减少http请求（合并文件，合并图片）
  
* 如果你参与到一个项目中，发现他们使用 Tab 来缩进代码，但是你喜欢空格，你会怎么做？
* 请写一个简单的幻灯效果页面。
* 如果今年你打算熟练掌握一项新技术，那会是什么？
* 请谈谈你对网页标准和标准制定机构重要性的理解。
  网页标准和标准制定机构都是为了能让web发展的更‘健康’，首先约束浏览器开发者遵循统一的标准，其次约束网站开发者，这样降低开发难度，开发成本，SEO也会更好做，也不会因为滥用代码导致各种BUG、安全问题，最终提高网站易用性。
* 什么是 FOUC (无样式内容闪烁)？你如何来避免 FOUC？
  如果使用import方法对CSS进行导入,会导致某些页面在Windows 下的Internet Explorer出现一些奇怪的现象:以无样式显示页面内容的瞬间闪烁,这种现象称之为文档样式短暂失效(Flash of Unstyled Content),简称为FOUC。
  原因大致为：
  1. 使用import方法导入样式表。
  2. 将样式表放在页面底部
  3. 有几个样式表，放在html结构的不同位置。
  解决方法：使用LINK标签将样式表放在文档HEAD中。

* 请解释什么是 ARIA 和屏幕阅读器 (screenreaders)，以及如何使网站实现无障碍访问 (accessible)。
  ARIA 为Web app提供满足用户不同需求的解决方案。建设起用户和软件之间的桥梁。
  新的HTML5标准中增加 aria-* 的标签属性，全称Accessible Rich Internet Application。与role标签属性配合使用。
  role属性表示一个非标准的tag的实际作用。比如用div做button，那么设置div 的 role=“button”，辅助工具就可以认出这实际上是个button。而aria-*的作用就是描述这个tag在可视化的情境中的具体信息。
  最简单的应用比如，
  < div role=”checkbox” aria-checked=”checked”>
  辅助工具就会知道，这个div实际上是个checkbox的角色，为选中状态。

* 请解释 CSS 动画和 JavaScript 动画的优缺点。
  JS动画
  缺点：
  1. JavaScript在浏览器的主线程中运行，而主线程中还有其它需要运行的JavaScript脚本、样式计算、布局、绘制任务等,对其干扰导致线程可能出现阻塞，从而造成丢帧的情况。
  2. 代码的复杂度高于CSS动画
  优点：
  1. JavaScript动画控制能力很强, 可以在动画播放过程中对动画进行控制：开始、暂停、回放、终止、取消都是可以做到的。
  2. 动画效果比css3动画丰富,有些动画效果，比如曲线运动,冲击闪烁,视差滚动效果，只有JavaScript动画才能完成
  3. CSS3有兼容性问题，而JS大多时候没有兼容性问题

  CSS动画
  缺点：
  1. 运行过程控制较弱,无法附加事件绑定回调函数。CSS动画只能暂停,不能在动画中寻找一个特定的时间点，不能在半路反转动画，不能变换时间尺度，不能在特定的位置添加回调函数或是绑定回放事件,无进度报告
  2. 代码冗长。想用 CSS 实现稍微复杂一点动画,最后CSS代码都会变得非常笨重。
  优点： 浏览器可以对动画进行优化。
  
  浏览器使用与 requestAnimationFrame 类似的机制，requestAnimationFrame比起setTimeout，setInterval设置动画的优势主要是:
    1. requestAnimationFrame 会把每一帧中的所有DOM操作集中起来，在一次重绘或回流中就完成,并且重绘或回流的时间间隔紧紧跟随浏览器的刷新频率,一般来说,这个频率为每秒60帧。
    2. 在隐藏或不可见的元素中requestAnimationFrame不会进行重绘或回流，这当然就意味着更少的的cpu，gpu和内存使用量。强制使用硬件加速 （通过 GPU 来提高动画性能）
* 什么是跨域资源共享 (CORS)？它用于解决什么问题？

#### <a name='html-questions'>HTML 相关问题：</a>

* `doctype`(文档类型) 的作用是什么？
* 浏览器标准模式 (standards mode) 、几乎标准模式（almost standards mode）和怪异模式 (quirks mode) 之间的区别是什么？
* HTML 和 XHTML 有什么区别？
* 如果页面使用 'application/xhtml+xml' 会有什么问题吗？
* 如果网页内容需要支持多语言，你会怎么做？
* 在设计和开发多语言网站时，有哪些问题你必须要考虑？
* 使用 `data-` 属性的好处是什么？
* 如果把 HTML5 看作做一个开放平台，那它的构建模块有哪些？
* 请描述 `cookies`、`sessionStorage` 和 `localStorage` 的区别。
* 请解释 `<script>`、`<script async>` 和 `<script defer>` 的区别。
* 为什么通常推荐将 CSS `<link>` 放置在 `<head></head>` 之间，而将 JS `<script>` 放置在 `</body>` 之前？你知道有哪些例外吗？
* 什么是渐进式渲染 (progressive rendering)？
* 你用过哪些不同的 HTML 模板语言？

#### <a name='css-questions'>CSS 相关问题：</a>

* CSS 中类 (classes) 和 ID 的区别。
* 请问 "resetting" 和 "normalizing" CSS 之间的区别？你会如何选择，为什么？
* 请解释浮动 (Floats) 及其工作原理。
* 描述`z-index`和叠加上下文是如何形成的。
* 请描述 BFC(Block Formatting Context) 及其如何工作。
* 列举不同的清除浮动的技巧，并指出它们各自适用的使用场景。
* 请解释 CSS sprites，以及你要如何在页面或网站中实现它。
* 你最喜欢的图片替换方法是什么，你如何选择使用。
* 你会如何解决特定浏览器的样式问题？
* 如何为有功能限制的浏览器提供网页？
  * 你会使用哪些技术和处理方法？
* 有哪些的隐藏内容的方法 (如果同时还要保证屏幕阅读器可用呢)？
* 你用过栅格系统 (grid system) 吗？如果使用过，你最喜欢哪种？
* 你用过媒体查询，或针对移动端的布局/CSS 吗？
* 你熟悉 SVG 样式的书写吗？
* 如何优化网页的打印样式？
* 在书写高效 CSS 时会有哪些问题需要考虑？
* 使用 CSS 预处理器的优缺点有哪些？
  * 请描述你曾经使用过的 CSS 预处理器的优缺点。
* 如果设计中使用了非标准的字体，你该如何去实现？
* 请解释浏览器是如何判断元素是否匹配某个 CSS 选择器？
* 请描述伪元素 (pseudo-elements) 及其用途。
* 请解释你对盒模型的理解，以及如何在 CSS 中告诉浏览器使用不同的盒模型来渲染你的布局。
* 请解释 ```* { box-sizing: border-box; }``` 的作用, 并且说明使用它有什么好处？
* 请罗列出你所知道的 display 属性的全部值
* 请解释 inline 和 inline-block 的区别？
* 请解释 relative、fixed、absolute 和 static 元素的区别
* CSS 中字母 'C' 的意思是叠层 (Cascading)。请问在确定样式的过程中优先级是如何决定的 (请举例)？如何有效使用此系统？
* 你在开发或生产环境中使用过哪些 CSS 框架？你觉得应该如何改善他们？
* 请问你有尝试过 CSS Flexbox 或者 Grid 标准规格吗？
* 为什么响应式设计 (responsive design) 和自适应设计 (adaptive design) 不同？
* 你有兼容 retina 屏幕的经历吗？如果有，在什么地方使用了何种技术？
* 请问为何要使用 `translate()` 而非 *absolute positioning*，或反之的理由？为什么？

#### <a name='js-questions'>JS 相关问题：</a>

* 请解释事件代理 (event delegation)。
* 请解释 JavaScript 中 `this` 是如何工作的。
* 请解释原型继承 (prototypal inheritance) 的原理。
* 你怎么看 AMD vs. CommonJS？
* 请解释为什么接下来这段代码不是 IIFE (立即调用的函数表达式)：`function foo(){ }();`.
  * 要做哪些改动使它变成 IIFE?
* 描述以下变量的区别：`null`，`undefined` 或 `undeclared`？
  * 该如何检测它们？
* 什么是闭包 (closure)，如何使用它，为什么要使用它？
* 请举出一个匿名函数的典型用例？
* 你是如何组织自己的代码？是使用模块模式，还是使用经典继承的方法？
* 请指出 JavaScript 宿主对象 (host objects) 和原生对象 (native objects) 的区别？
* 请指出以下代码的区别：`function Person(){}`、`var person = Person()`、`var person = new Person()`？
* `.call` 和 `.apply` 的区别是什么？
* 请解释 `Function.prototype.bind`？
* 在什么时候你会使用 `document.write()`？
* 请指出浏览器特性检测，特性推断和浏览器 UA 字符串嗅探的区别？
* 请尽可能详尽的解释 Ajax 的工作原理。
* 使用 Ajax 都有哪些优劣？
* 请解释 JSONP 的工作原理，以及它为什么不是真正的 Ajax。
* 你使用过 JavaScript 模板系统吗？
  * 如有使用过，请谈谈你都使用过哪些库？
* 请解释变量声明提升 (hoisting)。
* 请描述事件冒泡机制 (event bubbling)。
* "attribute" 和 "property" 的区别是什么？
* 为什么扩展 JavaScript 内置对象不是好的做法？
* 请指出 document load 和 document DOMContentLoaded 两个事件的区别。
* `==` 和 `===` 有什么不同？
* 请解释 JavaScript 的同源策略 (same-origin policy)。
* 如何实现下列代码：
```javascript
[1,2,3,4,5].duplicator(); // [1,2,3,4,5,1,2,3,4,5]
```
* 什么是三元表达式 (Ternary expression)？“三元 (Ternary)” 表示什么意思？
* 什么是 `"use strict";` ? 使用它的好处和坏处分别是什么？
* 请实现一个遍历至 `100` 的 for loop 循环，在能被 `3` 整除时输出 **"fizz"**，在能被 `5` 整除时输出 **"buzz"**，在能同时被 `3` 和 `5` 整除时输出 **"fizzbuzz"**。
* 为何通常会认为保留网站现有的全局作用域 (global scope) 不去改变它，是较好的选择？
* 为何你会使用 `load` 之类的事件 (event)？此事件有缺点吗？你是否知道其他替代品，以及为何使用它们？
* 请解释什么是单页应用 (single page app), 以及如何使其对搜索引擎友好 (SEO-friendly)。
* 你使用过 Promises 及其 polyfills 吗? 请写出 Promise 的基本用法（ES6）。
* 使用 Promises 而非回调 (callbacks) 优缺点是什么？
* 使用一种可以编译成 JavaScript 的语言来写 JavaScript 代码有哪些优缺点？
* 你使用哪些工具和技术来调试 JavaScript 代码？
* 你会使用怎样的语言结构来遍历对象属性 (object properties) 和数组内容？
* 请解释可变 (mutable) 和不变 (immutable) 对象的区别。
  * 请举出 JavaScript 中一个不变性对象 (immutable object) 的例子？
  * 不变性 (immutability) 有哪些优缺点？
  * 如何用你自己的代码来实现不变性 (immutability)？
* 请解释同步 (synchronous) 和异步 (asynchronous) 函数的区别。
* 什么是事件循环 (event loop)？
  * 请问调用栈 (call stack) 和任务队列 (task queue) 的区别是什么？
* 解释 `function foo() {}` 与 `var foo = function() {}` 用法的区别

#### <a name='testing-questions'>测试相关问题：</a>

* 对代码进行测试的有什么优缺点？
* 你会用什么工具测试你的代码功能？
* 单元测试与功能/集成测试的区别是什么？
* 代码风格 linting 工具的作用是什么？

#### <a name='performance-questions'>效能相关问题：</a>

* 你会用什么工具来查找代码中的性能问题？
* 你会用什么方式来增强网站的页面滚动效能？
* 请解释 layout、painting 和 compositing 的区别。

#### <a name='network-questions'>网络相关问题：</a>

* 为什么传统上利用多个域名来提供网站资源会更有效？
* 请尽可能完整得描述从输入 URL 到整个网页加载完毕及显示在屏幕上的整个流程。
* Long-Polling、Websockets 和 Server-Sent Event 之间有什么区别？
* 请描述以下 request 和 response headers：
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
* 什么是 HTTP method？请罗列出你所知道的所有 HTTP method，并给出解释。
* 请解释 HTTP status 301 与 302 的区别？

#### <a name='coding-questions'>代码相关的问题：</a>

*问题：`foo`的值是什么？*
```javascript
var foo = 10 + '20';
```

*问题：如何实现以下函数？*
```javascript
add(2, 5); // 7
add(2)(5); // 7
```

*问题：下面的语句的返回值是什么？*
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```

*问题：`window.foo`的值是什么？*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*问题：下面两个 alert 的结果是什么？*
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

*问题：`foo.length`的值是什么？*
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

*问题：`foo.x`的值是什么？*
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```

*问题：下面代码的输出是什么？*
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
console.log('three');
```

#### <a name='fun-questions'>趣味问题：</a>

* 你最近写过什么的很酷的项目吗？
* 在你使用的开发工具中，最喜欢哪些方面？
* 谁使你踏足了前端开发领域？
* 你有什么业余项目吗？是哪种类型的？
* 你最爱的 IE 特性是什么？
* 你对咖啡有没有什么喜好？


#### <a name='contributors'>贡献者：</a>

本文档始于 2009 年，是以下作者的合作成果：[@paul_irish](https://twitter.com/paul_irish) [@bentruyman](https://twitter.com/bentruyman) [@cowboy](https://twitter.com/cowboy) [@ajpiano](https://twitter.com/ajpiano) [@SlexAxton](https://twitter.com/slexaxton) [@boazsender](https://twitter.com/boazsender) [@miketaylr](https://twitter.com/miketaylr) [@vladikoff](https://twitter.com/vladikoff) [@gf3](https://twitter.com/gf3) [@jon_neal](https://twitter.com/jon_neal) [@sambreed](https://twitter.com/sambreed) 和 [@iansym](https://twitter.com/iansym)。

时至今日，文档已经融入超过 [100 位开发者](https://github.com/h5bp/Front-end-Developer-Interview-Questions/graphs/contributors)的贡献。
