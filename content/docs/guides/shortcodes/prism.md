---
weight: 242
title: "Prism"
icon: change_history
description: "How to use the Prism Shortcode for syntax highlighting code blocks."
date: 2022-11-28T04:05:31+00:00
lastmod: 2022-11-28T04:05:31+00:00
draft: true
images: []
toc: true
---

## Syntax highlighting

[Prism](https://prismjs.com/) syntax highlighting is enabled by default in Lotus Docs. Code blocks enclosed in triple backticks with a declared code language, e.g. ` ```html ` , will automatically be highlighted by Prism:

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

The same result can be achieved by using a paired Prism shortcode with the language declared with the `lang` parameter :

```go
{{</* prism lang="html" >}}
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
{{< /prism */>}}
```

All code blocks highlighted by Prism feature the [Copy to Clipboard Button](https://prismjs.com/plugins/copy-to-clipboard/) plugin. Hover over (or tap if on mobile) either of the above examples and you'll see the copy button appear in the top right hand corner of the code block. Click this button to copy the code to your clipboard.

## Line Highlighting

The Prism shortcode can highlight specific lines and/or line ranges in code blocks using the `line` parameter:
```go
{{</* prism lang="html" line="2-4,6" >}}
<html>
  <head>
  ...
{{< /prism */>}}
```
See the rendered example below:

{{< prism lang="html" line="2-4,6" >}}
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
{{< /prism >}}

## Line numbers

Add line numbers to your code with the `line-numbers="true"` parameter:

{{< prism lang="html" line-numbers="true" >}}
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
{{< /prism >}}

The number at which the line starts can be specified by the `start` parameter. e.g. `start="48"`:

{{< prism lang="html" line-numbers="true" start="48" >}}
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
{{< /prism >}}

## Combined Line Parameters

Prism's [Line Highlighting](https://prismjs.com/plugins/line-highlight/) & [Line Numbers](https://prismjs.com/plugins/line-numbers/) plugins are compatible with each other. So the `line` & `line-numbers` options can be combined to display both, line numbers and highlight specified lines in a code block:

```go
{{</* prism lang="html" line-numbers="true" line="2-4,6" >}}
<html>
  <head>
  ...
{{< /prism */>}}
```
This renders the following code block:

{{< prism lang="html" line-numbers="true" line="2-4,6" >}}
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
{{< /prism >}}

## Disable Prism

TBC

## Command line

TBC