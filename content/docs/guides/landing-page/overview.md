---
weight: 510
title: "Overview"
description: "An overview of the Lotus Docs landing page"
icon: overview
date: "2023-11-16T19:49:34Z"
lastmod: "2023-11-16T19:49:34Z"
draft: false
toc: true
---

The Lotus Docs theme features a built-in landing page that's easy to customise and manage.

![Landing Page Screenshot](https://res.cloudinary.com/lotuslabs/image/upload/bo_1px_solid_rgb:c4c4c4,c_scale,r_8,w_800/v1700164935/Lotus%20Docs/screenshots/lotusdocs_screenshot_2023-11-16_at_19-59-06_btprao.webp)
{.text-center}

The landing page layout is comprised of individual sections, each with their own [template]({{% relref "templates" %}}). These sections are configured via a [data file](https://gohugo.io/templates/data-templates/#data-files-in-themes) named `landing.yaml` in your [`/data` directory.](https://gohugo.io/templates/data-templates/#the-data-directory)

## Data file configuration

Here's a screenshot of the hero section from [lotusdocs.dev](https://lotusdocs.dev):

![Lotus Docs Landing Page Hero Section Screenshot](https://res.cloudinary.com/lotuslabs/image/upload/bo_1px_solid_rgb:c4c4c4,c_scale,r_8,w_1000/v1700171635/Lotus%20Docs/screenshots/lotusdocs_screenshot_landing_page_hero_section_ddrfvo.webp)
{.text-center}

And here's the part of the data file (`/data/landing.yaml`) used to enable and configure that section:

{{% alert context="info" text="Lotus Docs supports data files in `.yaml`, `.json`, and `.toml` formats" /%}}

{{< tabs tabTotal="3">}}
{{% tab tabName="landing.yaml" %}}

```yaml
# Hero
hero:
  enable: true
  weight: 10
  template: hero

  backgroundImage:
    path: "images/templates/hero"
    filename:
      desktop: "gradient-desktop.webp"
      mobile: "gradient-mobile.webp"

  badge:
    text: v0.1.0
    color: primary # primary, secondary, success, danger, warning, info, light, dark
    pill: false # boolean
    soft: true # boolean

  title: "Lotus Docs"
  subtitle: A lightweight, **modern documentation** theme for Hugo. Easily customised for building **fast**, **secure**, and **SEO-friendly** documentation sites.

  image:
    path: "images" # path to image under configured assets directory. default 'images'
    filename: "lotus_docs_screenshot.png" # filename of your hero image (including file extension)
    alt: "Lotus Docs Screenshot" # Optional but recommended
    boxShadow: true # default 'false' (excludes .svg images)
    rounded: true # round the image corners? default 'false' (excludes .svg images)

  ctaButton:
    icon: rocket_launch
    btnText: "Get Started"
    url: "/docs/quickstart/#create-a-new-lotus-docs-site"
  cta2Button:
    icon: construction
    btnText: "In Development"
    url: "https://github.com/colinwilson/lotusdocs"

  info: "**Open Source** MIT Licensed."
  ...
```

{{% /tab %}}
{{% tab tabName="landing.json" %}}

```json
{
    "hero": {
        "enable": true,
        "weight": 10,
        "template": "hero",
        "backgroundImage": {
            "path": "images/templates/hero",
            "filename": {
                "desktop": "gradient-desktop.webp",
                "mobile": "gradient-mobile.webp"
            }
        },
        "badge": {
            "text": "v0.1.0",
            "color": "primary",
            "pill": false,
            "soft": true
        },
        "title": "Lotus Docs",
        "subtitle": "A lightweight, **modern documentation** theme for Hugo. Easily customised for building **fast**, **secure**, and **SEO-friendly** documentation sites.",
        "image": {
            "path": "images",
            "filename": "lotus_docs_screenshot.png",
            "alt": "Lotus Docs Screenshot",
            "boxShadow": true,
            "rounded": true
        },
        "ctaButton": {
            "icon": "rocket_launch",
            "btnText": "Get Started",
            "url": "/docs/quickstart/#create-a-new-lotus-docs-site"
        },
        "cta2Button": {
            "icon": "construction",
            "btnText": "In Development",
            "url": "https://github.com/colinwilson/lotusdocs"
        },
        "info": "**Open Source** MIT Licensed."
    },
    ....
}
```

{{% /tab %}}
{{% tab tabName="landing.toml" %}}

```toml
[hero]
enable = true
weight = 10
template = "hero"
title = "Lotus Docs"
subtitle = "A lightweight, **modern documentation** theme for Hugo. Easily customised for building **fast**, **secure**, and **SEO-friendly** documentation sites."
info = "**Open Source** MIT Licensed."

  [hero.backgroundImage]
  path = "images/templates/hero"

    [hero.backgroundImage.filename]
    desktop = "gradient-desktop.webp"
    mobile = "gradient-mobile.webp"

  [hero.badge]
  text = "v0.1.0"
  color = "primary"
  pill = false
  soft = true

  [hero.image]
  path = "images"
  filename = "lotus_docs_screenshot.png"
  alt = "Lotus Docs Screenshot"
  boxShadow = true
  rounded = true

  [hero.ctaButton]
  icon = "rocket_launch"
  btnText = "Get Started"
  url = "/docs/quickstart/#create-a-new-lotus-docs-site"

  [hero.cta2Button]
  icon = "construction"
  btnText = "In Development"
  url = "https://github.com/colinwilson/lotusdocs"
  ...
```

{{% /tab %}}
{{< /tabs >}}