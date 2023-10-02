---
weight: 1510
title: "GitHub Pages"
description: "How to deploy Lotus Docs on GitHub Pages"
icon: "filter_drama"
date: "2023-08-26T15:36:39+01:00"
lastmod: "2023-08-26T15:36:39+01:00"
draft: false
toc: true
---

## Overview

GitHub provides free and fast static hosting over SSL for personal, organization, or project pages directly from a GitHub repository via its [GitHub Pages](https://pages.github.com/) service and automating development workflows and build with [GitHub Actions](https://github.com/features/actions).

## Prerequisites

1. [A GitHub Account](https://github.com/signup)
2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. [Create a Hugo site using the Lotus Docs theme]({{% relref "quickstart#create-a-new-lotus-docs-site" %}})

## Procedure

Use the following steps to get your Lotus Docs site up and running on GitHub Pages.

1. Create a new repo on GitHub e.g. `https://github.com/colinwilson/colinwilson.github.io`

2. Visit your GitHub repository. From the main menu choose **Settings > Pages**. In then center of your screen you will see this:

    ![GitHub Pages settings 01](https://res.cloudinary.com/lotuslabs/image/upload/r_7/v1694797503/Lotus%20Docs/images/github_pages_settings_01_camkns.webp)
    {.text-center}

3. Change the Source to `GitHub Actions`. The change is immediate; you do not have to press a Save button.

    ![GitHub Pages settings 02](https://res.cloudinary.com/lotuslabs/image/upload/r_7/v1694797611/Lotus%20Docs/images/github_pages_settings_02_xseoyt.webp)
    {.text-center}

4. Follow the [quickstart]({{% relref "quickstart#create-a-new-lotus-docs-site" %}}) guide to create your new site locally.

    ```bash
    hugo new site colinwilson.github.io && cd colinwilson.github.io
    ```

5. Update your site's config file (`hugo.toml` / `hugo.yaml` / `hugo.json`) to include the required theme modules and update your `baseURL` to your intended GitHub Pages domain e.g. `colinwilson.github.io`. You can also configure a `[[menu.primary]]` item. This creates a link on the landing page to the `docs/` section.

    {{< tabs tabTotal="3">}}
    {{< tab tabName="hugo.toml" disabled="true" >}}
    {{< prism lang="toml" >}}

     baseURL = 'https://colinwilson.github.io'
    languageCode = 'en-us'
    title = 'My New Hugo Site'

    [module]
        [[module.imports]]
            path = "github.com/colinwilson/lotusdocs"
            disable = false
        [[module.imports]]
            path = "github.com/gohugoio/hugo-mod-bootstrap-scss/v5"
            disable = false

    [markup.goldmark.renderer]
        unsafe = true

    [[menu.primary]]
        name  = "Docs"
        url = "/docs/"
        identifier = "docs"
        weight = 10

    {{< /prism >}}
    {{< /tab >}}
    {{< tab tabName="hugo.yaml" >}}
    {{< prism lang="yaml" >}}

    baseURL: 'https://colinwilson.github.io'
    languageCode: en-us
    title: My New Hugo Site
    module:
      imports:
        - path: github.com/colinwilson/lotusdocs
          disable: false
        - path: github.com/gohugoio/hugo-mod-bootstrap-scss/v5
          disable: false
    markup:
      goldmark:
        renderer:
          unsafe: true
    menu:
      primary:
        - name: Docs
          url: /docs/
          identifier: docs
          weight: 10

    {{< /prism >}}
    {{< /tab >}}
    {{< tab tabName="hugo.json" >}}
    {{< prism lang="json" >}}

    {
      "baseURL": "https://colinwilson.github.io",
      "languageCode": "en-us",
      "title": "My New Hugo Site",
      "module": {
        "imports": [
          {
            "path": "github.com/colinwilson/lotusdocs",
            "disable": false
          },
          {
            "path": "github.com/gohugoio/hugo-mod-bootstrap-scss/v5",
            "disable": false
          }
        ]
      },
      "markup": {
        "goldmark": {
          "renderer": {
            "unsafe": true
          }
        }
      },
      "menu": {
        "primary": [
          {
            "name": "Docs",
            "url": "/docs/",
            "identifier": "docs",
            "weight": 10
          }
        ]
      }
    }

    {{< /prism >}}
    {{< /tab >}}
    {{< /tabs >}}

6. Create some example content.

    ```bash
     hugo new docs/example-page.md
    ```

    Update the front matter `draft` parameter in the created `example-page.md` file to `false`.

    ```yaml
     ---
    title: "Example Page"
    date: 2023-08-25T23:36:29+01:00
    draft: false
    ---
    ```
7. Create an empty `hugo.yaml` workflow file in your local repository.

    ```
    .github/workflows/hugo.yaml
    ```
8. Copy and paste the YAML below into the workflow file you created. Change the `branch` name and Hugo version as needed.

    ```yaml
    # Sample workflow for building and deploying a Hugo site to GitHub Pages
    name: Deploy Hugo site to Pages

    on:
    # Runs on pushes targeting the default branch
    push:
        branches:
        - main

    # Allows you to run this workflow manually from the Actions tab
    workflow_dispatch:

    # Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
    permissions:
    contents: read
    pages: write
    id-token: write

    # Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
    # However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
    concurrency:
    group: "pages"
    cancel-in-progress: false

    # Default to bash
    defaults:
    run:
        shell: bash

    jobs:
    # Build job
    build:
        runs-on: ubuntu-latest
        env:
        HUGO_VERSION: 0.118.2
        steps:
        - name: Install Hugo CLI
            run: |
            wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
            && sudo dpkg -i ${{ runner.temp }}/hugo.deb
        - name: Checkout
            uses: actions/checkout@v4
            with:
            submodules: recursive
            fetch-depth: 0
        - name: Setup Pages
            id: pages
            uses: actions/configure-pages@v3
        - name: Install Node.js dependencies
            run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
        - name: Build with Hugo
            env:
            # For maximum backward compatibility with Hugo modules
            HUGO_ENVIRONMENT: production
            HUGO_ENV: production
            run: |
            hugo \
                --gc \
                --minify \
                --baseURL "${{ steps.pages.outputs.base_url }}/"
        - name: Upload artifact
            uses: actions/upload-pages-artifact@v1
            with:
            path: ./public

    # Deployment job
    deploy:
        environment:
        name: github-pages
        url: ${{ steps.deployment.outputs.page_url }}
        runs-on: ubuntu-latest
        needs: build
        steps:
        - name: Deploy to GitHub Pages
            id: deployment
            uses: actions/deploy-pages@v2
    ```

9. Commit all the changes to your local repository with a commit message of something like “New site & workflow”, and push your local repo to the repository you created on GitHub in `step 1`.

10. From GitHub’s main menu, choose Actions. You will see something like this:

    ![GitHub Pages settings 03](https://res.cloudinary.com/lotuslabs/image/upload/r_7/v1694798306/Lotus%20Docs/images/github_pages_settings_03_x0zvvd.webp)
    {.text-center}

11. When GitHub has finished building and deploying your site, the color of the status indicator will change to green.

    ![GitHub Pages settings 04](https://res.cloudinary.com/lotuslabs/image/upload/r_7/v1694798414/Lotus%20Docs/images/github_pages_settings_04_wosrsa.webp)
    {.text-center}

12. Click on the commit message as shown above. You will see this:

    ![GitHub Pages settings 05](https://res.cloudinary.com/lotuslabs/image/upload/r_7/v1694798537/Lotus%20Docs/images/github_pages_settings_05_sfpvpf.webp)
    {.text-center}

    Under the deploy step, you will see a link to your live site 🎉.

    In the future, whenever you push a change from your local repository, GitHub will rebuild your site and deploy the changes.