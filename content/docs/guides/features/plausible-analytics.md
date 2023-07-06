---
weight: 515
title: "Plausible Analytics"
description: "How to add Plausible Analytics to your Lotus Docs site."
icon: trending_up
date: 2022-12-29T16:28:15+00:00
lastmod: 2023-07-05T23:45:15+00:00
draft: true
images: []
---

[Plausible Analytics](https://plausible.io) is a simple, open source, lightweight (< 1 KB) and privacy-friendly alternative to Google Analytics. Plausible is completely independent, self-funded and bootstrapped. Read more about them [here](https://plausible.io/about).

![Plausible Analytics Dashboard Screenshot](https://res.cloudinary.com/lotuslabs/image/upload/v1673015990/Lotus%20Docs/Social%20Media/plausible-analytics-screenshot_ds_rdd_c6bi3o.webp)

## Why use Plausible Analytics?

Plausible is an open source, privacy-first Google Analytics alternative. So what are the benefits of this?

- **Privacy by design** - Plausible, by design complies with [strict privacy policies](https://plausible.io/data-policy). Including: GDPR, CCPA, and PECR.
- **You own your data** - Plausible does **not** sell or share your data, or abuse your visitor's privacy. When using Plausible Analytics, you 100% own and control all of your website data. Your data is not being shared with or sold to any third-parties.
- **No personal data collected** - Plausible does not track and collect any personal data or personally identifiable information.
- **Open Source** - Plausible Analytics is completely open source so anyone can view, review and inspect the code they're running to verify whether their actions match their claims of privacy.
- **Your data is encrypted** - Plausible minimize their data collection and whatever is tracked is kept **fully secured**, **encrypted** and hosted on servers **in the EU** (European Union) to ensure it's covered by strict laws on data privacy.

You can read more about Plausible Analytics and their polices [here](https://plausible.io/about).

## Create an Account on plausible.io

Before enabling Plausible Analytics in Lotus Docs, make sure to [register an account](https://plausible.io/docs/register-account) with them and add your site domain to your account; without an active account, no data can be collected by Plausible.

Make a note of the domain name that you entered when [adding your website to Plausible](https://plausible.io/docs/add-website), as this is required when enabling Plausible Analytics in Lotus Docs.

## Enable Plausible Analytics

To enable Plausible Analytics, provide the following parameters in your configuration file under `[params.plausible]`:

- `dataDomain` - Enter the domain name that you will be tracking through Plausible Analytics, e.g. `lotusdocs.dev`; make sure it's the same domain you entered when adding your website to your Plausible account.
- `scriptURL` - Enter the URL that points to your self-hosted `script.js` file e.g. `mydomain.com`. By default or when empty it will always link to `plausible.io` ([https://plausible.io/js/script.js](https://plausible.io/js/script.js)).
- `eventAPI` - If you're [proxying Plausible](https://plausible.io/docs/proxy/introduction) requests via another service (e.g. [Vercel](https://plausible.io/docs/proxy/guides/vercel), [Netlify](https://plausible.io/docs/proxy/guides/netlify), [Cloudflare](https://plausible.io/docs/proxy/guides/cloudflare)), enter the appropriate event API path here.

{{< tabs tabTotal="3">}}
{{% tab tabName="hugo.toml" %}}

```toml
[params.plausible] # Parameters for Plausible Analytics
        dataDomain = "lotusdocs.dev"
        scriptURL  = "plausible.io"
        eventAPI   = "/docs/s"       # optional
```

{{% /tab %}}
{{% tab tabName="hugo.yaml" %}}

```yaml
params:
    plausible: # Parameters for Plausible Analytics
        dataDomain: "lotusdocs.dev"
        scriptURL: "plausible.io"
        eventAPI: "/docs/s"       # optional
```

{{% /tab %}}
{{% tab tabName="hugo.json" %}}

```json
{
   "params": {
        "plausible": {
            "dataDomain": "lotusdocs.dev",
            "scriptURL": "plausible.io",
            "eventAPI": "/docs/s"
        }
   }
}
```

{{% /tab %}}
{{< /tabs >}}

## Proxying Plausible through Vercel