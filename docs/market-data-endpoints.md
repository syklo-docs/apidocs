---
layout: default
title: Market data endpoints
nav_order: 3
---

# Market data endpoints
{: .no_toc }

Just the Docs has some specific configuration parameters that can be defined in your Jekyll site's \_config.yml file.
{: .fs-6 .fw-300 }

## Functions
{: .no_toc .text-delta }

1. TOC
{:toc}

---

View this site's [\_config.yml](https://github.com/just-the-docs/just-the-docs/tree/main/_config.yml) file as an example.

## List all assets

`GET /analytics/apiv1/allassets`

Response

```js
[
   {
      "asset":"ARS",
      "name":"Argentine Peso",
      "methods":[
         "ARS:AR:null:Money Gram",
         "ARS:AR:null:Uala Cash",
         "ARS:AR:null:Bank",
         "ARS:AR:null:Mercado Pago",
         "ARS:AR:null:Uala Transfer",
         "ARS:AR:null:Lemon Cash"
      ]
   },
   {
      "asset":"AUD",
      "name":"Australian Dollar",
      "methods":[
         null
      ]
   }
]
```

## Tickers

`GET /analytics/apiv1/ticker`

Response

```js
// "prices":[last_price, bid_price, ask_price]
[
   {
      "symbol":"USDC_ARS",
      "method":"ARS:AR:null:Bank",
      "last_timestamp":1674867900877,
      "prices":[
         364.2,
         364.2,
         363.8
      ]
   },
   {
      "symbol":"USDC_VES",
      "method":"VES:VE:null:Banesco",
      "last_timestamp":1674865378539,
      "prices":[
         23.005,
         23.005,
         23.6
      ]
   }
]
```