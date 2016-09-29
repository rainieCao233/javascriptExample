### 在HTML中使用Script

### script元素

- 六个属性：
 - async：立即下载脚本
 - charset：代码字符集
 - defer：脚本可以延迟到文档完全被解析和显示之后再执行
 - language : 废弃
 - src : source
 - type : 内容类型

> 现代Web 应用程序一般都把全部JavaScript 引用放在<body>元素中页面内容的后面，或者使用defer属性，H5中规定按照顺序延迟，标记为async 的脚本并不保证按照指定它们的先后顺序执行

### 文档模式

> 混杂模式（quirks mode）和标准模式（standards mode）

```
<!-- HTML 4.01 严格型 -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<!-- XHTML 1.0 严格型 -->
<!DOCTYPE html PUBLIC
"-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<!-- HTML 5 -->
<!DOCTYPE html>
```

#### noscript元素
> 当浏览器不支持JavaScript 时使用noscript元素让页面平稳地退化
