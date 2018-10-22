[TOC]
# 第二章 在HTML中使用JavaScript

## 2.1 `<script>` 元素  

**`<script>`定义了6个元素**  

- async : 可选。表示立即下载脚本，但不妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。==只针对外部脚本有效==。
- charset : 可选。表示通过src属性指定的代码的字符集。由于==大多数浏览器会忽略它的值==。因此这个属性很少有人用。
- defer ： 可选。表示脚本可以延迟到文档完全被解析和显示之后再执行。==只对外部文件有效==。
- language : 已废弃。
- src ： 可选。表示包含执行代码的外部文件。
- type : 可选。 可以看做是language的代替属性：表示编写代码使用脚本语言的内容类型(也称为==MIME类型==)。虽然text/javascript和text/ecmascript都以不推荐使用。实际上，服务器在传送JavaScript文件时使用的MIME类型通常是application/x-javascript。如果没有指定这个属性，其默认值仍为text/javascript。  


**使用`<script>`的2种方法：**  

1. 在页面中嵌入JavaScript代码；
2. 引用外部JavaScript文件。  

在包含`<script>`元素内部的JavaScript代码将被==从上至下==依次解释。  
在解释器对`<script>`元素内部的所有代码求值完毕以前，页面中的其余内容都不会被浏览器加载或显示。  
在使用`<script>`嵌入JavaScript代码时，浏览器遇到字符串`</script>`就会认为是结束标志。需要通过转义字符`\`解决。  

引用外部JavaScript文件  
`<script src="文件名.js"></script>`  
如果在`<script>`和`</script>` 之间嵌入代码，则只会下载并执行外部脚本文件，嵌入的代码会被忽略。  
scr属性还可以包含来自外域的JavaScript文件。  
无论如何包含代码，只要不存在defer和async属性，浏览器都会按照`<script>`元素在页面中出现的先后顺序对它们依次进行解析。  

### 2.1.1 标签位置

1. 在`<head>`元素中：这种做法必须等所有的JavaScript代码都被下载，解析和执行完以后才能开始呈现页面内容；
2. 在`<body>`元素底部： 在页面内容完全呈现在浏览器之后再解析JavaScript代码，缩短空白页面的显示时间，从而感觉打开页面速度加快。

### 2.1.2 延迟脚本

`<script type="text/javascript" defer="defer" scr="example.js"></script>`  
defer属性的脚本会被延迟到整个页面都解析完毕后再运行。  
HTML5规范要求脚本按照他们出现的先后顺序执行，因此第一个延迟脚本会优先第二个延迟脚本执行，而且脚本会优先于`DOMContentLoaded`事件执行。但在现实中，延迟脚本不一定会按照顺序执行，也不一定会在`DOMContentLoaded`事件触发前执行，因此==最好只包含一个延迟脚本==。  
defer属性只适用于外部脚本文件。

### 2.1.3 异步脚本  

`<script type="text/javascript" async scr="example.js"></script>`   
async属性只适用于外部脚本文件。
async属性不能保证按照指定它们的先后顺序执行，因此要确保脚本之间互不依赖。
async属性的目的是不让页面等待脚本下载和执行，从而异步加载页面的其他内容。建议异步脚本不要在加载期间修改DOM。
异步脚本一定会在页面的load事件前执行，但可能会在`DOMContentLoaded`事件触发之前或之后执行。

## 2.2 嵌入代码和外部文件

使用外部文件的优点：

- 可维护性
- 可缓存
- 适应未来

## 2.3 文档模式 
IE5.5引入了文档模式的概念，通过文档类型(doctype)来实现。最初的2种文档模式是：==混杂模式和标准模式==。

HTML5文档模式： `<!DOCTYPE HTML>`

## 2.4 `<noscript>`元素
为了早期那些不支持JavaScript的浏览器而使用的元素。

`<noscript>`元素中的内容在下列清空中显示： 

- 浏览器不支持脚本
- 浏览器支持脚本，但脚本被禁用。

满足以上任何一个条件，浏览器都会显示`<noscript>`中的内容，其他情况都不会显示。


```
<html>
    <head>
        <title>123</title>
        <script></script>
    </head>
    <body>
        <noscript>
            <p>本页面需要浏览器启用JavaScript</p>
        </noscript>
    </body>
</html>
```

## 2.5 小结
使用`<script>`元素吧JavaScript嵌入到HTML中。  
在使用中需要注意：

- 在包含外部JavaScript文件时，必须将src属性设置为指向相应文件件的URL。而这个文件可以是与包含它的页面位于同一个服务器上文件，也可以是其他任何域中的文件。
- 所有`<script>`元素都会按照它们在页面中出现的先后顺序依次被解析。在不使用defer和async属性的情况下，只有在解析完前面`<script>`元素中的所有代码之后，才会开始解析下一个
`<script>`元素中的代码。
- 由于浏览器会先解析完不使用defer使用的`<script>`元素中的代码，然后再解析后面的内容，所以一般应该把`<script>`元素放在页面的最后，即`</body>`标签前。
- 使用defer属性可以让脚本在文档完全呈现之后再执行。延迟脚本总是按照指定它们的顺序执行。
- 使用async属性可以表示当前脚本不必等待其他脚本，也不必阻塞文档呈现。不能保证异步脚本按照它们在页面中出现的顺序执行。
