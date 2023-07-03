---
weight: 305
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

## Google Fonts

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `google_fonts` | N/A | An array of Google fonts and sizes to load. e.g.<br>`google_fonts = [["Poppins", "300, 400, 600, 700"],["Source Code Pro", "500, 700"]]`<br> This will load the Google [Poppins](https://fonts.google.com/specimen/Poppins) and [Source Code Pro](https://fonts.google.com/specimen/Source+Code+Pro) fonts in the specified sizes. |
| `sans_serif_font` | System Font | Set the Sans Serif font. e.g. `"Poppins"` |
| `secondary_font` | System Font | Set the Secondary font. e.g. `"Poppins"` |
| `mono_font` | System Font | Set the Mono font. e.g. `"Source Code Pro"` |
{{</ table >}}

## Footer

{{< table "table table-striped" >}}
| Parameter | Default Value | Description |
|---------|--------|------|
| `copyright` | N/A | Sets the copyright text inside the docs footer section (supports Markdown) |
{{</ table >}}