---
weight: 1137
title: "Link behaviour"
description: "Options for Link behaviour in content pages"
icon: "link"
date: "2023-09-14T19:10:58+01:00"
lastmod: "2023-09-14T19:10:58+01:00"
aliases:
    - ../guides/theme-options/link-behaviour
draft: false
toc: true
---

## Open external links in a new tab

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


External links are indicated by the 'external link' icon to the right of the link text. e.g. [Lotus Docs GitHub repository](https://github.com/colinwilson/lotusdocs):

<!-- ![External link with external link icon](https://res.cloudinary.com/lotuslabs/image/upload/v1694716415/Lotus%20Docs/images/screenshot_lotus_docs_external_link_icon_pejqum.webp) -->

## Preview tooltip for internal links

When this option is enabled, internal links feature a tooltip that displays basic information about the destination page, such as it's parent section, title, and description.

![Internal link preview tooltip](https://res.cloudinary.com/lotuslabs/image/upload/bo_1px_solid_rgb:d1d1d1,r_7/v1694720495/Lotus%20Docs/images/lotus_docs_tooltip_screenshot_ttmre4.webp)

### How to enable the link preview tooltip

To enable tooltip previews for internal links, set the `intLinkTooltip` parameter to `true` in your config:

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

### How to format links in your Markdown for preview tooltips

The link preview tooltip feature works by using a custom [Markdown render hook](https://gohugo.io/templates/render-hooks/) to first validate a link is internal, and then enables the tooltip function for those links. Markdown links in your content pages can be formatted in one of two ways:

1. Using the `relref` shortcode - This shortcode displays the relative permalink to a document[^1].

    {{< alert context="danger" >}}
    Be sure to use the <code>%</code> delimiter if creating internal markdown links using the <code>relref</code> shortcode. e.g.
    <code>[Plausible Analytics Guide]({{%/* relref "/docs/features/plausible-analytics" */%}})</code>
    {{< /alert >}}

    {{< alert context="warning" text="Note, that `relref` links don’t work with `_index` or `index` files, you’ll need to use regular Markdown links to section landing or other index pages. Specify these links relative to the site’s root URL, for example:`/docs/guides/`" />}}

2. Links relative to the site's root - e.g. `/docs/guides/features/docsearch/` - [/docs/guides/features/docsearch/](/docs/features/docsearch/)

Both these formats will enable preview tooltips on internal links. However, one benefit of using `relref` to link internal content is that the `hugo` command will produce an error if an internal link's path is invalid.

[^1]: [Links and cross references | Hugo](https://gohugo.io/content-management/cross-references/#use-ref-and-relref)