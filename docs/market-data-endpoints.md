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
// aggregates by symbol are presented first, with null methods
// "prices":[last_price, bid_price, ask_price]
[
   {
      "symbol":"USDC_ARS",
      "method":null,
      "last_timestamp":1675048314681,
      "prices":[361.5,361.8,368.9]
   },
   {
      "symbol":"USDC_ARS",
      "method":"ARS:AR:null:Bank",
      "last_timestamp":1675048314681,
      "prices":[361,361,368.9]
   },
   {
      "symbol":"USDC_USD",
      "method":"USD:ALL:null:Mony",
      "last_timestamp":1675042255145,
      "prices":[1.018,null,1.018]
   }
]
```

## 24hr ticker price change statistics

`GET /analytics/apiv1/ticker24h`

Response

```js
// aggregates by symbol are presented first, with null methods
// "stats":[open, high, low, close, base_volume, quote_volume, trades, price_change_pct]
[
   {
      "symbol":"USDC_COP",
      "method":null,
      "last_timestamp":"1675049087193",
      "stats":[4530,4540,4425,4508,294.29,1306938.7,15,-0.0049]
   },
   {
      "symbol":"USDC_COP",
      "method":"COP:CO:null:Bancolombia",
      "last_timestamp":"1675036349730",
      "stats":[4530,4450,4430,4450,102,453500,2,-0.0177]
   },
   {
      "symbol":"USDC_COP",
      "method":"COP:CO:null:Nequi",
      "last_timestamp":"1675049087193",
      "stats":[4426,4540,4425,4508,192.29,853438.7,13,0.0185]
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