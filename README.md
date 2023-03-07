# Dev-portal-content

Welcome to the [VTEX Developer Portal](https://developers.vtex.com) content repository! Here you will find the files for all guides included in that documentation portal. It is managed by the [Tech Writing team at VTEX](https://github.com/vtexdocs/dev-portal-content/graphs/contributors), with lots of love, sweat and PRs.

We're so glad you're here! It means you care about sharing knowledge through documentation ❤️ 📝. So come along, get comfy and learn how to [contribute with documentation](#contributing-with-developer-portal-documentation), [manage content](#managing-content) and [fix errors](#fixing-errors) in this repository.

## Why have we changed platforms from [ReadMe](https://readme.com/) to our custom built Developer Portal?

- Faster navigation.
- More control over the search.
- Create an interface completely controlled by us.
- Managing content in GitHub.
- High efficiency: we saved a considerable amount of our monthly budget.

## Developer Portal repositories

We have created a new organization in GitHub to host our documentation: [vtexdocs](https://github.com/vtexdocs).

You can find all repositories included in it in [vtex/education-tools](https://github.com/vtex/education-tools#education-teams-repositories).

They each serve a different purpose, and will be mentioned in the FAQ below, depending on which action you wish to perform.

### In this repository

You will find the following folders in this repository:

- **.github**: stores workflows configured for this repository.
- **docs**: stores the markdown files of all our docs. They are categorized into:
  - **guides**: API guides.
  - **release-notes**: release notes included in our [changelog](https://developers.vtex.com/updates/release-notes).
  - **vtex-io**: all VTEX IO guides.
- **docs-utils**: scripts used to import documentation from ReadMe.
- **images**: stores images imported from ReadMe.
- **readme-api-md**: stores API Reference's markdown imported from Readme.
- **.gitignore**: stores files that should be ignored by GitHub.

## Contributing with Developer Portal documentation

We're so glad you're here! Thanks for being interested.

### How can I add new articles or release notes?

1. Open a branch in the [dev-portal-content](https://github.com/vtexdocs/dev-portal-content) repository.
2. Add a new file in the [desired folder](#in-this-repository), following our [template](https://github.com/vtexdocs/dev-portal-content/blob/main/docs/guide_template.md).
3. Complete the [frontmatter](#what-information-goes-in-the-frontmatter).
   > The `excerpt` field is mandatory for release notes.
4. Add your content in markdown.
5. Add images in the chosen guide's folder, if you wish.
6. To determine the left navigation's order, follow [these instructions](#what-determines-the-left-navigations-order-and-organization).
7. Submit your PR for review.

*The [dev-portal-content](https://github.com/vtexdocs/dev-portal-content) repository just stores our documentation, it is not automatically synched to be rendered in the Dev Portal - yet. For now, when a new content is added to it, it is just included in the desired folder. For it to appear in the Developer Portal, our Tech Writing team leaders must run the portal's build.*

>⚠️ Note that we have a limitation of PRs by hour, so we have to accumulate the day's PRs to be all approved and merged by our Tech Writing team leaders. This means that if you want your content to be published, you should submit your PR for review with at least 2 days in advance from the desired publication date!

### What information goes in the frontmatter?

The frontmatter is the table with metadata about the article you're adding. It contains the following fields:

- **title:** article's title, which should match the slug.
- **slug:** slug to the article's link, which should match the title.
- **excerpt:** brief description of release notes and guides, like a synopsis or TLDR.
  - *Release notes:* it is rendered as a synopsis of the release notes, readable when the user clicks on the ▶️ collapsible button next to the release's title, in our [changelog UI](https://developers.vtex.com/updates/release-notes). This field is mandatory for release notes! Character limit: 400.
  - *Guides*: it is rendered as the greyed-out sentence at the bottom of the title, with a brief TLDR for that article. Character limit: 120.
- **hidden:** boolean that makes the article not discoverable by search engines and our internal search if `true`. Know more in [How can I hide articles from search engines](#how-can-i-hide-articles-from-search-engines).
- **createdAt:** creation date, automatically filled in.
- **updatedAt:** update date, automatically filled in.
- **seeAlso:** adds articles in the `See also` section, at the footer of the content. Should be filled in when there's a recommended reading sequence for the articles you are managing. It should be filled with the slug of the chosen article. Example `seeAlso: - "/docs/guides/vtex-io-documentation-2-prerequesites"`
- **hidePaginationPrevious**: boolean that hides in the article's footer a hyperlink to the previous article listed on the navigation. Mark as `true` to  hide the link to the previous doc on the navigation.
- **hidePaginationNext**: boolean that hides in the article's footer a hyperlink to the next article listed on the navigation. Mark as `true` to  hide the link to the following doc on the navigation.

### How can I make sure my content will be visible and rendered correctly?

- Make sure you have a unique slug.
- Make sure your slug is the exact copy of your title.
- Images must be saved in the repository. To add it to your markdown, see [How to add images to articles](#how-can-i-addfix-images-in-an-article).
- Ask team leaders to run the portal's build.

### How can I deal with page slugs?

The slugs used in our previous version of Developer Portal were mostly maintained. You shouldn't have to worry about previous slugs.

- **New guide:** an article's title will become the page's slug always. *Do not create a slug that is different than the title, the portal will not interpret it otherwise.*
- **API Reference:** the URL structure of the Developer Portal API reference has the endpoint's path as part of it. It includes `/api-reference/{category in API Reference}#{operation}-{endpoint's path}`.

> For the content to be rendered properly, it is mandatory that slugs are unique, so no article should have a repeated title. Learn how to fill in titles in [frontmatter](#what-information-goes-in-the-frontmatter).

### What determines the left navigation's order and organization?

The [dev-portal-content](https://github.com/vtexdocs/dev-portal-content) repository just stores our documentation, it is not automatically synched to be rendered in the Developer Portal - yet. For now, when a new content is added to it, it is just included in the desired folder.

For it to appear in the Developer Portal in the order that you choose for the left navigation, you need to create a pull request in the [devportal](https://github.com/vtexdocs/devportal/) repository.

The portal's navigation comes from the navigation [file](https://github.com/vtexdocs/devportal/blob/main/public/navigation.json). It is a json object listing the navigation and hierarchy of all contents in Developer Portal.

The excerpt below represents the first articles of the Guides section, for instance.

```jsx
{
        "documentation": "API Guides",
        "slugPrefix": "docs/guides/",
        "categories": [
        {
            "name": "Getting Started",
            "slug": "getting-started-category",
            "origin": "",
            "type": "category",
            "children": [
            {
                "name": "Introduction",
                "slug": "getting-started",
                "origin": "",
                "type": "markdown",
                "children": [
                {
                    "name": "Platform overview",
                    "slug": "getting-started-platform-overview",
                    "origin": "",
                    "type": "markdown",
                    "children": []
                },
                {
                    "name": "List of REST APIs",
                    "slug": "getting-started-list-of-rest-apis",
                    "origin": "",
                    "type": "markdown",
                    "children": []
                },
                {
                    "name": "Authentication",
                    "slug": "getting-started-authentication",
                    "origin": "",
                    "type": "markdown",
                    "children": []
                },
                {
                    "name": "Making your first request",
                    "slug": "getting-started-making-your-first-request",
                    "origin": "",
                    "type": "markdown",
                    "children": []
                }
                ]
            },
            {
                "name": "Catalog",
                "slug": "catalog-overview",
                "origin": "",
                "type": "markdown",
                "children": []
            },
            {
                "name": "Orders",
                "slug": "orders-overview",
                "origin": "",
                "type": "markdown",
                "children": []
            },
            ...
            ]
        },
...
```

To add new content in the left navigation:

1. Open a branch in the [/devportal](https://github.com/vtexdocs/devportal) repository.

    > ⚠️ **Before you start adding commits, read the repository's [readme](http://readme.md) file!** Commits must be done in a certain format for your PR to be approved.

2. In the [navigation.json](https://github.com/vtexdocs/devportal/blob/main/public/navigation.json) file, locate where you want the new content to appear. (Yes, it is a long document, be patient!)
3. Copy the structure below, and replace the values for your desired content.

```jsx
    {
        "name": "Checking which user is currently authenticated",
        "slug": "checking-which-user-is-currently-authenticated",
        "origin": "",
        "type": "markdown",
        "children": []
    }
```

4. Paste the object in the desired spot.
5. Open a PR.

> By opening a PR, a bot will present a preview for you to test the navigation. With each commit, the preview will be updated.

6. Test your navigation through the preview.
7. Send the PR link in the `#dev-portal-pr` Slack channel for approval.

### How to update the left navigation after changing an endpoint's path?

The URL structure of the Developer Portal API reference has the endpoint's path as part of it. For example, the [List shipping policies](https://developers.vtex.com/docs/api-reference/logistics-api#get-/api/logistics/pvt/shipping-policies) endpoint's URL is `https://developers.vtex.com/docs/api-reference/logistics-api#get-/api/logistics/pvt/shipping-policies`, and the endpoints path is `/api/logistics/pvt/shipping-policies`.

Therefore, once you change the endpoint's path, the corresponding URL in the Developer Portal will change as well, and it will be necessary to update the left navigation.

>❗ Currently, it is not possible to create redirects from an endpoint URL to its updated version. If necessary, update the links in the most strategic documentations related to that endpoint, to decrease 404 errors.

To update the left navigation after changing an endpoint's path follow the steps below:

1. Open a branch in the [/devportal](https://github.com/vtexdocs/devportal) repository.
    >⚠️ Before you start adding commits, read the repository's readme file. Commits must be done in a certain format for your PR to be approved.
2. In the [navigation.json](https://github.com/vtexdocs/devportal/blob/main/public/navigation.json) file, locate the old endpoint slug and replace it with the new slug in the `endpoint` field. For example:

    ```json
    {
        "name": "Update shipping policy",
        "slug": "logistics-api",
        "type": "openapi",
        "method": "PUT",
        "origin": "",
        "endpoint": "/api/logistics/pvt/shipping-policies/-id-",
        "children": []
    }
    ```

3. Open a PR.
4. Send the PR in `#dev-portal-pr` Slack channel for approval.
5. After approval, merge the PR.

### How can I add different colored callouts?

We recommend using a simple markdown syntax to add callouts:

```jsx
>ℹ️ Information type callout
```

```jsx
>⚠️ Warning type callout
```

```jsx
>❗ Danger type callout
```

The following complex syntax is also supported:

```jsx
[block:callout]
{
    "type": "info",
    "body": "Check the new [Payments onboarding guide](https://developers.vtex.com/vtex-rest-api/docs/payments-overview). We created this guide to improve the onboarding experience for developers at VTEX. It assembles all documentation on our Developer Portal about Payments and is organized by focusing on the developer's journey.",
    "title": "Onboarding guide"
}
[/block]
```

```jsx
[block:callout]
{
    "type": "warning",
    "body": "Check the new [Payments onboarding guide](https://developers.vtex.com/vtex-rest-api/docs/payments-overview). We created this guide to improve the onboarding experience for developers at VTEX. It assembles all documentation on our Developer Portal about Payments and is organized by focusing on the developer's journey.",
    "title": "Onboarding guide"
}
[/block]
```

```jsx
[block:callout]
{
    "type": "danger",
    "body": "Check the new [Payments onboarding guide](https://developers.vtex.com/vtex-rest-api/docs/payments-overview). We created this guide to improve the onboarding experience for developers at VTEX. It assembles all documentation on our Developer Portal about Payments and is organized by focusing on the developer's journey.",
    "title": "Onboarding guide"
}
[/block]
```

### How can I add/fix images in an article?

1. Access the [dev-portal-content/docs/guides](https://github.com/vtexdocs/dev-portal-content/tree/main/docs/guides) folder.
2. Upload the images you wish to include in your guide in the same folder your article is located.
3. Access the file in GitHub web.
4. Open the raw version of the uploaded file by opening the image in a new tab.
5. Save the URL.
6. Mention the URL in your markdown.

>ℹ️ This repository uses [JSDELIVR](https://www.jsdelivr.com) as a CDN for adding images with files stored in GitHub. Thus, you can also use the image CDN URL instead of going through steps 3 to 5. To do this, format your image URL like so: `https://cdn.jsdelivr.net/gh/vtexdocs/dev-portal-content@{branch}/{path}/{imgFileName}`. For instance, the CDN URL for [this image](https://github.com/vtexdocs/dev-portal-content/blob/main/docs/guides/Getting-Started/getting-started/making-your-first-request-1.png) is `https://cdn.jsdelivr.net/gh/vtexdocs/dev-portal-content@main/docs/guides/Getting-Started/getting-started/making-your-first-request-1.png`.

Note that we have configured an action that converts images to this CDN automatically, so both methods can be used.

### How can I hide articles from search engines?

When you publish an article in Developer Portal and wish that only those with the link can access it, you can hide it from search engines. This is useful for products in Beta that need documentation for specific clients, instead of publicly available docs, for example.

To do so, when creating the article fill in the header with the value `hidden: true`. You can keep the article out of the navigation bar by not making any changes in `navigation.json`.

```jsx
---
title: "Orders v2"
slug: "orders-getting-started"
hidden: true
createdAt: "2022-09-27T20:34:46.354Z"
updatedAt: "2022-10-04T14:36:08.692Z"
---
```

>️ Be aware that this will hide your article not only in Developer Portal searches, but also in other sites, like Google.

## Managing content

### How can I create a redirect?

1. Open a branch in the [/devportal](https://github.com/vtexdocs/devportal) repository.
    >⚠️ Before you start adding commits, read the repository's readme file. Commits must be done in a certain format for your PR to be approved.
2. In line 37 of the [next.config.js](https://github.com/vtexdocs/devportal/blob/07519dab0c357cb107342cf21bc86ae107cce603/next.config.js#L37) file, you will find an array of redirects. Add the one you want to create following this format, replacing `source` and `destination` with the desired slugs:
    ```javascript
        {
                source: '/vtex-rest-api/docs/:slug',
                destination: '/docs/guides/:slug',
                permanent: true,
        },
    ```
    Make sure you add specific redirects before more global redirects, otherwise they will have no effect. For now, hashlinks (`#`) are not supported in the source slug.
3. Open a PR. Netlify will generate a preview link for you to test the redirect.
4. Send the PR in `#dev-portal-pr` Slack channel for approval.
5. After approval, merge the PR.

### API Reference: what about the [openapi-schemas](https://github.com/vtex/openapi-schemas) repository?

All API Reference is still documented and managed through our usual repository, [openapi-schemas](https://github.com/vtex/openapi-schemas). Nothing's changed here. There is a 5 minute cache between merged PRs in the [openapi-schemas](https://github.com/vtex/openapi-schemas) and the Developer Portal, but it should be rendered automatically.

### How can I update docs from IO apps that already have a readme file in the app's repository?

All docs should be included in the dev-portal-content repository. If their readme.md file is not yet included, create a new file, and copy and paste the text.

## Fixing errors

### How to fix the error type `Error: There are incorrectly formatted code blocks in this file` in #dev-portal-logs?

This error means that there is a <code>`</code> loose somewhere in the document. The system reads it as an inline code block.

### How can I fix the error type in `#dev-portal-logs`?

This error should already be fixed. Check the log's age to see if it is still valid.

### 404 errors

#### What causes 404 errors?

- Broken callouts
- Broken images
- Missing closing tags in HTML
- Links mentioned in other articles containing previous Dev Portal slugs, or mentions to headings
- Redirects not made from older URLs
- Content does not exist in /dev-portal-content, only on Readme

#### 404 automatic checker in files

We have embedded a GitHub action called [check-links.yml](https://github.com/vtexdocs/dev-portal-content/blob/main/.github/workflows/check-links.yml) to review all URLs mentioned in a file and check if they return 404 errors. If there's a link experiencing the 404 error in your file, you must fix it so the branch can be merged.

Broken links will appear in red in your code editor tool (VSCode), and you can learn more about it by clicking on `Details`.
