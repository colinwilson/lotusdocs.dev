---
weight: 215
title: "DocSearch"
description: "DocSearch is a Server Side Search plugin."
icon: search
date: 2023-07-01T14:09:15+00:00
lastmod: 2023-07-01T14:09:15+00:00
draft: true
images: []
---

## What is DocSearch?

[DocSearch](https://docsearch.algolia.com/) is unique, free search specifically-designed for technical documentation for open-source projects or technical blogs. Providing fast, accurate search options, DocSearch empowers visitors to find the information they need as quickly as possible. With the DocSearch plugin, integrating search into your Publii site takes just a few moments.

## How does DocSearch work?

Much like other search engines, DocSearch uses a scraper to index your site content; in simple terms, the scraper reads through your website and stores the data, which it can then collate to make a custom search that is effective for your site. Uniquely, DocSearch is targeted to documentation specifically; this means it is designed to help users more effectively find answers to specific questions or subjects within a narrow scope rather than looking for more generalised relevance, and it also offers autocomplete functionality to help users locate the sections that will be more helpful in answering their query.

With the data collected, Algolia will automatically configure a search relevant to your site content, then provide methods to integrate the search into your site. The functionality for the search is handled by DocSearch itself; processing the search query and delivering results occurs separate from your site’s infrastructure.

## Why DocSearch?

DocSearch is designed purely to provide efficient, relevant documentation searches; this means that it will be more efficient and effective at answering specific queries and pointing you to relevant sections in the documentation, rather than the more general searches that Google or other search engines provide.

If you're running a website providing technical documentation on an open-source project, then DocSearch is the perfect choice as your search provider.

## DocSearch requirements

DocSearch's mission is to make finding relevant content in technical documentation easier, rather than to create a general search engine that any site can use. Therefore, in order to use DocSearch, each site must meet certain criteria.

### In order to use DocSearch, your website must meet these conditions:

1. Your website must be publicly available so that DocSearch can index it.
2. Your website must be a documentation site for an open-source project, or a technical blog. Algolia will reduce the scope of the data that they collect for searches to helpful pages only.
3. Your website is production-ready; that is, already contains content relevant and useful documentation. Algolia will not accept placeholder or lorem ipsum websites that are intended to be updated later.

## How to get started?

Once your website is online and ready to add search functionality, you should [submit it to DocSearch](https://docsearch.algolia.com/apply/) on their frontpage; the form in the header of the site will allow you to do this. You will only need provide the website URL and your email address so that you can receive the search credentials once they are ready; note that you will also need to be the owner of the website in question and confirm this when submitting your application. Once Algolia accept your submission they will send you the credentials for enabling your search via email.

After receiving the confirmation email, you will need to copy the following data in order to add it into the plugin options:

- Application ID
- Search API Key
- Index Name

Once the plugin has been enabled and the relevant data added, DocSearch will crawl your website every 24 hours to ensure your search is up-to-date.

The DocSearch team recommend that your site includes a sitemap as this will allow it to better track changes, and it has the added benefit of being considered best practice for SEO. By default Publii generates a full sitemap for you, but if you would like to check that it is enabled or want to exclude content from the sitemap you can do so in the **Settings → Advanced options → Sitemap** section of the Publii interface.

## Enabling the Search Section

All official Publii themes have a search area built-into the theme, which will need to be enabled before the plugin will be able to function. To enable the search section:

1. In the Publii main menu in the left-sidebar, click on the **Theme Settings** option to open the settings screen.
2. In the second section of this screen, **Custom Settings**, click on the **Search** tab in the list of options under the custom settings title to open the search options.
3. Click on the switcher button next to the **Search** option to enable the search bar.
4. The area is now enabled in your theme, and you can move on to enabling and configuring the DocSearch plugin.

## Enabling the Plugin

To activate the plugin, open the **Tools & Plugins** section of the Publii app via the left-menu to see a list of installed plugins. Click on the switcher button in the bottom-left of the **DocSearch** box in this list to enable the plugin.

Once both the plugin and search area in the theme have been enabled, we will need to add the **Application ID**, **Search API Key**, and **Index Name** that were provided by DocSearch via email after the submitted site was approved, to the plugin settings.

To open the plugin settings, click on the **DocSearch** box once again, anywhere except on the switcher button, and the settings screen will open. Note that this screen will not be available if the plugin is not enabled first.

## DocSearch Options

As the hard work in crawling your site and creating the search is handled by DocSearch themselves, there are only three options in the plugin, all of which need to be configured before the plugin can function correctly. Make sure that you have the email with your search credentials that DocSearch provided after accepting your site submission to hand so that the relevant information can be added to the plugin options. The settings in the plugin are as follows:

### Search Configuration

- **Application ID** - Enter the application ID provided by DocSearch in this field.
- **API Key** - Enter the API Key provided by DocSearch in this field.
- **Index Name** - Enter the Index Name provided by DocSearch in this field.

Once done, save the changes by clicking on the **Save Settings** button at the bottom of the options screen; the plugin will now be ready to use.