---
weight: 210
title: "Syntax Highlighting"
description: "Code highlighting in Lotus Docs."
icon: highlight
date: 2022-12-16T01:07:15+00:00
lastmod: 2022-12-16T01:07:15+00:00
draft: true
images: []
---

## Code Highlighting Options

Lotus Docs supports syntax highlighting via [Prism](https://prismjs.com/) (enabled by default) or Hugo's built-in code highlighter [Chroma](https://github.com/alecthomas/chroma). Fenced code blocks (code blocks with triple backticks before and after) that specify a code language next to the triple backticks placed before the block of code, e.g. ` ```html ` , will automatically be highlighted by Prism:

````md
```html
<html>
  <head>
    <title>Buy cool new product</title>
  </head>
  <body>
    <!-- Use action="/create-checkout-session.php" if your server is PHP based. -->
    <form action="/create-checkout-session" method="POST">
      <button type="submit">Checkout</button>
    </form>
  </body>
</html>
```
````

Result:
```html
<html>
  <head>
    <title>Buy cool new product</title>
  </head>
  <body>
    <!-- Use action="/create-checkout-session.php" if your server is PHP based. -->
    <form action="/create-checkout-session" method="POST">
      <button type="submit">Checkout</button>
    </form>
  </body>
</html>
```