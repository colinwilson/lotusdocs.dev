---
weight: 545
title: "Dark Mode"
icon: dark_mode
description: "Lotus Docs Dark Mode"
date: 2023-08-11T04:03:15+00:00
lastmod: 2023-08-11T04:03:15+00:00
draft: true
images: []
toc: true
---

1. blah

    ```html
    <a>Hello</a>
    ```

    {{< alert icon="🍅" context="success" >}}

    This is an alert **that** should be indented.

    {{< /alert >}}

    1. bleed

        {{< alert icon="🍅" context="success" >}}

        This is an alert **that** should be indented.

        {{< /alert >}}

2. Bloat

    {{% prism lang="html" %}}
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
    {{% /prism %}}

    {{% alert icon="🍅" context="success" text="This is an alert **that** should be indented." /%}}

    {{% alert icon="🍅" context="success" %}}

    This is an alert **that** should be indented.

    {{% /alert %}}

    Hello

    {{< alert icon="🍅" context="success" >}}

    This is an alert **that** should be indented.

    {{< /alert >}}