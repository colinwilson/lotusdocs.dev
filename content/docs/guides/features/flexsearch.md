---
weight: 214
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

1. search button
2. search input
3. query result

Click on the search button (or use `ctrl` + `/`) to reveal and activate the search input bar. Just start typing a search query and the result will appear automatically just below the search bar.

![Lotus Docs - FlexSearch Screenshot](https://res.cloudinary.com/lotuslabs/image/upload/v1688185913/Lotus%20Docs/images/lotus_docs_flexsearch_ui_components_diagram_v1.0_zfkkg3.png)
