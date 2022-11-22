---
weight: 220
title: "Alerts"
icon: notification_important
description: "How to use Alert Shortcodes."
lead: "Alerts."
date: 2022-11-22T13:42:31+00:00
lastmod: 2022-11-22T13:42:31+00:00
draft: true
images: []
toc: true
---

## Adding a Page Alert

A page alert can be added to your markdown using the following code:

```md
{{</* alert text="This is the default alert. It consists of a default theme colour and icon." /*/>}}
```

The above code results in the following alert:

{{< alert text="This is the default alert. It consists of a default theme colour and icon." />}}

## Alert with Context

Add context to an alert via the `context` parameter:

```md
{{</* alert context="info" text="This is an alert with an <strong>info</strong> context. It consists of the info theme colour and icon." /*/>}}
```

Here's what is rendered:

{{< alert context="info" text="This is an alert with an <strong>info</strong> context. It consists of the info theme colour and icon." />}}

The additional available alert contexts include `success`, `danger`, `warning`, `primary`, `light` and `dark`:

{{< alert context="success" text="This is an alert with a <strong>success</strong> context. It consists of the success theme colour and icon." />}}

{{< alert context="danger" text="This is an alert with a <strong>danger</strong> context. It consists of the danger theme colour and icon." />}}

{{< alert context="warning" text="This is an alert with a <strong>warning</strong> context. It consists of the warning theme colour and icon." />}}

{{< alert context="primary" text="This is an alert with a <strong>primary</strong> context. Its theme and icon color are that of the current primary theme colour." />}}

{{< alert context="light" text="This is an alert with a <strong>light</strong> context. It consists of the light theme colour. The light alert has no default icon." />}}

{{< alert context="dark" text="This is an alert with a <strong>dark</strong> context. It consists of the dark theme colour. The dark alert has no default icon." />}}

## Alert with Custom Emoji Icon

The default icon of an alert can be substituted with an emoji using the `icon` parameter:

```md
{{</* alert icon="🍅" context="info" text="This is an <strong>info</strong> context alert with a tomato emoji replacing the default icon. It consists of the info theme colour and icon." /*/>}}
```

{{< alert icon="🍅" context="info" text="This is an <strong>info</strong> context alert with a tomato emoji replacing the default icon. It consists of the info theme colour and icon." />}}

## Alert with No Icon

An alert can be rendered without an icon by setting the `icon` parameter to an empty space, `icon=" "`:

{{< alert context="warning" >}}
**N.B.** The icon parameter **must** contain a space. Setting it to `icon=""` will render the default icon.
{{< /alert >}}

```md
{{</* alert icon=" " context="info" text="This <strong>info</strong> context alert has no icon." /*/>}}
```

{{< alert icon=" " context="info" text="This <strong>info</strong> context alert has no icon." />}}

## Render Markdown & HTML inside an Alert

Using a [paired shortcode](https://gohugo.io/content-management/shortcodes/) allows Markdown and HTML to be rendered inside an alert:

```
{{</* alert icon="🛒" context="success" >}}
This alert can contain **markdown** such as a list:

My Shopping List:
1. Tomatoes
2. Bananas
3. Pineapples

or HTML e.g. <strong><em>A bold, italic sentence</em></strong>
{{< /alert /*/>}}
```

{{< alert icon="🛒" context="success" >}}
This alert can contain **markdown** such as a list:

My Shopping List:
1. Tomatoes
2. Bananas
3. Pineapples

or HTML e.g. <strong><em>A bold, italic sentence</em></strong>
{{< /alert >}}