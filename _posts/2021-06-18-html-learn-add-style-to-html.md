---
layout: post
tag: [html-learn]
title: "Add style to HTML"
---

- 3 ways to add styles

<!--more-->

## External .css file

```css
/* mystyle.css external stylesheet */
/* placed in same folder as .html */
h1 {
padding: 0;
margin: 0;
background-color: #ddd;
color: #003151;
font-family: roboto, arial, sans-serif;
font-size: 2em;
font-weight: bold;
font-style: italic;
line-height: 1.2;
text-align: center;
text-decoration: underline;}
```

```html
<!DOCTYPE html>
<html>

<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>

<body>
<h1>heading1</h1>
</body>

</html>
```

## Embed stylesheet in header

```html

<!DOCTYPE html>
<html>

<head>
<style type="text/css">
h1 {
padding: 0;
margin: 0;
background-color: #ddd;
color: #003151;
font-family: roboto, arial, sans-serif;
font-size: 2em;
font-weight: bold;
font-style: italic;
line-height: 1.2;
text-align: center;
text-decoration: underline;
}
</style>
</head>

<body>
<h1>heading1</h1>
</body>

</html>
```

## Enforce a style to element

```html

<!DOCTYPE html>
<html>

<head>
</head>

<body>
<h1 style="
padding: 0;
margin: 0;
background-color: #ddd;
color: #003151;
font-family: roboto, arial, sans-serif;
font-size: 2em;
font-weight: bold;
font-style: italic;
line-height: 1.2;
text-align: center;
text-decoration: underline;">
heading1</h1>
</body>

</html>
```

