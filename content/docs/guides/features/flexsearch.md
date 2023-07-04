---
weight: 520
title: "FlexSearch"
description: "FlexSearch is a Static site Search plugin."
icon: search
date: 2023-06-20T15:30:15+00:00
lastmod: 2023-06-20T15:30:15+00:00
draft: true
images: []
---

## What is FlexSearch?

The FlexSearch Static Search plugin provides the smoothest, fastest and easiest search possible for your Lotus Docs site. Static Search provides instant, dynamic results for any search terms, and comes equipped with a wealth of options and settings to fine-tune the functionality to perfectly meet the needs of your site visitors.

## Enabling FlexSearch

**FlexSearch is enabled by default** in Lotus Docs. To disable it, simply set the `flexSearch` parameter (located under `[params.docs]`) in the `hugo.toml` configuration file to `false`. That's it!

```toml
[params.docs]
    # Search
    flexSearch      = false # default is true
```

## How to search your site using FlexSearch

With FlexSearch enabled you should see a search button in the top navigation bar:

![FlexSearch Screenshot | Lotus Docs](https://res.cloudinary.com/lotuslabs/image/upload/v1688442518/Lotus%20Docs/images/lotus_docs_flexsearch_ui_components_diagram_v1.1_jp2f0l.webp "FlexSearch components: **1.** Search Button **2.** Search Input Bar **3.** Search Result | Lotus Docs")

Click on the search button (or use `ctrl` + `/`) to reveal and activate the search input bar. Start typing a search query and the result(s) will automatically appear in a 'suggestions' panel underneath. Click a search result to navigate to said page.

## FlexSearch options