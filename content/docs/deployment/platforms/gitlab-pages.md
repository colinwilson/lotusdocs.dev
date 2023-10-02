---
weight: 1515
title: "GitLab Pages"
description: "How to deploy Lotus Docs on GitLab Pages"
icon: "filter_drama"
date: "2023-08-26T15:36:47+01:00"
lastmod: "2023-08-26T15:36:47+01:00"
draft: false
toc: true
---

## Overview

With [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/), you can publish your Lotus Docs site directly from a repository in GitLab.

- Use for any personal or business website.
- Native support for Hugo.
- Create websites for your projects, groups, or user account.
- Host your site on your own GitLab instance or on GitLab.com for free.
- Connect your custom domains and TLS certificates.
- Attribute any license to your content.

GitLab makes it easy to build, deploy, and host your Lotus Docs website via their free GitLab Pages service.

## Prerequisites

1. [A GitLab Account](https://gitlab.com/users/sign_in)
2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. [Create a Hugo site using the Lotus Docs theme]({{% relref "quickstart#create-a-new-lotus-docs-site" %}})

## Procedure

Use the following steps to get your Lotus Docs site up and running on GitLab Pages.

1. Create a [new repo on GitLab](https://docs.gitlab.com/ee/user/project/index.html) e.g. `https://gitlab.com/colinwilson/colinwilson.gitlab.io`. Select `GitLab Pages` as the `Project deployment target`:

    ![](https://res.cloudinary.com/lotuslabs/image/upload/r_7/v1694886749/Lotus%20Docs/images/gitlab_create_new_repo_for_gitlab_pages_screenshot_t2sbwa.webp)

2. Create a new Hugo project using the `hugo new` command:

    ```bash
    hugo new site colinwilson.gitlab.io && cd colinwilson.gitlab.io
    ```

    Initialize your project as a Hugo Module using the hugo mod init command:

    ```
    hugo mod init my-docs-site
    ```

3. Update your site's config file (`hugo.toml` / `hugo.yaml` / `hugo.json`) to include the required theme modules and update your `baseURL` to your intended GitLab Pages domain e.g. `colinwilson.gitlab.io`. You can also configure a `[[menu.primary]]` item. This creates a link on the landing page to the `docs/` section.

    {{< alert context="info" text="Refer to the [quickstart guide]({{% relref `quickstart` %}}) if you wish install the Lotus Docs theme in a manner other than Hugo Modules (below)." />}}

    {{< tabs tabTotal="3">}}
    {{< tab tabName="hugo.toml" disabled="true" >}}
    {{< prism lang="toml" >}}

     baseURL = 'https://colinwilson.gitlab.io'
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

    baseURL: 'https://colinwilson.gitlab.io'
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
      "baseURL": "https://colinwilson.gitlab.io",
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

4. Create some example content.

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

5. Create an empty `.gitlab-ci.yml` file at the root of your local repository.

    ```
    /.gitlab-ci.aml
    ```
6. Copy and paste the YAML below into the job file you created.

    ```yaml
    image: registry.gitlab.com/pages/hugo/hugo_extended:0.118.2

    variables:
      HUGO_ENV: production

    default:
      tags:
        - docker
        - linux
      before_script:
        - apk add --no-cache go curl bash nodejs
        # - hugo mod get -u $THEME_URL
        ## Uncomment the following if you use PostCSS. See https://gohugo.io/hugo-pipes/postcss/
        #- npm install postcss postcss-cli autoprefixer

    test:
      tags:
        - docker
        - linux
      script:
        - hugo
      rules:
        - if: $CI_COMMIT_REF_NAME != $CI_DEFAULT_BRANCH

    pages:
      tags:
        - docker
        - linux
      script:
        - hugo
      artifacts:
        paths:
          - public
      rules:
        - if: $CI_COMMIT_REF_NAME == $CI_DEFAULT_BRANCH
    ```
7. Create a `.gitignore` file. Copy the contents below into it. This prevents your local `/public` directory (and other resources) being committed to to your GitLab repository.

    ```
    /public
    /assets/jsconfig.json
    resources/_gen/
    .hugo_build.lock
    ```
8. Your site structure should now look similar to the one below:

    ```treeview
    colinwilson.gitlab.io/
      ├── archetypes/
      ├── assets/
      ├── content/
      │   └── docs/
      │       └── example-page.md
      ├── data/
      ├── i18n/
      ├── layouts/
      ├── static/
      ├── themes/
      ├── .gitignore
      ├── .gitlab-ci.yml
      ├── .hugo_build.lock
      ├── go.mod
      ├── go.sum
      └── hugo.toml
    ```
9. Use `git int` to initialize your project as a repository, then commit all the changes to your local repository with a commit message of something like “🎉 initial commit”. Push your local repo to the repository you created on GitLab in `step 1`.

10. Revisit your repository on GitLab, navigate to **Build > Pipelines**, and you should see that your Hugo site was successfully built.

    ![GitLab pipelines screenshot](https://res.cloudinary.com/lotuslabs/image/upload/r_7/v1694885877/Lotus%20Docs/images/gitlab_pages_pipeline_01_engtdo.webp)
    {.text-center}

<!-- 11. On Gitlab, navigate to **Settings > General**, scroll down and expand the **Advanced** section. Scroll once more till you see the **Change path** section and change the path to match that of your repo.

    ![](https://res.cloudinary.com/lotuslabs/image/upload/v1694817677/Lotus%20Docs/images/gitlab_settings_change_path_u8vxvs.webp) -->

12. You should now be able to see your site at the `baseURL` (e.g. `https://colinwilson.gitlab.io`) defined in your `hugo.toml` / `hugo.yaml` / `hugo.json` config file