---
weight: 230
title: "Tables & Tabs"
icon: table_chart
description: "How to use Lotus Docs tables & tabs shortcodes to render great looking markdown tables and tabs"
lead: "Using Hugo shortcodes to render tables and tabs."
date: 2022-11-05T04:41:15+00:00
lastmod: 2022-11-05T04:41:15+00:00
draft: true
images: []
toc: true
---

## Regular Tables

| Tables   |      Are      |  Cool |
|----------|:-------------:|------:|
| col 1 is |  left-aligned | $1600 |
| col 2 is |    centered   |   $12 |
| col 3 is | right-aligned |    $1 |

## Shortcode Table

{{< table "table table-borderless table-responsive table-xs" >}}
| Animal | Sounds | Legs |
|---------|--------|-----|
| `Cat` | Meow | 4 |
| `Dog` | Woof | 4 |
| `Cricket` | Chirp | 6 |
{{</ table >}}

### Stripe Example

{{< table "table table-responsive table-striped" >}}
| Flow | Description |
|---------|--------|
| `STPSourceFlowRedirect` | Your customer must be redirected to the [payment method’s](#) website or app to confirm the charge. See the section below for more information. |
| `STPSourceFlowReceiver` | Your customer must push funds to the account information provided in the Source object. See the documentation for the specific [payment method](#) you are using for more information. |
| `STPSourceFlowVerification` | Your customer must verify ownership of their account by providing a code that you post to the Stripe API for authentication. See the documentation for the specific [payment method](#) you are using for more information. |
{{</ table >}}