Member API v2
=============
Member API is API which can be used by client application like SPA.

**Version:** 0.0.1

**License:** https://github.com/rubykube/peatio/blob/master/LICENSE.md

### /v2/markets
---
##### ***GET***
**Summary:** Get all available markets.

**Description:** Get all available markets.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get all available markets. |

### /v2/tickers
---
##### ***GET***
**Summary:** Get ticker of all markets.

**Description:** Get ticker of all markets.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get ticker of all markets. |

### /v2/tickers/{market}
---
##### ***GET***
**Summary:** Get ticker of specific market.

**Description:** Get ticker of specific market.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | path | [object Object] | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get ticker of specific market. |

### /v2/members/me
---
##### ***GET***
**Summary:** Get your profile and accounts info.

**Description:** Get your profile and accounts info.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get your profile and accounts info. |

### /v2/deposits
---
##### ***GET***
**Summary:** Get your deposits history.

**Description:** Get your deposits history.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | [object Object] | No | string |
| limit | query | Set result limit. | No | integer |
| state | query |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get your deposits history. |

### /v2/deposit
---
##### ***GET***
**Summary:** Get details of specific deposit.

**Description:** Get details of specific deposit.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| txid | query |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get details of specific deposit. |

### /v2/deposit_address
---
##### ***GET***
**Summary:** Where to deposit. The address field could be empty when a new address is generating (e.g. for bitcoin), you should try again later in that case.

**Description:** Where to deposit. The address field could be empty when a new address is generating (e.g. for bitcoin), you should try again later in that case.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | [object Object] | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Where to deposit. The address field could be empty when a new address is generating (e.g. for bitcoin), you should try again later in that case. |

### /v2/orders
---
##### ***GET***
**Summary:** Get your orders, results is paginated.

**Description:** Get your orders, results is paginated.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query | [object Object] | Yes | string |
| state | query | Filter order by state, default to 'wait' (active orders). | No | string |
| limit | query | Limit the number of returned orders, default to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| order_by | query | If set, returned orders will be sorted in specific order, default to 'asc'. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get your orders, results is paginated. |

##### ***POST***
**Summary:** Create a Sell/Buy order.

**Description:** Create a Sell/Buy order.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | formData | [object Object] | Yes | string |
| side | formData | [object Object] | Yes | string |
| volume | formData | [object Object] | Yes | string |
| price | formData | [object Object] | No | string |
| ord_type | formData | [object Object] | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Create a Sell/Buy order. |

### /v2/orders/multi
---
##### ***POST***
**Summary:** Create multiple sell/buy orders.

**Description:** Create multiple sell/buy orders.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | formData | [object Object] | Yes | string |
| orders[side] | formData | [object Object] | Yes | [ string ] |
| orders[volume] | formData | [object Object] | Yes | [ string ] |
| orders[price] | formData | [object Object] | No | [ string ] |
| orders[ord_type] | formData | [object Object] | No | [ string ] |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Create multiple sell/buy orders. |

### /v2/orders/clear
---
##### ***POST***
**Summary:** Cancel all my orders.

**Description:** Cancel all my orders.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| side | formData | If present, only sell orders (asks) or buy orders (bids) will be canncelled. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Cancel all my orders. |

### /v2/order
---
##### ***GET***
**Summary:** Get information of specified order.

**Description:** Get information of specified order.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query | [object Object] | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get information of specified order. |

### /v2/order/delete
---
##### ***POST***
**Summary:** Cancel an order.

**Description:** Cancel an order.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| id | formData | [object Object] | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Cancel an order. |

### /v2/order_book
---
##### ***GET***
**Summary:** Get the order book of specified market.

**Description:** Get the order book of specified market.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query | [object Object] | Yes | string |
| asks_limit | query | Limit the number of returned sell orders. Default to 20. | No | integer |
| bids_limit | query | Limit the number of returned buy orders. Default to 20. | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get the order book of specified market. |

### /v2/depth
---
##### ***GET***
**Summary:** Get depth or specified market. Both asks and bids are sorted from highest price to lowest.

**Description:** Get depth or specified market. Both asks and bids are sorted from highest price to lowest.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query | [object Object] | Yes | string |
| limit | query | Limit the number of returned price levels. Default to 300. | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get depth or specified market. Both asks and bids are sorted from highest price to lowest. |

### /v2/trades
---
##### ***GET***
**Summary:** Get recent trades on market, each trade is included only once. Trades are sorted in reverse creation order.

**Description:** Get recent trades on market, each trade is included only once. Trades are sorted in reverse creation order.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query | [object Object] | Yes | string |
| limit | query | Limit the number of returned trades. Default to 50. | No | integer |
| timestamp | query | An integer represents the seconds elapsed since Unix epoch. If set, only trades executed before the time will be returned. | No | integer |
| from | query | Trade id. If set, only trades created after the trade will be returned. | No | integer |
| to | query | Trade id. If set, only trades created before the trade will be returned. | No | integer |
| order_by | query | If set, returned trades will be sorted in specific order, default to 'desc'. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get recent trades on market, each trade is included only once. Trades are sorted in reverse creation order. |

### /v2/trades/my
---
##### ***GET***
**Summary:** Get your executed trades. Trades are sorted in reverse creation order.

**Description:** Get your executed trades. Trades are sorted in reverse creation order.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query | [object Object] | Yes | string |
| limit | query | Limit the number of returned trades. Default to 50. | No | integer |
| timestamp | query | An integer represents the seconds elapsed since Unix epoch. If set, only trades executed before the time will be returned. | No | integer |
| from | query | Trade id. If set, only trades created after the trade will be returned. | No | integer |
| to | query | Trade id. If set, only trades created before the trade will be returned. | No | integer |
| order_by | query | If set, returned trades will be sorted in specific order, default to 'desc'. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get your executed trades. Trades are sorted in reverse creation order. |

### /v2/k
---
##### ***GET***
**Summary:** Get OHLC(k line) of specific market.

**Description:** Get OHLC(k line) of specific market.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query | [object Object] | Yes | string |
| limit | query | Limit the number of returned data points, default to 30. | No | integer |
| period | query | Time period of K line, default to 1. You can choose between 1, 5, 15, 30, 60, 120, 240, 360, 720, 1440, 4320, 10080 | No | integer |
| timestamp | query | An integer represents the seconds elapsed since Unix epoch. If set, only k-line data after that time will be returned. | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get OHLC(k line) of specific market. |

### /v2/k_with_pending_trades
---
##### ***GET***
**Summary:** Get K data with pending trades, which are the trades not included in K data yet, because there's delay between trade generated and processed by K data generator.

**Description:** Get K data with pending trades, which are the trades not included in K data yet, because there's delay between trade generated and processed by K data generator.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query | [object Object] | Yes | string |
| trade_id | query | The trade id of the first trade you received. | Yes | integer |
| limit | query | Limit the number of returned data points, default to 30. | No | integer |
| period | query | Time period of K line, default to 1. You can choose between 1, 5, 15, 30, 60, 120, 240, 360, 720, 1440, 4320, 10080 | No | integer |
| timestamp | query | An integer represents the seconds elapsed since Unix epoch. If set, only k-line data after that time will be returned. | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get K data with pending trades, which are the trades not included in K data yet, because there's delay between trade generated and processed by K data generator. |

### /v2/timestamp
---
##### ***GET***
**Summary:** Get server current time, in seconds since Unix epoch.

**Description:** Get server current time, in seconds since Unix epoch.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Get server current time, in seconds since Unix epoch. |

### /v2/withdraws
---
##### ***GET***
**Summary:** List your withdraws as paginated collection.

**Description:** List your withdraws as paginated collection.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | [object Object] | No | string |
| page | query | Page number (defaults to 1). | No | integer |
| limit | query | Number of withdraws per page (defaults to 100, maximum is 1000). | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | List your withdraws as paginated collection. |

##### ***POST***
**Summary:** [DEPRECATED] Create withdraw.

**Description:** [DEPRECATED] Create withdraw.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | formData | [object Object] | Yes | string |
| amount | formData | Withdraw amount without fees. | Yes | double |
| destination_id | formData | Stored withdraw destination ID. You should create withdraw destination before. | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | [DEPRECATED] Create withdraw. |

### /v2/withdraws/destinations
---
##### ***GET***
**Summary:** List your withdraw destinations as paginated collection.

**Description:** List your withdraw destinations as paginated collection.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | [object Object] | No | string |
| page | query | Page number (defaults to 1). | No | integer |
| limit | query | Number of withdraws per page (defaults to 100, maximum is 1000). | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | List your withdraw destinations as paginated collection. |

##### ***POST***
**Summary:** Create withdraw destination.

**Description:** Create withdraw destination.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | formData | Currency code. Both upcase (BTC) and downcase (btc) are supported. | Yes | string |
| label | formData | The label associated with withdraw destination. | Yes | string |
| bank_name | formData | The bank name. | No | string |
| bank_branch_name | formData | The bank branch name. | No | string |
| bank_branch_address | formData | The place where the bank branch is located. | No | string |
| bank_identifier_code | formData | Financial institution's unique SWIFT/BIC code. | No | string |
| bank_account_number | formData | International or SWIFT bank account number. | No | string |
| bank_account_holder_name | formData | The name on your bank account. | No | string |
| address | formData | Wallet address in blockchain. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Create withdraw destination. |

### /v2/withdraws/destinations/{id}
---
##### ***DELETE***
**Summary:** Delete withdraw destination.

**Description:** Delete withdraw destination.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Delete withdraw destination. |

### /v2/sessions
---
##### ***DELETE***
**Summary:** Delete all user sessions.

**Description:** Delete all user sessions.

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Delete all user sessions. |

### /v2/solvency/liability_proofs/latest
---
##### ***GET***
**Summary:** Returns newest liability proof record for given currency.

**Description:** Returns newest liability proof record for given currency.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | The code of any currency with type 'coin'. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns newest liability proof record for given currency. |

### /v2/solvency/liability_proofs/partial_tree/mine
---
##### ***GET***
**Summary:** Returns newest partial tree record for member account of specified currency.

**Description:** Returns newest partial tree record for member account of specified currency.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | The code of any currency with type 'coin'. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns newest partial tree record for member account of specified currency. |
