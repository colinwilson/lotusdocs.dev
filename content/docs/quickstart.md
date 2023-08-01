+++
weight = 300
date = "2023-06-08T19:25:22+01:00"
draft = false
author = "Colin Wilson"
title = "Quickstart"
icon = "rocket_launch"
# featured_image = ""
description = "A guide to getting up and running with Lotus Docs."
publishdate = "2022-09-30T05:34:22+01:00"
tags = ["Beginners","Guide"]
categories = [""]

[twitter]
  card = "summary"
  site = "@LotusDocs"
  creator = "@LotusDocs"
  title = "Getting started"
  description = "Getting started with Lotus Docs."
  image = ""
+++

## Requirements

- **git**
- **Hugo** ≥ **v0.100.0** (Extended Version)

## Install Hugo

Install the [Hugo CLI](https://github.com/gohugoio/hugo/releases/latest), using the specific instructions for your operating system below:

{{< tabs tabTotal="4">}}
{{% tab tabName="Linux" %}}

Your Linux distro’s package manager may include Hugo. If this is the case, install it directly using your distro’s package manager – for instance, in Ubuntu, run the following command. This will install the extended edition of Hugo:

```shell
sudo apt install hugo
```

{{% /tab %}}
{{% tab tabName="Homebrew (macOS)" %}}

If you use the package manager [Homebrew](https://brew.sh/), run the `brew install` command in your terminal to install Hugo:

```shell
brew install hugo
```

{{% /tab %}}
{{% tab tabName="Windows (Chocolatey)" %}}

If you use the package manager [Chocolatey](https://chocolatey.org/), run the `choco install` command in your terminal to install Hugo:

```shell
choco install hugo --confirm
```

{{% /tab %}}
{{% tab tabName="Windows (Scoop)" %}}

If you use the package manager [Scoop](https://scoop.sh/), run the `scoop install` command in your terminal to install Hugo:

```shell
scoop install hugo
```

{{% /tab %}}
{{< /tabs >}}

### Manual Installation

The Hugo GitHub repository contains pre-built versions of the Hugo command-line tool for various operating systems, which can be found on the [Releases page](https://github.com/gohugoio/hugo/releases/latest)

For more instruction on installing these releases, refer to [Hugo’s documentation](https://gohugo.io/getting-started/installing/)

## Create a New Lotus Docs Site

With Hugo installed, the Lotus Docs theme can be installed using various methods:

- **Adding the theme as a Git submodule**
- **Adding the theme as a Hugo Module**
- **Cloning the theme files**

{{< tabs tabTotal="3">}}
{{% tab tabName="Add as a Git submodule" %}}

Create a new Hugo project using the `hugo new` command:

```shell
hugo new site my-docs-site && cd my-docs-site
```

Now initialize Git and clone the Lotus Docs theme repository as a submodule:

```shell
git init
git submodule add https://github.com/colinwilson/lotusdocs themes/lotusdocs
```

Initialize the Lotus Docs theme as a module:
```shell
hugo mod init theme/lotusdocs
```

Replace your existing `hugo.toml` config file with an example file:

```shell
curl -O https://raw.githubusercontent.com/colinwilson/lotusdocs/release/exampleSite/hugo.toml
```

{{% /tab %}}
{{% tab tabName="Add as a Hugo Module" %}}

```shell
TBD
```

{{% /tab %}}
{{% tab tabName="Clone theme files" %}}

```shell
TBD
```

{{% /tab %}}
{{< /tabs >}}

## Create New Content

Navigate to the root of your Hugo project and use the `hugo new` command to create a file in the `content/docs` directory:

```shell
hugo new docs/example-page.md
```

This will create a markdown file named `example-page.md` with the following default front matter:

```toml
+++
title = "Example Page"
description = ""
icon = "article"
date = "2023-05-22T00:27:57+01:00"
lastmod = "2023-05-22T00:27:57+01:00"
draft = false
toc = true
weight = 999
+++
```

Modify the options to suit your needs.

The code below shows the front matter code used to create this page, along with some markdown in the body:

```md
+++
weight = 100
date = "2023-05-03T22:37:22+01:00"
draft = true
author = "Colin Wilson"
title = "Quickstart"
icon = "rocket_launch"
toc = true
description = "A quickstart guide to creating new content in Lotus Docs"
publishdate = "2023-05-03T22:37:22+01:00"
tags = ["Beginners"]
+++

## Create New Content

Navigate to the root of your Hugo project and use the `hugo new` command to create a file in the `content/docs` directory:

    ```shell
    hugo new docs/examplepage.md
    ```
...
```

## Ordering Content

Lotus Docs uses a simple weighting method for ordering content and creating menus.

The front matter `weight` variable is used to order all content and auto-generate the menu structure (including the sidebar menu and page navigation buttons). Lower weight values take higher precedence. So content with lower weights come first and are so ordered in the menu.

## Auto-Generated Menu

As mentioned, Lotus Docs auto-generates menus and navigation links using the [front matter](https://gohugo.io/content-management/front-matter/#predefined) weight variable. For example, Navigate to the `content/docs` directory and create two content files, `doc-one.md` and `doc-two.md`, then edit the weight values to `100` and `200` respectively:

{{< alert text="It's good practice to increment the weight of your posts by a factor of <code>100</code>. This ensures plenty of room to insert new posts between existing items should you need to." />}}

Your directory structure should now look like this:

```treeview
content/
└── docs/
    ├── doc-one.md
    └── doc-two.md
```

Links to both posts are now visible in the sidebar menu where `doc-one.md` will come before and be placed above `doc-two.md`:

![sidebar menu items example](https://res.cloudinary.com/lotuslabs/image/upload/v1684719173/Lotus%20Docs/images/sidebar_menu_example_01-modified_qkb2si.png)

{{< alert context="info" text="The option to manually configure a predefined menu structure in <code>hugo.toml</code> as opposed to an auto-generated one is part of the Lotus Docs roadmap." />}}

## Second Level Menu Items

Second level menu items can be generated by first creating a **'parent'** directory containing an `_index.md` file, e.g.:

```shell
hugo new docs/parent-directory/_index.md
```

The above command creates an `_index.md` file inside a directory named `parent-directory` under `content/docs`:

```treeview
content/
└── docs/
    ├── parent-directory/
    │   └── _index.md
    ├── doc-one.md
    ├── doc-two.md
    └── _index.md
```

You can now create second level items inside the `parent-directory` as normal. Run the `hugo new` command again to create a post inside the newly created `parent-directory`:

```shell
hugo new docs/parent-directory/doc-three.md
```

Your directory/file structure should now look like this:

```treeview
content/
└── docs/
    ├── parent-directory/
    │   ├── _index.md
    │   └── doc-three.md
    ├── doc-one.md
    ├── doc-two.md
    └── _index.md
```

This is reflected in the sidebar menu with `parent-directory` functioning as a dropdown menu containing a link to the **Doc Three** post:

![sidebar parent menu example](https://res.cloudinary.com/lotuslabs/image/upload/v1684802032/Lotus%20Docs/images/sidebar_menu_example_02_jsecye.png)