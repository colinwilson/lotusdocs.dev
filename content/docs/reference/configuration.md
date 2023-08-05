---
weight: 705
title: "Configuration"
icon: settings
description: "Reference table of configuration options for the Lotus Docs theme."
lead: ""
date: 2023-01-21T16:16:15+00:00
lastmod: 2023-01-21T16:16:15+00:00
draft: false
images: []
toc: true
---

A list of available configuration settings in the site configuration file, `hugo.toml`, `hugo.yaml`, or `hugo.json`:

## `[params]`

### Google Fonts

{{< table "table table-striped" >}}
| Parameter | Type | Default Value | Description |
|---------|-----|--------|------|
| `google_fonts` | array | N/A | An array of Google fonts and sizes to load. e.g.<br>`google_fonts = [["Inter", "300, 400, 600, 700"],["Fira Code", "500, 700"]]`<br> This will load the Google [Inter](https://fonts.google.com/specimen/Inter) and [Fira Code](https://fonts.google.com/specimen/Fira+Code) fonts in the specified sizes. |
| `sans_serif_font` | string | System Font | Set the Sans Serif font. e.g. `"Inter"` |
| `secondary_font` | string | System Font | Set the Secondary font. e.g. `"Inter"` |
| `mono_font` | string | System Font | Set the Mono font. e.g. `"Fira Code"` |
{{</ table >}}

## `[params.footer]`

### Footer

{{< table "table table-striped" >}}
| Parameter | Type | Default Value | Description |
|---------|-----|-----|------|
| `copyright` | string | N/A | Sets the footer copyright text for both the landing page and `/docs` section (**supports Markdown**) |
| `version` | boolean | `false` | Display the site's `git` commit info in the footer? |
{{</ table >}}

## `[params.social]`

Social links are displayed as icons in the top left corner of the Lotus Docs theme. This goes for the landing page and docs site.

### Social Icon Links

{{< table "table table-striped" >}}
| Parameter | Type | Default Value | Description |
|---------|-----|-----|------|
| `github` | string | N/A | Enables the GitHub social icon link using the GitHub URL value set here e.g. `colinwilson` or `colinwilson/lotusdocs` |
| `twitter` | string | N/A | Enables the Twitter (X - Ugh!) social icon link using the username value set here e.g. `lotusdocs` |
| `instagram` | string | N/A | Enables the Instagram social icon link using the username value set here e.g. `lotusdocs` |
| `rss` | boolean | `false` | Display an RSS icon link? |
{{</ table >}}

## `[params.docs]`

Options to help you configure Lotus Docs to suite your needs.

### Core Site Options

{{< table "table table-striped" >}}
| Parameter | Type | Default Value | Description |
|---------|-----|-----|------|
| `title` | string | N/A | Set the default HTML title for your documentation pages/sections e.g. `Lotus Docs` (This parameter is separate from the root Hugo [`title`](https://gohugo.io/getting-started/configuration/#title) parameter that sets the title for your site overall e.g the landing page.) |
| `pathName` | string | `docs` | Pathname for the documentation site. A few additional changes to the Lotus Docs theme are required when this value is updated. See the **Installation** guide for more details. |
| `themeColor` | string | `blue` | Set the sites accent color. This affects links, buttons and icons. Available options/colors include, `blue` (default), `green`, `red`, `yellow`, `emerald`, `cardinal`, `magenta`, `cyan`. |
| `darkMode` | boolean | `false` | Enable Dark Mode for the site? |
| `prism` | boolean | `true` | Enable the PrismJS syntax highlighting plugin? See the [Syntax Highlighting](../../guides/features/syntax-highlighting/#prism-features) and [Prism Shortcode](../../guides/shortcodes/prism/) guides for more details. |
{{</ table >}}

### GitInfo Options

{{< table "table table-striped" >}}
| Parameter | Type | Default Value | Description |
|---------|-----|-----|------|
| `ghrepo` | string | N/A | Set the Git repository URL for your site e.g. `github.com/colinwilson/lotusdocs.dev` |
| `editPage` | boolean | `false` | Enable '**Edit this page**' link at the bottom of documentation pages? Links to the Git repository set by the `ghrepo` parameter. |
| `lastMod` | boolean | `false` | Enable '**Last updated**' date at the bottom of documentation pages? |
| `lastModRelative` | boolean | `true` | Format the `lastMod` (if enabled) date parameter as relative? e.g. 8 hours ago, 2 months ago |
{{</ table >}}

### Table of Contents

{{< table "table table-striped" >}}
| Parameter | Type | Default Value | Description |
|---------|-----|-----|------|
| `toc` | boolean | `true` | Enable a Table of Contents for all documentation pages? (Activates only if a documentation page generates a ToC). |
| `tocMobile` | boolean | `true` | Enable a Table of Contents menu in mobile view? Helps navigate pages with a lot of headings/sections. |
| `scrollSpy` | boolean | `true` | Enable [scrollSpy](https://getbootstrap.com/docs/5.3/components/scrollspy/) on the Table of Contents menus? |
{{</ table >}}