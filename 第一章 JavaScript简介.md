[TOC]
# 第一章 JavaScript简介

## 1.1 JavaScript实现 

**完整的JavaScript由3个部分组成:**  
1. ECMAScript(European Computer Manufacturers Association)
2. DOM
3. BOM

## 1.2 ECMAScript
- ECMAScript-262定义的这门语言的基础
- ECMAScrpt规定了语言由以下部分组成：  
    * 语法
    * 类型
    * 语句
    * 关键字
    * 保留字
    * 操作符
    * 对象

## 1.3 文档对象模型 DOM  
DOM是针对XML但经过扩展用于HMTL的应用程序编程接口(API)。  
DOM把整个页面映射为一个多层节点结构。  

### 1.3.1 DOM级别
- DOM1级：由2个部分组成
    + DOM核心： 规定的是如何映射基于XML的文档结构；
    + DOM HTML： 在DOM核心的基础上加以扩展，添加了针对HTML的对象和方法。
- DOM2级： 引入以下新模块：
    + DOM视图(DOM View)： 定义了跟踪不同文档(如：应用CSS前后的文档)视图的接口；
    + DOM事件(DOM Event): 定义了事件和事件处理接口；
    + DOM样式(DOM Style)： 定义了基于CSS为元素应用样式的接口；
    + DOM遍历和范围(DOM Traversal and Range)： 定义了遍历和操作文档树的接口。
- DOM3级： 进一步扩展DOM  
    + DOM加载和保存(DOM Load and Save)
    + DOM验证(DOM Validation)  

## 1.4 浏览器对象模型 BOM  

从根本上讲，BOM只处理浏览器窗口和框架；但人们也习惯把所有针对浏览器的JavaScript扩展算作BOM的一部分：  

- 弹出新浏览器窗口的功能；
- 移动，缩放和关闭浏览器的功能；
- 提供浏览器详细信息的navigator对象；
- 提供浏览器所加载页面详细信息的location对象；
- 提供用户显示器分辨率详细信息的screen对象；
- 对cookie的支持；
- 像XMLHTTPRequest和IE的ActiveXObject 这样的自定义对象。

## 1.5 小结

JavaScript是一种专为与网页交互设计的脚本语言，由下列三个不同部分组成：

- ECMAScript： 由ECMAScript-262定义，提供核心语言功能；
- 文档对象模型(DOM)： 提供访问和操作网页内容的方法和接口；
- 浏览器对象模型(BOM)： 提供与浏览器交互的方法和接口。