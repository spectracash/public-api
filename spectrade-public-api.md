# Spectrade Public API for Aggregators

This is the public API for [Spectrade Exchange](https://spectrade.io), designed to serve data to aggregators like CoinGecko, CoinMarketCap, and other crypto services.

> **Base URL:** `https://api.spectrade.io/api/public`

---

### `GET /coins`

Returns metadata of all supported coins.

**Response Example:**
```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "symbol": "BTC",
      "name": "Bitcoin",
      "description": null,
      "deposit": true,
      "withdraw": true,
      "deposit_fee": "0",
      "withdraw_fee": "0.0001",
      "minimum_deposit": "0.0002",
      "is_token": false,
      "token_network": [],
      "trading_fee": "0.1"
    },
    {
      "id": 2,
      "symbol": "SCL",
      "name": "Spectra Cash",
      "description": "Spectra Cash core focus is on building a robust investment portfolio that generates income to support liquidity and buyback, ensuring the long-term value of your assets. Our platform seamlessly integrates with popular e-commerce plugins like WHMCS and WooCommerce, making SCL the go-to payment currency for your online transactions",
      "deposit": true,
      "withdraw": true,
      "deposit_fee": "0",
      "withdraw_fee": "1",
      "minimum_deposit": "2",
      "is_token": false,
      "token_network": [],
      "trading_fee": "0.1"
    },
    {
      "id": 17,
      "symbol": "USDT",
      "name": "USD Tether",
      "description": "Tether tokens are the most widely adopted stablecoins, having pioneered the concept in the digital token space. A disruptor to the conventional financial system and a trailblazer in the digital use of traditional currencies, Tether tokens support and empower growing ventures and innovation throughout the blockchain space. Tether tokens exist as a digital token built on multiple blockchains.",
      "deposit": true,
      "withdraw": true,
      "deposit_fee": "0",
      "withdraw_fee": "0.5",
      "minimum_deposit": "1",
      "is_token": true,
      "token_network": [
        {
          "network": "polygon",
          "contract_address": "0xc2132d05d31c914a87c6611c10748aeb04b58e8f",
          "withdraw_fee": "0.50000000",
          "token_type": "POL20"
        }
      ],
      "trading_fee": "0.1"
    },
    ...
  ]
}
```

---

## 📌 Available Endpoints

### `GET /markets`

Returns a list of active trading markets.

**Response Example:**
```json
[
  {
    "pair": "USDT_NRC",
    "quote": "NRC",
    "price": "0.0009000000000007677",
    "change_24h": "5.29",
    "base_volume": "0.17981999",
    "quote_volume": "199.79998889",
    "lowest_ask": "0.0011",
    "highest_bid": "0.0009000000000007677"
    },
  ...
]
```

---

### `GET /orderbook/:pair`

Returns the current orderbook for the given market pair.

**Parameters:**
- `:pair` — in format `BASE_QUOTE` (e.g., `BTC_USDT`)

**Response Example:**
```json
{
  "success": true,
  "pair": "USDT_SCL",
  "timestamp": 1750603909524,
  "bids": [
    { "price": "0.0000001", "quote": "749.30000000", "base": "0.00007493" },
    { "price": "0.0000001", "quote": "10000000", "base": "1" }
  ],
  "asks": [
    { "price":"0.000299989999607273","quote":"23461.35730929","base":"7.03817257" },
    { "price":"0.000299999852756335","quote":"61.71403029","base":"0.01851420" }
  ]
}
```

---

### `GET /trades/:pair`

Returns recent trades for the given market pair.

**Parameters:**
- `:pair` — in format `BASE_QUOTE` (e.g., `BTC_USDT`)

**Response Example:**
```json
{
  "success" :true,
  "pair" :"USDT_SCL",
  "trades": [
    { "price": "0.000000010000000000", "base_volume": "0.000001000000000000", "quote_volume": "100.000000000000000000",  "trade_type": "buy", "datetime": "2025-06-21T03:09:24.000Z" },
    { "price": "0.000128510000000000", "base_volume": "0.010281000000000000", "quote_volume": "80.000000000000000000", "trade_type": "buy", "datetime": "2025-06-21T03:06:57.000Z" },
    ...
  ]
}
```

---

### `GET /stats`

Returns global statistics such as total volume and top pairs.

**Response Example:**
```json
{
  "success": true,
  "total_pairs": 105,
  "total_volume_usdt": "7.485973920000001000",
  "top_pairs": [
    { 
      "pair": "USDT_DDR",
      "base_volume": 5.48945712,
      "quote_volume": 30612.5788302,
      "percent_change": -99.5
    },
    { 
      "pair": "USDT_GTC",
      "base_volume": 0.47742039,
      "quote_volume": 68202.912858,
      "percent_change": 0
    },
    {
      "pair": "USDT_DOGE",
      "base_volume": 0.46544433,
      "quote_volume": 2.023671,
      "percent_change": 64.28
    }
  ],
  "updated_at":"2025-06-22T14:55:11.000Z"
}
```

---

## 💡 Notes

- All data is served in **JSON** format.
- Rate limits may apply in the future.
- This API is read-only and does not require authentication.

---
