---
layout: post
tag: HTML
title: Anchor, image and table
---



## Start a new window to open link

```html
<a href="http://www.bing.com" target="_blank">www.bing.com!</a>
<!-- target="_blank" opens a new window -->
```

## Link to a location on the same page

```html
<!-- Table of Content -->
<a href="#ch1">Chapter 1 Introduction</a>
<a href="#ch2">Chapter 2 Conslusion</a>

<a name="ch1">Chapter 1 Introduction</a>
<!-- Content of chapter 1 -->
<!-- Content of chapter 1 -->
<!-- Content of chapter 1 -->

<a name="ch2">Chapter 2 Conslusion</a>
<!-- Content of chapter 2 -->
<!-- Content of chapter 2 -->
<!-- Content of chapter 2 -->
```

## Image

```html
<p><a href=""><img src="img/sample.png" /></a></p>
<!-- sample.png placed in img folder -->
<!-- img folder in same path as HTML -->
```

## Table

![image-20210618171500009](https://raw.githubusercontent.com/tosingfung/images/master/image-20210618171500009.png)

```html
<html>
<style type="text/css">
th {background: #fde;} <!--pink-->
td {background: #def;} <!--blue-->
th, td {padding: 0.5em 1em;}
caption {padding: 0 0 0.5em}
</style>
<body>
<table cellspacing="0" border="1">
<caption>Table 1</caption>
<tr>
<td rowspan="2">A1</td>
<th colspan="2" align="right">A2</th>
</tr>
<tr>
<td >B2</td>
<td rowspan="2">B3</td>
</tr>
<tr>
<th colspan="2" align="left">C1</th>
</tr>
</table>
</body>
</html>
```



