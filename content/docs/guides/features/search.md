---
weight: 214
title: "Search"
description: "Lotus Docs site search options."
icon: search
date: 2023-06-20T15:30:15+00:00
lastmod: 2023-06-20T15:30:15+00:00
draft: true
images: []
---

## FlexSearch

The FlexSearch Static Search plugin provides the smoothest, fastest and easiest search possible for your Lotus Docs site. Static Search provides instant, dynamic results for any search terms, and comes equipped with a wealth of options and settings to fine-tune the functionality to perfectly meet the needs of your site visitors.

### Enabling FlexSearch

**FlexSearch is enabled by default** in Lotus Docs. To disable it, simply set the `flexSearch` parameter (located under `[params.docs]`) in the `hugo.toml` configuration file to `false`. That's it!

```toml
[params.docs]
    # Search
    flexSearch      = false # default is true
```

### How to search your site using FlexSearch

With FlexSearch enabled you should now see a search button [**1.**] in the top navigation bar:

![Lotus Docs - FlexSearch Screenshot](https://res.cloudinary.com/lotuslabs/image/upload/v1688185913/Lotus%20Docs/images/lotus_docs_flexsearch_ui_components_diagram_v1.0_zfkkg3.png)

Click on the search button (or use `ctrl` + `/`) to reveal and activate the search input bar `(2)`. Just start typing a search query and the result `[3]` will appear automatically just below the search bar.

## DocSearch