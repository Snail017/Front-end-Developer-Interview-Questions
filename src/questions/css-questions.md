---
title: CSS Questions
layout: layouts/page.njk
permalink: /questions/css-questions/index.html
---

# What is CSS selector specificity and how does it work?
  浏览器将HTML和CSS转换为DOM(文档对象模型)。DOM表示计算机内存中的文档。它结合了文档的内容和样式。浏览器显示DOM的内容。

# What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
  reset.css功能是将网页标签重置。Normalize.css 只作用于需要规范化的样式,在默认的HTML元素样式上提供了跨浏览器的高度一致性.相比传统reset更优质。
  特点：
  1. 保护有用的浏览器默认样式而不是完全去掉它们
  2. 一般化的样式：为大部分HTML元素提供
  3. 修复浏览器自身的bug并保证各浏览器的一致性
  4. 优化CSS可用性：用一些小技巧
  5. 解释代码：用注释和详细的文档来

# Describe Floats and how they work.
  float 属性定义元素在哪个方向浮动。以往这个属性总应用于图像，使文本围绕在图像周围，不过在 CSS 中，任何元素都可以浮动。浮动元素会生成一个块级框，而不论它本身是何种元素。
  假如在一行之上只有极少的空间可供浮动元素，那么这个元素会跳至下一行，这个过程会持续到某一行拥有足够的空间为止。
  有以下几个属性：
  left 元素向左浮动。
  right 元素向右浮动。
  none 默认值。元素不浮动，并会显示在其在文本中出现的位置。
  inherit 规定应该从父元素继承 float 属性的值。
  任何的版本的 Internet Explorer （包括 IE8）都不支持属性值 “inherit”。
  
# Describe z-index and how stacking context is formed.
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


# Describe BFC (Block Formatting Context) and how it works.
  BFC也就是块级格式化上下文，是用于布局块级盒子的一块渲染区域。
  布局规则：
    1.在BFC环境内部的所有元素按照垂直方向上一个接一个的放置；
    2.相邻盒子（BOX）在垂直方向的margin值会重叠；
    3.内部盒子会以BFC的左边（右边）线接触，浮动也是这样的；
    4.BCF区域不会与浮动盒子重叠；
    5.BFC环境中的子元素以外界分离，不会影响到外面的元素，而外面的元素也不会影响到BFC里面的元素。
    6.BFC中浮动元素会参与计算。
  BFC的触发方式：
    一下的值都会触发BFC：
    float：的值不为none，都会触发BFC。
    position:absolulute,fixed
    display:in-line-block,table-cell,table-caption,flex,in-line-fiex.
    overflow:不为visible.

# IFC环境（in-line formatting context行级格式化上下文）
  布局规则：
      1.IFC中的元素会在一行从左到右依次排列；
      2.在一行上的所有元素会在该区域形成一个行框；
      3.行框的宽度为包含框的宽度，高度为行框中最高元素的高度；
      4.浮动的元素不会在行框中，并且浮动元素会压缩行框的宽度；
      5.行框的宽度容纳不下子元素时，子元素会换到下一行，并且产生新的行框；
      6.行框内的元素遵循   text-align   和    vartical-align;9

# What are the various clearing techniques and which is appropriate for what context?
# How would you approach fixing browser-specific styling issues?（如何解决特定于浏览器的样式问题）
1. 在同一个CSS样式表中，使用 !important 来定义不同的值以适应Firefox和IE。
eg:
```
//(注意这里IE6是无法识别 !important 这个标记的,但它会识别padding: 20px,所以要在后面加上padding: 10px用来覆盖padding: 20px)
padding: 20px !important; /*For Firefox*/
padding: 10px; /*For IE*/
```
2. 条件注释。
```
<!--[if IE]>
According to the conditional comment this is Internet Explorer<br />
<![endif]-->
<!--[if IE 5]>
According to the conditional comment this is Internet Explorer 5<br />
<![endif]-->
<!--[if IE 5.0]>
According to the conditional comment this is Internet Explorer 5.0<br />
<![endif]-->
<!--[if IE 5.5]>
According to the conditional comment this is Internet Explorer 5.5<br />
<![endif]-->
<!--[if IE 6]>
According to the conditional comment this is Internet Explorer 6<br />
<![endif]-->
<!--[if IE 7]>
According to the conditional comment this is Internet Explorer 7<br />
<![endif]-->
<!--[if gte IE 5]>
According to the conditional comment this is Internet Explorer 5 and up<br />
<![endif]-->
<!--[if lt IE 6]>
According to the conditional comment this is Internet Explorer lower than 6<br />
<![endif]-->
<!--[if lte IE 5.5]>
According to the conditional comment this is Internet Explorer lower or equal to 5.5<br />
<![endif]-->
<!--[if gt IE 6]>
According to the conditional comment this is Internet Explorer greater than 6<br />
<![endif]-->
//注意：
//gt: greater than （高于）
//lte: less than or equal to （低于或等于）
```
3. 使用js判断不同浏览器，引入不同css
4. 在css里为特定浏览器设置
```
height:20px; /*For all 包括火狐 */
*height:25px; /*For IE7 & IE6*/
_height:20px; /*For IE6*/
*+height:20px /* IE7 */
```

# How do you serve your pages for feature-constrained browsers?
# What techniques/processes do you use?
# What are the different ways to visually hide content (and make it available only for screen readers)?(有哪些不同的方法可以在视觉上隐藏内容(并且只对屏幕阅读器可用)?)
```
display:none;         //缺陷:搜索引擎可能认为被隐藏的文字属于垃圾信息而被忽略屏幕阅读器（是为视觉上有障碍的人设计的读取屏幕内容的程序）会忽略被隐藏的文字，同时不利于搜索引擎。
visibility: hidden ;    //缺陷:隐藏的内容会占据他所应该占据物理空间
overflow:hidden;      
```

# Have you ever used a grid system, and if so, what do you prefer?(您使用过网格系统吗?如果使用过，您更喜欢哪种?)
# Have you used or implemented media queries or mobile specific layouts/CSS?
# Are you familiar with styling SVG?
# Can you give an example of an `@media` property other than `screen`?
# What are some of the "gotchas" for writing efficient CSS?
# What are the advantages/disadvantages of using CSS preprocessors?
  # Describe what you like and dislike about the CSS preprocessors you have used.
# How would you implement a web design comp that uses non-standard fonts?
# Explain how a browser determines what elements match a CSS selector.
# Describe pseudo-elements and discuss what they are used for.
# Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
# What does ```# { box-sizing: border-box; }``` do? What are its advantages?
# What is the CSS `display` property and can you give a few examples of its use?
# What's the difference between inline and inline-block?
# What's the difference between the "nth-of-type()" and "nth-child()" selectors?
# What's the difference between a relative, fixed, absolute and statically positioned element?
# What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
# Have you used CSS Grid?
# Can you explain the difference between coding a web site to be responsive versus using a mobile-first strategy?
# Have you ever worked with retina graphics? If so, when and what techniques did you use?
# Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?
# How is clearfix css property useful?
# Can you explain the difference between px, em and rem as they relate to font sizing?
# Can you give an example of a pseudo class? Can you provide an example use case for a pseudo class? 
# What is the difference between a block level element and an inline element. Can you provide examples of each type of element?
