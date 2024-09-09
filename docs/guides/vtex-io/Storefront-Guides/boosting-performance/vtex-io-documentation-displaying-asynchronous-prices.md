---
title: "Displaying asynchronous prices"
slug: "vtex-io-documentation-displaying-asynchronous-prices"
hidden: false
createdAt: "2020-11-23T13:33:26.379Z"
updatedAt: "2022-12-13T20:17:45.051Z"
---

Although useful to enhance user experience, displaying the most up-to-date prices comes at the heavy cost of increasing your store's page response time.

This is due to the fact that fetching the newest prices in your store database relies on making a new request to the server every time a product is rendered on the interface.

A favorable way out is to set your store to fetch product prices on the client-side, promoting a decrease of response time in your pages in order to display the *asynchronous prices*.

> ℹ️ **Asynchronous prices do not mean outdated**. They are product prices stored in the browser cache according to the user navigation. If your store does not routinely update product prices, it is strongly recommended to display asynchronous prices instead.

![priceasync](https://cdn.jsdelivr.net/gh/vtexdocs/dev-portal-content@main/images/vtex-io-documentation-displaying-asynchronous-prices-0.gif)

Learn below how to set your store up to decrease page response time with asynchronous prices!

## Instructions

1. Ensure that your store is not fetching the price data on the server-side by setting the `simulationBehavior` prop (from the [Search Result](https://developers.vtex.com/docs/guides/vtex-search-result/) app) to `skip`:

```diff
"store.search": {
  "blocks": [
    "search-result-layout"
  ],
  "props": {
    "context": {
+     "simulationBehavior": "skip"
    }
  }
},
```

2. Ensure that the [Product Summary](https://developers.vtex.com/docs/guides/vtex-product-summary/) and the [Product Price](https://developers.vtex.com/docs/guides/vtex-product-price/) apps are listed as dependencies in your theme's `manifest.json` file:

```json
"dependencies": {
  "vtex.product-summary": "2.x",
  "vtex.product-price": "1.x"
}  
```

3. Add the `priceBehavior` prop to your [`product-summary.shelf`](https://developers.vtex.com/docs/guides/vtex-product-summary-productsummaryshelf) block and set its value to `async`:

```diff
"product-summary.shelf": {
  "props": {
+   "priceBehavior": "async"
  },
  "children": [
    // other children
    "product-list-price#summary",
    "flex-layout.row#selling-price-savings",
    "product-installments#summary",
    "add-to-cart-button",
  ]
}
```

4. Wrap the all price blocks under the `product-price-suspense` block (from the [Product Prices app](https://developers.vtex.com/docs/guides/vtex-product-price/)):

```diff
{
  "product-summary.shelf": {
    "props": {
     "priceBehavior": "async"
    },
    "children": [
      // other children
-     "product-list-price#summary",
-     "flex-layout.row#selling-price-savings",
-     "product-installments#summary",
-     "add-to-cart-button",
+     "product-price-suspense"
   ]
  },
+ "product-price-suspense": {
+   "children": [
+     "product-list-price#summary",
+     "flex-layout.row#selling-price-savings",
+     "product-installments#summary",
+     "add-to-cart-button"
+   ]
+ }
}
```
