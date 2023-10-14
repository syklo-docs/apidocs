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