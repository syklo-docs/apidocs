---
layout: default
title: Change log
nav_order: 4
---

# Change Log

## 2023-10-14

Changes to Market Data Endpoint `GET /analytics/apiv1/makerstats`:
- The key `maker_id` has been renamed to `user_id`.
- A new field named `user_name` string, has been introduced.
- Within the `wstats` array, two additional values for `median time` and `disputes lost` have been included.

## 2024-01-12

Changes to Market Data Endpoint `GET /analytics/apiv1/trades`:
- Lookback was reduced from 1 day to 1 hour
- Field `trades` array now includes values for `maker_id`, `taker_id`, `status`, `taker quote amount`
- Value `price` removed from `trades` array  
- Field `trades` now includes transactions with various status, previously only `4: "buyer_confirmed2"`