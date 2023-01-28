---
layout: default
title: Market data endpoints
nav_order: 3
---

# Market data endpoints
{: .no_toc }



## Functions
{: .no_toc .text-delta }

1. TOC
{:toc}


---


## List of all assets and methods

`GET /analytics/apiv1/allassets`

Response

```js
// "methods":["currency:country:category:name"]
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

## Ticker prices

`GET /analytics/apiv1/ticker`

Response

```js
// "prices":[last_price, bid_price, ask_price]
[
   {
      "symbol":"USDC_ARS",
      "method":"ARS:AR:null:Bank",
      "last_timestamp":1674867900877,
      "prices":[364.2,364.2,363.8]
   },
   {
      "symbol":"USDC_ARS",
      "method":"ARS:AR:null:Mercado Pago",
      "last_timestamp":1674882195700,
      "prices":[354,364.2,354]
   }
]
```

## 24hr ticker price change statistics

`GET /analytics/apiv1/ticker24h`

Response

```js
// "stats":[open, high, low, close, base_volume, quote_volume, trades, price_change_pct]
[
   {
      "symbol":"USDC_ARS",
      "method":"ARS:AR:null:Bank",
      "last_timestamp":"1674867900877",
      "stats":[364.1,364.2,363.2,364.2,107,38940.2,9,0.0003]
   },
   {
      "symbol":"USDC_VES",
      "method":"VES:VE:null:Mobile payment",
      "last_timestamp":"1674879023734",
      "stats":[22.75,23.498,22.76,23.05,1781.81,41179.35152,123,0.0132]
   }
]
```

## Order book

`GET /analytics/apiv1/depth`

Response
```js
// "bids"||"asks":[order_id, maker_id, price, min_amount, max_amount]
[
   {
      "symbol":"USDC_USD",
      "method":"USD:ALL:null:Advcash",
      "last_timestamp":1674899191286,
      "bids":[
         [578721,4260,0.98,10.2,2551.02]
      ],
      "asks":[
         [578727,4260,1.02,1,100],
         [599582,1619,1.015,1,50]
      ]
   },
   {
      "symbol":"USDC_VES",
      "method":"VES:VE:null:Mobile payment",
      "last_timestamp":1674871135343,
      "bids":[
         [566270,3869,21.3,14.08,39.91],
         [598974,2260,22.55,1,305.1]
      ],
      "asks":null
   }
]
```

## Recent trades

`GET /analytics/apiv1/trades`

Response
```js
// "trades":[order_id, timestamp, price, taker_base_amount]
[
   {
      "symbol":"USDC_ARS",
      "method":"ARS:AR:null:Bank",
      "trades":[
         [594633,1674828916625,364,5],
         [594782,1674829346205,363.3,-5]
      ]
   },
   {
      "symbol":"USDC_VES",
      "method":"VES:VE:null:Mobile payment",
      "trades":[
         [597368,1674855446461,23.43,5],
         [597511,1674859147052,23,-6.3]
      ]
   }
]
```

## 7 day rolling maker statistics

`GET /analytics/apiv1/makerstats`

Response
```js
// "wstats":[to_accept, accepted, to_disburse, disbursed]
[  
   {
      "maker_id":1619,
      "wstats":[62,58,52,50]
   },
   {
      "maker_id":4260,
      "wstats":[7,6,6,6]
   },
   {
      "maker_id":2260,
      "wstats":[5,3,3,3]
   }
]
```