---
title: "Migrating CMS settings after a major theme update"
slug: "vtex-io-documentation-migrating-cms-settings-after-major-update"
hidden: false
createdAt: "2020-09-22T20:44:01.218Z"
updatedAt: "2022-12-13T20:17:44.742Z"
---

You may need to perform a major update of your Store Theme app due to changes in its peer dependencies. However, transitioning to a new major version of the Store Theme could result in undesired consequences, such as losing the configured Admin page template settings.

To handle this situation and ensure a smooth migration, follow the steps below to migrate template settings.

## Before you begin

Ensure you have the following tools installed on your machine. They are responsible for facilitating the interactions with the VTEX platform and enhancing your development experience:

1. Install the [VTEX IO CLI](https://developers.vtex.com/docs/guides/vtex-io-documentation-vtex-io-cli-install).
2. Install GraphQL IDE by running the following command:

   ```bash
   vtex install vtex.admin-graphql-ide@3.x
   ```

## Instructions

1. Open the terminal and log in to your account.
2. Change to the [**production workspace**](https://developers.vtex.com/docs/guides/vtex-io-documentation-creating-a-production-workspace) containing your latest changes and [publish](https://developers.vtex.com/docs/guides/vtex-io-documentation-making-your-new-app-version-publicly-available#step-2---publishing-the-new-app-version) a new major version of your Store Theme app.
3. In the **production workspace**, install the Store Theme version published in the previous steps by running the following command:

   ```sh
   vtex install {appVendor}.{appName}@{appVersion}
   ```

4. Open the VTEX Admin of the production workspace used in the previous steps and go to the **GraphQL Admin IDE**:

   ```sh
   vtex browse admin/graphql-ide
   ```

5. From the **Choose an app** dropdown list, select `vtex.pages-graphql@2.x`.
6. Copy the code below and paste it into the GraphQL IDE.

   ```gql
    mutation{
      updateThemeIds(from:"{appVendor}.{appName}@{oldMajor}.x", to:"{appVendor}.{appName}@{newMajor}.x")
   }
   ```

   >⚠️ Replace only the values in curly brackets with those that apply to your scenario. You must keep the `x`, without replacing it with the minor and patch versions. If you do that, the mutation will not work.

7. Execute the code by clicking `Execute Query` (▶). 

   The expected response body is

   ```json
   {
     "data": {
       "updateThemeIds": true
     }
   }
   ```

8. Go to the **Storefront** module within VTEX Admin and validate the content in its features, such as **Site Editor**, **Pages** and **Redirects**.

9. Once you have validated your data in the **Storefront** module, [promote your workspace to master](https://developers.vtex.com/docs/guides/vtex-io-documentation-promoting-a-workspace-to-master/).
