---
title: hexo为文章代码增加代码框，让代码放在框内css代码
date: 2026-02-23 12:17:29
tags:
---
<div class="red-box">
```css
// 自定义代码块红色方框
.red-box
    border: 2px solid red           
    padding: 10px           
    border-radius: 5px      
    background-color: #fff5f5   
    overflow-x: auto
```
</div>
打开你的博客主题目录下的 source/css/_custom/custom.styl（或 custom.css），添加以上代码.  

以后写文章用  
```php
<div class="red-box">
```
代码
```
</div>
```
框起来就可以了

