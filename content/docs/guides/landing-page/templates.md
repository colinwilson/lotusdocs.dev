---
weight: 520
title: "Templates"
icon: dashboard
description: "A guide to using the Lotus Docs landing page templates."
date: 2022-12-08T19:19:31+00:00
lastmod: 2022-12-08T19:19:31+00:00
draft: false
images: []
toc: true
---

## Introduction

Each section on the landing page corresponds to a specific template with its own set of parameters for customisation. There are (currently) 4 templates.

{{< table "table table-striped" >}}
| Name | Type | Description |
|---------|-----|-------|
| [`hero`](#hero) | hero | A basic hero template with text and CTA buttons on the left and an image on the right. Traditionally the first section of a landing page. |
| [`feature grid`](#feature-grid) | grid | A multi row, 3 column grid listing features. Each feature consists of an icon, title, and descriptive text. |
| [`image text`](#image-text) | image + text | A 2 column section with an image on the left (or the right) with some descriptive text, lists and a call-to-action button adjacent. |
| [`image compare`](#image-compare) | image comparison | Utilizes the [image-compare-viewer](https://github.com/kylewetton/image-compare-viewer) library by [Kyle Wetton](https://github.com/kylewetton) to compare multiple before and after images. Includes an auto-generated tab to switch between image comparison sets. |
{{</ table >}}

{{% alert text="Additional templates and template types are part of the Lotus Docs roadmap" /%}}

## Required data file parameters

For each enabled section defined in your data file (`/data/landing.yaml`), the following parameters are required:

- Choose a unique name for each section array defined in the data file. e.g. `myCoolHero` for the section using the `hero` template.

- **`weight`** - This key is nested under a section's array title. It's value defines where in the landing page the section should appear. Sections with lower values appear higher up on the rendered landing page.

- **`template`** - This key defines the template the section should use.

Here's an example of how the `weight` key (lines 4, 11, and 18 below) is used to configure the order in which sections on the landing page appear:

{{< tabs tabTotal="2">}}
{{% tab tabName="landing.yaml (partial)" %}}

```yaml {hl_lines=[4,11,18]}
# Hero
myCoolHero: # section title
  enable: true
  weight: 10 # position the 'myCoolHero' section at the top of the landing page
  template: hero # use the 'hero' template for this section
  ...

# Feature Grid
coolAppFeatures:
  enable: true
  weight: 20
  template: feature grid
  ...

# Image Compare
appImageCompare:
  enable: true
  weight: 30
  template: image compare
  ...
```

{{% /tab %}}
{{% tab tabName="Rendered Result Diagram" %}}

This diagram illustrates the order in which each section configured in the first tab will appear once the landing page is rendered.

![Lotus Docs Rendered Landing Page Diagram](https://res.cloudinary.com/lotuslabs/image/upload/v1700192360/Lotus%20Docs/images/lotusdocs_landing_page_sections_diag_outlined_rqs40w.svg)

{{% /tab %}}
{{< /tabs >}}

## Section anchors

Each section defined in the `landing.yaml` configuration has an `id` auto-generated using the section name. So a section named `appImageCompare` can be linked using the anchor `/#appImageCompare`. This is useful for linking from one section to another on the landing page.

## Hero

The `hero` template has 8 configurable components. The illustration below demonstrates a rendered layout of these components.

![Lotus Docs Landing Page Hero Section Diagram](https://res.cloudinary.com/lotuslabs/image/upload/bo_1px_solid_rgb:c4c4c4,r_8/v1700247403/Lotus%20Docs/images/lotusdocs_hero_template_diag_v1.1_hydkjq.webp)
{.text-center}

Configure the options illustrated above using your `landing.yaml` data configuration file:

{{< tabs tabTotal="6">}}
{{% tab tabName="1. title / 2. subtitle / 3. info" %}}

```yaml
# landing.yaml
heroSection:
    ...
    title: "Lotus Docs" # 1
    subtitle: A lightweight, **modern documentation** theme for Hugo. Easily customised for building **fast**, **secure**, and **SEO-friendly** documentation sites. # 2
    info: "**Open Source** MIT Licensed." # 3
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `title` | N/A | The main title of the hero section (**h4** sized font).  |
| `subtitle` | N/A | Subheading text. Supports Markdown. |
| `info` | N/A | Useful for any additional text you may wish to add under the call-to-action buttons.  |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="4 .backgroundImage" %}}

```yaml
# landing.yaml
heroSection:
    ...
    backgroundImage: # 4
        path: "images/templates/hero"
        filename:
            desktop: "gradient-desktop.webp"
            mobile: "gradient-mobile.webp"
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `backgroundImage.path` | N/A | Set the asset directory path where your background image(s) is/are located.  |
| `backgroundImage.filename.desktop` | N/A | Set the name of the image file to use for the desktop background. Support for `.jpg`, `.png`, `.webp`, and `.svg` image formats. |
| `backgroundImage.filename.mobile` | N/A | Set the name of the image file to use for the mobile background. Supports `.jpg`, `.png`, `.webp`, and `.svg` image formats.  |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="5. image" %}}

```yaml
# landing.yaml
heroSection:
    ...
    image: # 5
        path: "images"
        filename: "lotus_docs_screenshot.png"
        alt: "Lotus Docs Screenshot" # Optional but recommended
        boxShadow: true # default 'false' (excludes .svg images)
        rounded: true # round the image corners? default 'false' (excludes .svg images)
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `image.path` | N/A | Set the asset directory path where your hero image is located.  |
| `image.filename` | N/A | Set the name of the hero image file to use. Support for `.jpg`, `.png`, `.webp`, and `.svg` image formats. |
| `image.alt` | N/A | Set the the `alt` text for the hero image (**optional**).  |
| `image.boxShadow` | `false` | Enable a subtle CSS [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow) for the hero image? (does **not** support `.svg` image formats) |
| `image.rounded` | `false` | Enable rounded corners for the top of the image (utilizes Bootstrap's [`rounded-top-4`](https://getbootstrap.com/docs/5.3/utilities/borders/#radius)). (does **not** support `.svg` image formats)  |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="6. ctaButton / cta2Button" %}}

```yaml
# landing.yaml
heroSection:
    ...
    ctaButton:
        icon: rocket_launch
        btnText: "Get Started"
        url: "/docs/quickstart/#create-a-new-lotus-docs-site"
    cta2Button:
        icon: construction
        btnText: "In Development"
        url: "https://github.com/colinwilson/lotusdocs"
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `ctaButton.icon`, `cta2Button.icon` | N/A | Define a [Material Symbol](https://fonts.google.com/icons?icon.style=Outlined) icon for the button. **e.g.** setting the value to `rocket_launch` will prefix the button text with a <span class="material-icons align-text-bottom">rocket_launch</span> icon. (**optional**)  |
| `ctaButton.btnText`, `cta2Button.btnText` | N/A | Set the text for the button. |
| `ctaButton.url`, `cta2Button.url` | N/A | Set URL for the button.  |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="7. badge" %}}

```yaml
# landing.yaml
heroSection:
    ...
    badge:
        text: v0.1.0
        color: primary
        pill: false
        soft: true
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `badge.text` | N/A | Set the text for the badge. (**optional**)  |
| `badge.color` | N/A | Set the color for the badge. Valid values: `primary`, `secondary`, `success`, `warning`, `danger`, `info`,  and `dark` |
| `badge.pill` | `false` | Switch badge style to a [pill](https://getbootstrap.com/docs/5.3/components/badge)?.  |
| `badge.soft` | `false` | Switch badge background color to a 'softer' version of the theme color defined by `color`.  |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="8. titleLogo" %}}

```yaml
# landing.yaml
heroSection:
    ...
    titleLogo:
        path: "images/logos"
        filename: "title_logo.png"
        alt: "Lotus Docs Logo"
        height: 80px
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `titleLogo.path` | N/A | Set the asset directory path where your logo image is located. |
| `titleLogo.filename` | N/A | Set the name of the logo image file to use. Support for `.jpg`, `.png`, `.webp`, and `.svg` image formats. |
| `titleLogo.alt` | N/A | Set the the `alt` text for the logo image (**optional**).  |
| `titleLogo.height` | `70px` | Set the height (in `px`) for the logo image. (does not apply to `.svg` image formats).  |
{{</ table >}}

{{% /tab %}}
{{< /tabs >}}

## Feature Grid

The `feature grid` template has 5 configurable components. The illustration below demonstrates a rendered layout of these components.

![Lotus Docs Landing Page Feature Grid Section Diagram](https://res.cloudinary.com/lotuslabs/image/upload/bo_1px_solid_rgb:c4c4c4,r_8/v1700520249/Lotus%20Docs/images/lotusdocs_feature_grid_template_diag_v1.1_cz593r.webp)
{.text-center}

{{< tabs tabTotal="2">}}
{{% tab tabName="1. title / 2. subtitle" %}}

```yaml
# landing.yaml
featureGrid:
    ...
    title: Why choose Lotus Docs? # 1
    subtitle: Lotus Docs is a highly configurable Hugo documentation theme. Yet, with the default configuration you can deploy and publish your documentation site in a matter of minutes. Check out some core features below. # 2
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `title` | N/A | The main title of the `feature grid` template (**h4** sized font).  |
| `subtitle` | N/A | Subheading text. Supports Markdown. |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="3., 4., 5., 6. feature item" %}}

```yaml
# landing.yaml
featureGrid:
    ...
    items:
    - title: Fast # 4
      icon: speed # 3
      description: 4 x 100's score on Google Lighthouse by default. Lotus Docs removes unused CSS, prefetches asset links, and lazy loads content images. # 5
      ctaLink: # 6
        text: learn more
        url: /docs/

    - title: SEO Friendly
      icon: trending_up
      description: Data is automatically structured to be SEO friendly. Includes Meta tags, Opengraph, and Twitter cards. Choose the settings that best suit you.
      ctaLink:
        text: learn more
        url: /docs/
    ...
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `items.title` | N/A | Set the title for the feature item.  |
| `items.icon` | N/A | Set the [Material Symbol](https://fonts.google.com/icons?icon.style=Outlined) icon for the feature item. **e.g.** setting the value to `trending_up` will prefix the item's `title` text with a <span class="material-icons align-text-bottom">trending_up</span> icon. (**optional**) |
| `items.description` | N/A | Set the description text for the feature item. |
| `items.ctaLink.text` | N/A | Set the text for the call-to-action link. |
| `items.ctaLink.url` | N/A | Set the URL for the call-to-action link. |
{{</ table >}}

{{% /tab %}}
{{< /tabs >}}

### Grid items wrap behaviour

The feature grid template arranges `items` into rows of 3 columns. Each group of extra `items` will wrap onto a new line:

![Feature Grid Layout Wrap Behaviour Diagram](https://res.cloudinary.com/lotuslabs/image/upload/v1700273792/Lotus%20Docs/images/lotusdocs_landing_page_feature_grid_layout_diag_svg_export_wtdcbv.svg)

## Image Compare

The `image compare` template allows multiple image comparisons to be presented in a single section. Each pair or compared images are selected by tabs. The template has 5 configurable components. See the illustration below for a rendered layout of these components.

![Lotus Docs Landing Page Image Compare Section Diagram](https://res.cloudinary.com/lotuslabs/image/upload/bo_1px_solid_rgb:c4c4c4,r_8/v1700316794/Lotus%20Docs/images/lotusdocs_image_compare_template_diag_v1.0_efkkax.webp)
{.text-center}

{{< tabs tabTotal="3">}}
{{% tab tabName="1. title / 2. subtitle" %}}

```yaml
# landing.yaml
imageCompare:
    ...
    title: Customise The Lotus Docs Appearance # 1
    subtitle: Much of Lotus Docs' appearance can be customised. Dark mode is optional (enabled by default) and you can choose a Google font that suites you via the config parameters. #2
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `title` | N/A | The main title of the `image compare` template (**h4** sized font).  |
| `subtitle` | N/A | Subheading text. Supports Markdown. |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="3. tab navigation" %}}

This tabbed navigation is auto-generated. Each tab is labelled according to its item `title` (nested under `items`. See line **5**, **7**, **9** below).

```yaml {hl_lines=[5,7,9]}
# landing.yaml
imageCompare:
    ...
    items:
        - title: Dark Mode
        ...
        - title: Custom Fonts
        ...
        - title: Accent Color
        ...
    ...
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `title` | N/A | The title for the compared images item.  |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="4. before image / 5. after image" %}}

```yaml {hl_lines=[18,19]}
# landing.yaml
imageCompare:
    ...
    items:
        - title: Dark Mode
          ...
          imagePath: "images/screenshots"
          imageBefore: "lotusdocs_dark_v0.8.webp"
          imageAfter: "lotusdocs_light_v0.8.webp"
    ...
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `imagePath` | N/A | Set the path to the directory containing the image assets you wish to compare.  |
| `imageBefore` | N/A | Set filename of the *before* image. |
| `imageAfter` | N/A | Set filename of the *after* image. |
{{</ table >}}

{{% /tab %}}
{{< /tabs >}}

### Configuration Options

Options for the each `image compare` are nested in the `config` array. Visit the [image compare viewer website](https://image-compare-viewer.netlify.app) to learn more about these options.

```yaml {hl_lines=["6-16"]}
# landing.yaml
imageCompare:
    ...
    items:
        - title: Dark Mode
          config: {
              startingPoint: 50,
              addCircle: true,
              addCircleBlur: false,
              showLabels: true,
              labelOptions: {
                before: 'Dark',
                after: 'Light',
                onHover: false
              }
          }
          imagePath: "images/screenshots"
          imageBefore: "lotusdocs_dark_v0.8.webp"
          imageAfter: "lotusdocs_light_v0.8.webp"
    ...
```

## Image Text

The `image text` template consists of a 2 columns. One with and image and the other with a combination of a title, descriptive text, a list, and a call-to-action link. The image can be position either on the left or the right of the section.

![Lotus Docs Landing Page Image Text Section Diagram](https://res.cloudinary.com/lotuslabs/image/upload/bo_1px_solid_rgb:c4c4c4,r_8/v1700490661/Lotus%20Docs/images/lotusdocs_image_text_template_diag_v1.0_sjor4e.webp)
{.text-center}

{{< tabs tabTotal="4">}}
{{% tab tabName="1. title / 2. subtitle" %}}

```yaml
# landing.yaml
imageText:
    ...
    title: Customise The Lotus Docs Appearance # 1
    subtitle: Much of Lotus Docs' appearance can be customised. Dark mode is optional (enabled by default) and you can choose a Google font that suites you via the config parameters. #2
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `title` | N/A | The main title of the `image text` template (**h4** sized font).  |
| `subtitle` | N/A | Subheading text. Supports Markdown. |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="3. list" %}}

```yaml
# landing.yaml
imageText:
    ...
    list:
    - text: Blazing fast page loads
      icon: speed

    - text: Sensible default SEO friendly settings
      icon: area_chart

    - text: Designed to be accessible
      icon: accessibility
    ...
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `list.text` | N/A | The title for the list item.  |
| `list.icon` | N/A | The [Material Symbol](https://fonts.google.com/icons?icon.style=Outlined) icon to use for the list item.  |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="4. cta link" %}}

```yaml
# landing.yaml
imageText:
    ...
    ctaButton:
        text: Learn more
        url: "/docs/"
    ...
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `ctaButton.text` | N/A | Set the text for the call-to-action button/link.  |
| `ctaButton.url` | N/A | Set the URL for the call-to-action button/link. |
{{</ table >}}

{{% /tab %}}
{{% tab tabName="5. image" %}}

```yaml
# landing.yaml
imageText:
    ...
    image:
        path: "images/templates/single"
        filename: "google_lighthouse_circle_v1.0.svg"
        alt: "Google LightHouse 100% Illustration" # Optional but recommended

    imgOrder:
        desktop: 2
        mobile: 1
    ...
```

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `image.path` | N/A | Set the path to image asset.  |
| `image.filename` | N/A | Set the filename of the image. |
| `image.alt` | N/A | Set the alt text for the image. |
| `imgOrder.desktop` | N/A | Set the column order for the image on desktops. `1` will place the image before the text column. `2` will place it after. |
| `imgOrder.mobile` | N/A | Set the order for the image on mobiles. `1` will place the image above the text column. `2` will place it underneath.  |
{{</ table >}}

{{% /tab %}}
{{< /tabs >}}