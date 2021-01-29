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
  CORS是一个W3C标准，全称是"跨域资源共享"（Cross-origin resource sharing）。
  它允许浏览器向跨源服务器，发出XMLHttpRequest请求，从而克服了AJAX只能同源使用的限制。
  [参考](https://www.ruanyifeng.com/blog/2016/04/cors.html)
#### <a name='html-questions'>HTML 相关问题：</a>

* `doctype`(文档类型) 的作用是什么？
  DOCTYPE 全拼document type 是一种标准通用标记语言的文档类型声明,它的目的是告诉浏览器（解析器）应该以什么样（html或xhtml）的文档类型定义（DTD）来解析文档。

* 浏览器标准模式 (standards mode) 、几乎标准模式（almost standards mode）和怪异模式 (quirks mode) 之间的区别是什么？
  标准模式（Strick mode）：浏览器使用W3C的标准解析渲染页面。在标准模式中，浏览器以其支持的最高标准呈现页面。
  怪异模式(混杂模式)(Quick mode 或Standards mode)：浏览器使用自己的怪异模式解析渲染页面。在怪异模式中，页面以一种比较宽松的向后兼容的方式显示。
  几乎标准模式（almost：是为了解决table中内联图片而设计的。

* HTML 和 XHTML 有什么区别？
  HTML与XHTML之间的差别，主要分为功能上的差别和书写习惯的差别两方面。
  关于功能上的差别，主要是XHTML可兼容各大浏览器、手机以及PDA，并且浏览器也能快速正确地编译网页。 
  由于XHTML的语法较为严谨，所以如果你是习惯松散结构的HTML编写者，那需要注意XHTML的规则。
  下面列出了几条容易犯的错误，供理解。  
  所有标签都必须小写
  在XHTML中，所有的标签都必须小写，不能大小写穿插其中，也不能全部都是大写。
  标签必须成双成对
  像是<p>...</p>、<a>...</a>、<div>...</div>标签等，当出现一个标签时，必须要有对应的结束标签，缺一不可，就像在任何程序语言中的括号一样
  标签顺序必须正确
  标签由外到内，一层层包覆着，所以假设你先写div后写h1，结尾就要先写h1后写div。只要记住一个原则“先进后出”，先弹出的标签要后结尾。
  所有属性都必须使用双引号
  在XHTML 1.0中规定连单引号也不能使用，所以全程都得用双引号。
  不允许使用target="_blank"
  从XHTML 1.1开始全面禁止target属性，如果想要有开新窗口的功能，就必须改写为rel="external"，并搭配JavaScript实现此效果。

* 如果页面使用 'application/xhtml+xml' 会有什么问题吗？
  兼容性问题，一些老的浏览器不支持

* 如果网页内容需要支持多语言，你会怎么做？
* 在设计和开发多语言网站时，有哪些问题你必须要考虑？
* 使用 `data-` 属性的好处是什么？
  data-xxx为前端开发者提供了自定义属性
  自定义属性可以通过对象的dataset来获取，不支持该属性的浏览器可以通过getAttribute()方法来获取

* 如果把 HTML5 看作做一个开放平台，那它的构建模块有哪些？
  div section nav footer header ...

* 请描述 `cookies`、`sessionStorage` 和 `localStorage` 的区别。
  1. 数据存储大小限制不同。
    - cookies：数据始终在同源的http请求中携带，即cookie在服务器和浏览器间回传。故存储的数据大小最小，一般为4k。
    - sessionStorage：数据在本地保存，不会自动把数据发给服务器。所以一般5M或者更大。
    - localStorage：数据在本地保存，不会自动把数据发给服务器。所以一般5M或者更大。
  2. 数据有效期不同
    - cookies：数据在cookie设置的有效期之前都有效，即使窗口和浏览器关闭。
    - sessionStorage：数据在关闭浏览器窗口后自动清除。存储的数据仅在同源同窗口内有效，即使在不同浏览器相同页面也是无效的。一般用于存储会话数据。
    - localStorage：始终有效，因此用作持久数据。
  3. 数据作用域不同
    - cookies：在所有同源窗口敏感词享。
    - sessionStorage：不在不同浏览器窗口敏感词享。
    - localStorage：在所有同源窗口敏感词享。

* 请解释 `<script>`、`<script async>` 和 `<script defer>` 的区别。
  1. 作用：
      - 没有 defer 或 async，浏览器会立即加载并执行指定的脚本，也就是说不等待后续载入的文档元素，读到就加载并执行。
      - async 属性表示异步执行引入的 JavaScript，与 defer 的区别在于，如果已经加载好，就会开始执行——无论此刻是 HTML 解析阶段还是 DOMContentLoaded 触发之后。需要注意的是，这种方式加载的 JavaScript 依然会阻塞 load 事件。换句话说，async-script 可能在 DOMContentLoaded 触发之前或之后执行，但一定在 load 触发之前执行。
      - defer 属性表示延迟执行引入的 JavaScript，即这段 JavaScript 加载时 HTML 并未停止解析，这两个过程是并行的。整个 document 解析完毕且 defer-script 也加载完成之后（这两件事情的顺序无关），会执行所有由 defer-script 加载的 JavaScript 代码，然后触发 DOMContentLoaded 事件。
  2. 区别
      - defer 与相比普通 script，有两点区别：载入 JavaScript 文件时不阻塞 HTML 的解析，执行阶段被放到 HTML 标签解析完成之后。
      在加载多个JS脚本的时候，async是无顺序的加载，而defer是有顺序的加载。

* 为什么通常推荐将 CSS `<link>` 放置在 `<head></head>` 之间，而将 JS `<script>` 放置在 `</body>` 之前？你知道有哪些例外吗？
* 什么是渐进式渲染 (progressive rendering)？
* 你用过哪些不同的 HTML 模板语言？

#### <a name='css-questions'>CSS 相关问题：</a>
* CSS 中类 (classes) 和 ID 的区别。
  ID是一个标签，用于区分不同的结构和内容，就象名字，如果一个屋子有2个人同名，就会出现混淆；class是一个样式，可以套在任何结构和内容上，就象一件衣服；

* 请问 "resetting" 和 "normalizing" CSS 之间的区别？你会如何选择，为什么？
  reset.css功能是将网页标签重置。Normalize.css 只作用于需要规范化的样式,在默认的HTML元素样式上提供了跨浏览器的高度一致性.相比传统reset更优质。
  特点：
  1. 保护有用的浏览器默认样式而不是完全去掉它们
  2. 一般化的样式：为大部分HTML元素提供
  3. 修复浏览器自身的bug并保证各浏览器的一致性
  4. 优化CSS可用性：用一些小技巧
  5. 解释代码：用注释和详细的文档来

* 请解释浮动 (Floats) 及其工作原理。
  float 属性定义元素在哪个方向浮动。以往这个属性总应用于图像，使文本围绕在图像周围，不过在 CSS 中，任何元素都可以浮动。浮动元素会生成一个块级框，而不论它本身是何种元素。
  假如在一行之上只有极少的空间可供浮动元素，那么这个元素会跳至下一行，这个过程会持续到某一行拥有足够的空间为止。
  有以下几个属性：
  left 元素向左浮动。
  right 元素向右浮动。
  none 默认值。元素不浮动，并会显示在其在文本中出现的位置。
  inherit 规定应该从父元素继承 float 属性的值。
  任何的版本的 Internet Explorer （包括 IE8）都不支持属性值 “inherit”。

* 描述`z-index`和叠加上下文是如何形成的。
  z-index 属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于前面。
  元素可拥有负的 z-index 属性值。
  z-index 仅能在定位元素上奏效（例如 position:absolute;）
  形象的说，该属性设置一个定位元素沿 z 轴的位置，z 轴定义为垂直延伸到显示区的轴。如果为正数，则离用户更近，为负数则表示离用户更远。
  层叠顺序总结：小于0的z-index < 块 < 浮动 < 行内块 < 行内 < 定位 < 大于0的z-index
  可见，在无特殊情况下定位元素总是比普通元素层级高，并且后一个元素比前一个元素层级高，这就是因为层叠上下文。
  除了定位元素可以创建层叠上下文以外，还有如下几个属性也可以做到。
  以下来自MDN
  根元素 (HTML),  z-index 值不为 “auto”的 绝对/相对定位，
  一个 z-index 值不为 “auto”的 flex 项目 (flex item)，即：父元素 display:flex|inline-flex，
  opacity 属性值小于 1 的元素
  transform 属性值不为 “none”的元素，
  mix-blend-mode 属性值不为 “normal”的元素，
  filter值不为“none”的元素，
  perspective值不为“none”的元素，
  isolation 属性被设置为 “isolate”的元素，
  position: fixed
  在 will-change 中指定了任意 CSS 属性，即便你没有直接指定这些属性的值
  -webkit-overflow-scrolling 属性被设置 “touch”的元素

* 请描述 BFC(Block Formatting Context) 及其如何工作。
  BFC也就是块级格式化上下文，是用于布局块级盒子的一块渲染区域。
  布局规则：
    1.在BFC环境内部的所有元素按照垂直方向上一个接一个的放置；
    2.相邻盒子（BOX）在垂直方向的margin值会重叠；
    3.内部盒子会以BFC的左边（右边）线接触，浮动也是这样的；
    4.BCF区域不会与浮动盒子重叠；
    5.BFC环境中的子元素以外界分离，不会影响到外面的元素，而外面的元素也不会影响到BFC里面的元素。
    6.BFC中浮动元素会参与计算。
  BFC的触发方式：
    1. 根元素；
    2. float为除none以外的值；
    3. overflow为除了visiable以外的值，包括hidden、scroll和auto；
    4. position值为absolute或fixed；
    5. display值为inline-block；
    6. display值以table-开头的表格单元格元素和值为table-caption的元素；
    7. display值为flow-root的元素；
    8. 此外还有flex元素、grid元素等等

* IFC环境（in-line formatting context行级格式化上下文）
  布局规则：
  1. IFC中的元素会在一行从左到右依次排列；
  2. 在一行上的所有元素会在该区域形成一个行框；
  3. 行框的宽度为包含框的宽度，高度为行框中最高元素的高度；
  4. 浮动的元素不会在行框中，并且浮动元素会压缩行框的宽度；
  5. 行框的宽度容纳不下子元素时，子元素会换到下一行，并且产生新的行框；
  6. 行框内的元素遵循   text-align   和    vartical-align;

* 列举不同的清除浮动的技巧，并指出它们各自适用的使用场景。
  1. 使用clear样式。
     给需要清除浮动的元素添加样式：
     ```
     .div_float{
       clear: left; 
     }
     ```
  2. 在父元素结束标签之前插入清除浮动的块级元素
     ```
     <div>
       <div class="div_float"></div>
       <div class="div_clear"></div>
     </div>

     //style
     .div_clear{
       clear:both
     }
     ```
  3. 利用伪元素
     HTML结构如下，给父Div元素添加一个类名clearfix
    ```
     <div class="clearfix">
       <div class="div_float"></div>
     </div>

    //style
    .clearfix:after{
        content:'.';
        height: 0;
        clear: both;
        display: block;
      }
    ```
  4. 使用overflow清除浮动

* 请解释 CSS sprites，以及你要如何在页面或网站中实现它。
  CSS Sprites其实就是把网页中一些背景图片整合到一张图片文件中，再利用CSS的“background-image”，“background- repeat”，“background-position”的组合进行背景定位，background-position可以用数字能精确的定位出背景图片的位置。
  减少图片请求，优化页面加载速度。

* 你最喜欢的图片替换方法是什么，你如何选择使用。
  图像替代，就是像我们在平时将文本添加到文本中，然后通过css隐藏文本并在它的位置上显示一个背景图片，这样，搜索引擎仍然可以搜到HTML文本，即使我们禁用css后，文本仍然是可以显示的。
  1. FIR(Fahrner Image Replacement)方法
    当图片无法显示时，将导致这个区域没有任何内容。同时，使用 display:none 的方式隐藏的内容，将被许多主流屏幕阅读器忽略，从而造成可用性问题，因此，应该尽量避免使用
    ```
        <h1 id="FIR">
        　　<a href="#">FIR Measure</a>
        </div>

        #FIR{　　width:300px;　　height:200px;　　background-img:url("fir.png");}
        #FIR a{　　display:none;}
    ```
  2. Phark方法
    text-indent属性，并且给其设置一个较大的负值，达到隐藏文本的效果。这种方法简单易懂而且支持阅读器之类浏览网页。当图片无法显示时，依然存在 FIR 的问题。
    ```
    <h1 id="mir">MIR Measure</h1>
    #mir{
        width:300px;
        height:200px;
        background-img:url("mir.png");
        text-indent:-5000px;
    }
    ```
  3. 通过把span的大小都设置为“0”，来达到隐藏文本效果，这样阅读器就能完全阅读到，而且又达到了图片替换文本的效果。
      ```
        <h1 id="thirdMeasure">
          <span>the third measure</span>
      </h1>

      #thirdMeasure{
          width:300px;
          height:200px;
          background-img:url("3rd.png");
      }
      #thirdMeasure span{
          display:block;
          width:0;
          height:0;
          font-size:0;
          overflow:hidden;
      }
      ```
    4. 将 h1 的 position 设为 relative ，这样将使 h1 里面的元素定位以h1 为参照，然后将span 元素绝对定位，撑满整个 h1 区域，同时将背景图应用在 span 标签里面；这种方法的原理是将 span 标签覆盖在文字内容上面，一旦 span 里面的背景图无法显示，将显示下层的文字内容，不影响正常使用。但是，此方法也有一个缺陷，就是背景图不能透明，否则将透出下面的文字。
      ```
      <h1 id="4thMeasure">
          <span></span>the fourth Measure
      </h1>

      #4thMeasure{
          width:300px;
          height:200px;
          position:relative;
      }
      span{
          position:absolute;
          width:100%;
          height:100%;
          background-img:url(4th.png);
      }
      ```
* 有哪些的隐藏内容的方法(如果同时还要保证屏幕阅读器可用呢？)
  1. 对文本的隐藏
    ```
      //第一种
      .texthidden{ 
      　　　text-indent:-9999px; 
      　　　white-space:nowrap; 
      　　　line-height:0; 
      } 
      //第二种
      .texthidden{
          display:block
          width:0;
          height:0;
          overflow:hidden;  
      }
      //第三种
      .texthidden{
        display:none      //使包括容器本身在内的东西都消失，简便且有效，但它有两个耳熟能详的缺陷，那就是对搜索引擎不友好，且被屏幕阅读器所忽略。
      }
    ```
    2. 隐藏超链接（另类黑链）
    3. 对统计代码隐藏
    4. 隐藏超出图片
    　　overflow:hidden
    5. css隐藏滚动条
    　　overflow-x:hidden;overflow-y:hidden;
    6. css隐藏div层
    　　display:none;或者visibility:hidden;

* 在书写高效 CSS 时会有哪些问题需要考虑？
  1. 尽量将样式写在单独的css文件里面，在head元素中引用（好处：内容和样式分离，易于管理和维护；减少页面体积；css文件可以被缓存、重用，维护成本降低. 
  2. 不使用@import，@import影响css文件的加载速度
  3. 避免使用复杂的选择器，层级越少越好；有时候项目的模块越来越多，功能越来越复杂，我们写的CSS选择器会内套多层，越来越复杂。建议选择器的嵌套最好不要超过三层。
  4. 利用CSS继承减少代码量
  　　一部分CSS代码是可以继承的，如果父元素已经设置了该样式，子元素就不需要去设置该样式，这个也是提高性能的行之有效的方法。常见的可以继承的属性比如：color，font-size，font-family等等；不可继承的比如：position，display，float等。
  5. 利用CSS Sprint，即雪碧图，将多个图片合并成一张图片，利用background-position来显示和定位图片。
  6. 避免使用多类选择符，IE6以及更古老的浏览器对类似.foo.bar的多类选择符解析不正确
  7. 移除空的CSS规则
  8. 正确使用display属性，由于display的作用，某些样式组合会无效，徒增样式体积的同时也影响解析性能。
  9. 不滥用浮动，虽然浮动不可避免，但不可否认很多css bug是由于浮动而引起
  10. 不滥用web字体，web fonts通常体积庞大，而且一些浏览器在下载web fonts时会阻塞页面渲染损伤性能。 
  11. 不在选择符中使用ID选择符，主要考虑到样式重用性以及与页面的耦合性

* 你会如何解决特定浏览器的样式问题？
  1. CSS Hack 形式
     CSS Hack大致有3种表现形式：CSS属性Hack、CSS选择符Hack以及IE条件注释Hack， Hack主要针对IE浏览器。
     - 属性级Hack：比如IE6能识别下划线"_"和星号" * "，IE7能识别星号" * "，但不能识别下划线"_"，而firefox两个都不能认识。等等
     - 选择符级Hack：比如IE6能识别*html .class{}，IE7能识别*+html .class{}或者*:first-child+html .class{}。等等
     - IE条件注释Hack：比如针对所有IE：<!--[if IE]><!--您的代码--><![endif]-->，针对IE6及以下版本：<!--[if lt IE 7]><!--您的代码--><![endif]-->，这类Hack不仅对CSS生效，对写在判断语句里面的所有代码都会生效。
     - 注意书写顺序：一般是将识别能力强的浏览器的CSS写在后面。通常先写FF等非IE浏览器所需样式，其次写IE8所需样式，接着是IE7的，再接着才是IE6的。
    ```
      /* CSS属性级Hack */
      color:red;    /* 所有浏览器可识别*/
      _color:red;     /*  仅IE6 识别 */
      *color:red;    /*  IE6、IE7 识别 */
      +color:red;    /*  IE6、IE7 识别 */
      *+color:red;    /*  IE6、IE7 识别 */
      [color:red;    /*  IE6、IE7 识别 */
      color:red\9;    /* IE6、IE7、IE8、IE9 识别 */
      color:red\0;    /* IE8、IE9 识别*/
      color:red\9\0;    /* 仅IE9识别 */
      color:red \0;    /* 仅IE9识别 */
      color:red!important; /* IE6 不识别!important 详情参见*/
      -------------------------------------------------------------
      /* CSS选择符级Hack */
      *html #demo { color:red;}   /*  仅IE6 识别 */
      *+html #demo { color:red;}  /*  仅IE7 识别 */
      body:nth-of-type(1) #demo { color:red;} /* IE9+、FF3.5+、Chrome、Safari、Opera 可以识别 */
      head:first-child+body #demo { color:red; } /* IE7+、FF、Chrome、Safari、Opera 可以识别 */
      :root #demo { color:red\9; } : /* 仅IE9识别 */
      --------------------------------------------------------------
      /* IE条件注释Hack　详情参见 */
      <!--[if IE]>此处内容只有IE可见<![endif]--> 
      <!--[if IE 6]>此处内容只有IE6.0可见<![endif]--> 
      <!--[if IE 7]>此处内容只有IE7.0可见<![endif]--> 
      <!--[if gte IE 6]> IE6以及IE6以上版本可识别 <![endif]-->
      <!--[if lt IE 7]> IE7以及IE7以下版本可识别 <![endif]-->
      <!--[if gte IE 7]> IE7以及IE7以上版本可识别 <![endif]-->
      <!--[if !IE]>此处内容只有非IE可见<![endif]--> 
    ```


* 如何为有功能限制的浏览器提供网页？
* 你会使用哪些技术和处理方法？
  优雅降级：Web站点在所有新式浏览器中都能正常工作，如果用户使用的是老式浏览器，则代码会检查以确认它们是否能正常工作。由于IE独特的盒模型布局问题，针对不同版本的IE的hack实践过优雅降级了,为那些无法支持功能的浏览器增加候选方案，使之在旧式浏览器上以某种形式降级体验却不至于完全失效。
  渐进增强：从被所有浏览器支持的基本功能开始，逐步地添加那些只有新式浏览器才支持的功能,向页面增加无害于基础浏览器的额外样式和功能的。当浏览器支持时，它们会自动地呈现出来并发挥作用。

* 你用过栅格系统 (grid system) 吗？如果使用过，你最喜欢哪种？
  element iview vant 

* 你用过媒体查询，或针对移动端的布局/CSS 吗？
* 你熟悉 SVG 样式的书写吗？
* 如何优化网页的打印样式？
* 在书写高效 CSS 时会有哪些问题需要考虑？
  1. 样式是：浏览器是从右向左来解析一个选择器的
  2. ID最快，Universal最慢 有四种类型的key selector，解析速度由快到慢依次是：ID、class、tag和universal
  3. 不要tag-qualify （永远不要这样做 ul#main-navigation { } ID已经是唯一的，不需要Tag来标识，这样做会让选择器变慢。）
  4. 后代选择器最糟糕（换句话说，下面这个选择器是很低效的： html body ul li a { }）
  5. CSS3的效率问题（CSS3选择器（比如 :nth-child）能够漂亮的定位我们想要的元素，又能保证我们的CSS整洁易读。但是这些神奇的选择器会浪费很多的浏览器资源。）
  6. 我们知道#ID速度是最快的，那么我们都用ID，是不是很快。但是我们不应该为了效率而牺牲可读性和可维护性

* 使用 CSS 预处理器的优缺点有哪些？
  优点：
    - 开发速度提升；
    - 代码优化效率提高（对开发者而言）；
    - 代码更通俗易懂（对开发者而言）；
    - 维护简单便捷；
    - 代码更干净，优美；
    - 功能更多更强，CSS做出JS的特效（其实就是JS）；
  缺点：
    - 舍弃用户体验来提高开发的效率，可以查考Bootstrap的缺点；
    - 舍弃网页打开速度换取开发效率提升；（Vue，react等前端开发框架打包之后降低了这一缺点）
    - 需要一个学习的过程，用之不当反而弄巧反拙；  

* 如果设计中使用了非标准的字体，你该如何去实现？
  1. 使用@font-face
    ```
    @font-face{
        font-family:"自己的字体名字，可以随便起，可以不和字体文件名相同";
        src:url("下载的字体路径");
    }
    ```
    这个是css3的属性，不过css2.1就已经出现了，css3加入了标准
  2. 引入字体文件
    ```
        <link rel='stylesheet' type='text/css' href='http://fonts.googleapis.com/css?family=Condiment'>
        @import url(http://fonts.googleapis.com/css?family=Condiment);
        avaScript 方式：
    ```
  3. 考虑优雅退化问题，使用系统自带字体。


* 请解释浏览器是如何判断元素是否匹配某个 CSS 选择器？
  先产生一个元素集合，然后从后往前判断；

* 请描述伪元素 (pseudo-elements) 及其用途。
  `:first-letter :first-line :after :before`
  1. 利用伪元素装饰内容 (无论是装饰图片还是音效) 而不需要更改 HTML 的内容，从而帮助内容与样式更好地分离
  2. HTML 标签的目的，就是为了展示内容信息。非内容信息要使用伪元素。具体的使用场景是图标和清除浮动。
  伪类:伪类选择元素基于的是当前元素处于的状态，或者说元素当前所具有的特性，而不是元素的id、class、属性等静态的标志。由于状态是动态变化的，所以一个元素达到一个特定状态时，它可能得到一个伪类的样式；当状态改变时，它又会失去这个样式。由此可以看出，它的功能和class有些类似，但它是基于文档之外的抽象，所以叫伪类。
  伪元素:与伪类针对特殊状态的元素不同的是，伪元素是对元素中的特定内容进行操作，它所操作的层次比伪类更深了一层，也因此它的动态性比伪类要低得多。实际上，设计伪元素的目的就是去选取诸如元素内容第一个字（母）、第一行，选取某些内容前面或后面这种普通的选择器无法完成的工作。它控制的内容实际上和元素是相同的，但是它本身只是基于元素的抽象，并不存在于文档中，所以叫伪元素。

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
