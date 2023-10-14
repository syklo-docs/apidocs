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
[
   {
      "method":"USDT:ALL:null:Arbitrum",
      "asset":"Tether (USDT)",
      "image":"https://bafybeihcpgisft47slhi7ztutu2kc55aafu3txphfbmzeyt35cc2fknnhi.ipfs.w3s.link/Arbitrum.png",
      "image2":"https://bafybeihcpgisft47slhi7ztutu2kc55aafu3txphfbmzeyt35cc2fknnhi.ipfs.dweb.link/Arbitrum.png"
   },
   {
      "method":"USDC:ALL:null:AVAX C-Chain",
      "asset":"USD Coin (USDC)",
      "image":"https://bafybeigpuxot6dcnwwv7u7hkee3cjrbcuf3ruqnpsilyaopucmc4pnzdje.ipfs.w3s.link/AVAX%20C-Chain.png",
      "image2":null
   }
]
```

## Ticker prices

`GET /analytics/apiv1/ticker`

Response

```js
// aggregates by symbol are presented first, with null methods
[
   {
      "symbol":"USDC_ARS",
      "method":null,
      "last_timestamp":1675048314681,
      "prices":[
         361.5,   // last price
         361.8,   // bid price
         368.9    // ask price
         ]
   },
   {
      "symbol":"USDC_ARS",
      "method":"ARS:🇦🇷:BN:Banco",
      "last_timestamp":1675048314681,
      "prices":[361,361,368.9]
   }
]
```

## 24hr ticker price change statistics

`GET /analytics/apiv1/ticker24h`

Response

```js
// aggregates by symbol are presented first, with null methods
[
   {
      "symbol":"USDC_COP",
      "method":null,
      "last_timestamp":"1675049087193",
      "stats":[
         4530,       // open
         4540,       // high
         4425,       // low
         4508,       // close
         294.29,     // base volume
         1306938.7,  // quote volume
         15,         // trades
         -0.0049     // price change percent
         ]
   },
   {
      "symbol":"USDC_COP",
      "method":"COP:🇨🇴:COBN7:Bancolombia",
      "last_timestamp":"1675036349730",
      "stats":[4530,4450,4430,4450,102,453500,2,-0.0177]
   },
   {
      "symbol":"USDC_COP",
      "method":"COP:🇨🇴:NEQ:Nequi",
      "last_timestamp":"1675049087193",
      "stats":[4426,4540,4425,4508,192.29,853438.7,13,0.0185]
   }
]
```

## Order book

`GET /analytics/apiv1/depth`

Response
```js
[
   {
      "symbol":"USDC_USD",
      "method":"USD:🌐:ADV:Advcash",
      "last_timestamp":1674899191286,
      "bids":[
         [
            578721,  // order id
            4260,    // user id
            0.98,    // price
            10.2,    // min amount
            2551.02  // max amount
         ]
      ],
      "asks":[
         [578727,4260,1.02,1,100],
         [599582,1619,1.015,1,50]
      ]
   },
   {
      "symbol":"USDC_VES",
      "method":"VES:🇻🇪:PF:Pago móvil",
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
// taker_base_amount: positive::taker_buy, negative::taker_sell
[
   {
      "symbol":"USDC_ARS",
      "method":"ARS:🇦🇷:BN:Banco",
      "trades":[
         [
            594633,        // transaction id
            1674828916625, // timestamp
            364,           // price
            5              // base amount (taker buy)
         ],
         [
            594782,        // transaction id
            1674829346205, // timestamp
            363.3,         // price
            -5             // base amount (taker sell)
         ]
      ]
   },
   {
      "symbol":"USDC_VES",
      "method":"VES:🇻🇪:PF:Pago móvil",
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
      "user_id":1619,
      "user_name":"cdhackers.BIAVGM",
      "wstats":[
         101,  // to accept
         97,   // accepted
         94,   // to disburse
         92,   // disbursed
         120,  // median time (seconds)
         0     // disputes lost
      ],
      "blocked_users":[null]
   },
   {
      "maker_id":4260,
      "user_name":"Paulito.QL6MCP",
      "wstats":[58,51,45,45,134,0],
      "blocked_users":[null]
   }
]
```