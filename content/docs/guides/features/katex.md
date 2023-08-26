---
weight: 530
title: "Katex"
description: "Fast Tex math rendering for your Lotus Docs site"
icon: "function"
date: "2023-08-26T20:43:23+01:00"
lastmod: "2023-08-26T20:43:23+01:00"
draft: false
toc: true
katex: true
---

$$
f\relax{x} = \int_{-\infty}^\infty
    \hat f\(\xi)\ e^{2 \pi i \xi x}
    \ d\xi
$$

<!-- $$
\begin{equation*}
   n \sim  10^{18} \mathrm{cm^{-3}} \left(\frac{100\mathrm{km}}{R}\right)^2 \left(\frac{10\mathrm{MeV}}{\langle E \rangle}\right).
\end{equation*}
$$ -->

<!-- $$
\int \frac{1}{x} dx = \ln \left| x \right| + C
$$ -->

## How to use Katex with Lotus Docs

[Katex](https://katex.org/) support is controlled by the `katex` parameter in your [front matter](https://gohugo.io/content-management/front-matter/) (**line 10 below**). Setting it to `true` enables Katex support only for pages that require it.

{{< prism lang="yaml" line="10" >}}
---
weight: 530
title: "Katex"
description: "Fast Tex math rendering for your Lotus Docs site"
icon: "function"
date: "2023-08-26T20:43:23+01:00"
lastmod: "2023-08-26T20:43:23+01:00"
draft: true
toc: true
katex: true
---
{{< /prism >}}

## Writing LaTex in Markdown

Equations can be displayed either in block level or inline.

### Block display

Type an equation using double dollar signs as the delimiter:

```md
$$
\int \frac{1}{x} dx = \ln \left| x \right| + C
$$
```

$$
\int \frac{1}{x} dx = \ln \left| x \right| + C
$$

### Inline display

Type an equation using single dollar signs as the delimiter:

```md
$
\int \frac{1}{x} dx = \ln \left| x \right| + C
$
```

$
\int \frac{1}{x} dx = \ln \left| x \right| + C
$