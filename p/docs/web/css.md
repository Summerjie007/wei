# CSS原理
## 一、什么是 CSS 

•CSS 是 Cascading Style Sheets(层叠样式表)的简称。  
•CSS 语言是一种标记语言，它不需要编译，可以直接由浏览器解释执行(属于浏览器解释型语言)。  
•在标准网页设计中 CSS 负责网页内容 (XHTML)的表现。  
•CSS 文件也可以说是一个文本文件，它包含了一些 CSS 标记，CSS 文件必须使用 css 为文件名后缀。  
•可以通过简单的更改 CSS 文件，改变网页的整体表现形式，可以减少我们的工作量，所以它是每一个网页设计人员的必修课。  
•CSS是由W3C的CSS工作组产生和维护的。  


## 二、 浏览器是如何渲染页面和加载页面  

浏览器的常规流程：  

1. 浏览器下载的顺序是从上到下，渲染的顺序也是从上到下，下载和渲染是同时进行的。

2. 在渲染到页面的某一部分时，其上面的所有部分都已经下载完成（并不是说所有相关联的元素都已经下载完）。

3. 如果遇到语义解释性的标签嵌入文件（JS脚本，CSS样式），那么此时IE的下载过程会启用单独连接进行下载。

4. 并且在下载后进行解析，解析过程中，停止页面所有往下元素的下载。

5. 样式表在下载完成后，将和以前下载的所有样式表一起进行解析，解析完成后，将对此前所有元素（含以前已经渲染的）重新进行渲染。

6. JS、CSS中如有重定义，后定义函数将覆盖前定义函数。

## 三、 浏览器对 CSS 的匹配原理  
浏览器CSS匹配不是从左到右进行查找，而是从右到左进行查找。比如之前说的 DIV#divBox p span.red{color:red;}，浏览器的查找顺序如下：先查找 html 中所有 class=’red’ 的 span 元素，找到后，再查找其父辈元素中是否有p元素，再判断p的父元素中是否有 id 为 divBox 的 div 元素，如果都存在，则 CSS 匹配上。

　　浏览器从右到左进行查找的好处是为了尽早过滤掉一些无关的样式规则和元素。Firefox 称这种查找方式为 keyselector(关键字查询)，所谓的关键字就是样式规则中最后(最右边)的规则，上面的 key 就是 span.red。  
ps:(class 会在第一次载入中被缓存，在层叠中会有更加好的效果，在根部元素采用id会具有更加好（id有微妙的速度优势）)。