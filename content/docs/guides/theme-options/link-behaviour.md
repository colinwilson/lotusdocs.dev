---
weight: 537
title: "Link behaviour"
description: "Options for Link behaviour in content pages"
icon: "link"
date: "2023-09-14T19:10:58+01:00"
lastmod: "2023-09-14T19:10:58+01:00"
draft: false
toc: true
---

## External links

By default, Lotus Docs will open external links in a new tab.

This behaviour can be disabled by setting the `extLinkNewTab` parameter to `false` in your config:

{{< tabs tabTotal="3">}}
{{% tab tabName="hugo.toml" %}}

```toml
[params.docs]
    extLinkNewTab   = false # Open external links in a new Tab? default true
```

{{% /tab %}}
{{% tab tabName="hugo.yaml" %}}

```yaml
    params:
        docs:
            extLinkNewTab: false # Open external links in a new Tab? default true
```

{{% /tab %}}
{{% tab tabName="hugo.json" %}}

```json
{
    "params": {
        "feedback": {
            "extLinkNewTab": false
        }
    }
}
```

{{% /tab %}}
{{< /tabs >}}


External links are indicated by the 'external link' icon:

![External link with external link icon](https://res.cloudinary.com/lotuslabs/image/upload/v1694716415/Lotus%20Docs/images/screenshot_lotus_docs_external_link_icon_pejqum.webp)

## Internal link preview tooltip

When this option is enabled, internal links feature a tooltip containing basic information about the destination page such as it's section, title, and description.

![Internal link preview tooltip](https://res.cloudinary.com/lotuslabs/image/upload/v1694720495/Lotus%20Docs/images/lotus_docs_tooltip_screenshot_ttmre4.webp)

### How to enable the link preview tooltip

This option can be enabled by setting the `intLinkTooltip` parameter to `true` in your config:

{{< tabs tabTotal="3">}}
{{% tab tabName="hugo.toml" %}}

```toml
[params.docs]
    intLinkTooltip   = true # Enable a tooltip for internal links that displays info about the destination? default false
```

{{% /tab %}}
{{% tab tabName="hugo.yaml" %}}

```yaml
    params:
        docs:
            intLinkTooltip: true # Enable a tooltip for internal links that displays info about the destination? default false
```

{{% /tab %}}
{{% tab tabName="hugo.json" %}}

```json
{
    "params": {
        "feedback": {
            "intLinkTooltip": true
        }
    }
}
```

{{% /tab %}}
{{< /tabs >}}

### How to format internal links for preview tooltips

The link preview tooltip feature works by validating internal links. Links can be formatted in the following ways:

1. Using the `ref` and `relref` shortcodes - These two shortcodes display the absolute and relative permalinks to a document, respectively[^1].

    {{< alert context="danger" >}}
    Be sure to use the <code>%</code> delimiter if creating internal markdown links using <code>ref</code> or <code>relref</code> shortcodes. e.g.
    <code>[Plausible Analytics Guide]({{%/* ref "/docs/guides/features/plausible-analytics" */%}})</code>
    {{< /alert >}}

    {{< alert context="warning" text="Note, that `ref` and `relref` links don’t work with `_index` or `index` files, you’ll need to use regular Markdown links to section landing or other index pages. Specify these links relative to the site’s root URL, for example:`/docs/guides/`" />}}

2. Links relative to the site's root - e.g. `/docs/guides/features/docsearch/` - [/docs/guides/features/docsearch/](/docs/guides/features/docsearch/)

Both these formats will have link preview tooltips enabled.

[^1]: [Links and cross references | Hugo](https://gohugo.io/content-management/cross-references/#use-ref-and-relref)