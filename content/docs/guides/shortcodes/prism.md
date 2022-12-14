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

Lotus Docs supports syntax highlighting via [Prism](https://prismjs.com/) (enabled by default). Fenced code blocks (code blocks with triple backticks before and after) that specify a code language next to the triple backticks placed before the block of code, e.g. ` ```html ` , will automatically be highlighted by Prism:

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

The same result can be achieved by using a paired Prism shortcode with the language declared using the `lang` parameter :

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

All code blocks highlighted by Prism feature the [Copy to Clipboard Button](https://prismjs.com/plugins/copy-to-clipboard/) plugin. Hover over (or tap if on mobile) the examples above and the copy button appears in the top right hand corner of the code block. Click this button to copy the code to your clipboard.

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

Combining `line` & `start` options requires the use of the `line-offset` option:

```go
{{</* prism lang="html" line-numbers="true" start="48" line="49-51,54" line-offset="48" >}}
<html>
  <head>
  ...
{{< /prism */>}}
```
This renders the following code block:

{{< prism lang="html" line-numbers="true" start="48" line="49-51,54" line-offset="48" >}}
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

Prism syntax highlighting can be disabled by setting `[params.docs.prism]` to `false` in the `config.toml` configuration file.

## Command line

TBC