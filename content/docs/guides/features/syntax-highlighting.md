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

## Code Highlighters

Lotus Docs supports syntax highlighting via [Prism](https://prismjs.com/) (enabled by default) or Hugo's built-in code highlighter [Chroma](https://github.com/alecthomas/chroma). Fenced code blocks (code blocks enclosed by triple backticks above and below) that specify a code language right of the triple backticks above the code, e.g. ` ```html ` , will be automatically highlighted by Prism:

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

Result (Prism Highlighting **Enabled**):
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

Result (Prism Highlighting **Disabled**):

![chroma highlighter screenshot](https://res.cloudinary.com/lotuslabs/image/upload/v1673109682/Lotus%20Docs/images/chroma-highlighter-screenshot_xqqw5v.webp)

## Features

The following features are included when Prism highlighter is enabled:

### Copy Code Button

All code blocks feature a button that copies the code block to the clipboard when clicked. Hover over any code block and the copy button (<span class="material-icons align-text-bottom">content_copy</span>) will appear in the top right hand corner.

### Code Block id

Every code block on a page has a unique `id` attribute, an auto-generated value calculated from the `sha1` hash of the block's contents combined with it's position on the page.

## Supported Languages

Both Prism & Chroma support a huge number of languages. See the links below for a complete list of supported languages for each highlighter:

- [Prism](https://prismjs.com/#supported-languages) (≈ 290 languages)
- [Chroma](https://gohugo.io/content-management/syntax-highlighting/#list-of-chroma-highlighting-languages) (≈ 200 languages)

## Code Fence Translations

{{< alert context="info" >}}
For more extensive code highlighting with Prism consider using the [Prism Shortcode](../../shortcodes/prism/) instead of the code fences syntax.
{{< /alert >}}

If your code blocks are highlighted using the [code fences syntax](https://gohugo.io/content-management/syntax-highlighting/#highlighting-in-code-fences), Prism will translate the following Hugo Shortcode options[^1]:

- `linenos`: configure line numbers. Valid values are `true`, `false`, `table`, or `inline`. false will turn off line numbers if it’s configured to be on in site config. `table` will give copy-and-paste friendly code blocks.
- `hl_lines`: lists a set of line numbers or line number ranges to be highlighted.
- `linenostart=199`: starts the line number count from 199.
- `anchorlinenos`: Configure anchors on line numbers. Valid values are `true` or `false`;

So the following example:
````md
```go {linenos=table,hl_lines=[2,"5-7"],linenostart=199,anchorlinenos=true}
package main

import "fmt"

func main() {
    fmt.Println("hello world")
}
```
````

Will render as shown below:

```go {linenos=true,hl_lines=[2,"5-7"],linenostart=199,anchorlinenos=true,lineanchors=prefix}
package main

import "fmt"

func main() {
    fmt.Println("hello world")
}
```

{{< alert context="warning" >}}
Translation of Hugo's [Highlight Shortcode](https://gohugo.io/content-management/syntax-highlighting/#example-highlight-shortcode) syntax by Prism is currently not (fully) supported.
{{< /alert >}}


[^1]: [Highlight Shortcode - Hugo](https://gohugo.io/content-management/syntax-highlighting/#highlight-shortcode)