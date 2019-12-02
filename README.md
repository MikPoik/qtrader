# qTrader
Welcome to the qTrade trading bot.

### What does this bot offer?
This bot places buy and sell orders for you at the best possible price, and at the best possible exposure.

### What is the premise?
Market spread is an inefficiency, which can be exploited by covering both sides of it while the difference is higher than market fees. Nothing new.

### How do I run this bot?
On start, you will be asked for your API credentials. You need to obtain these from [https://qtrade.io/settings/api_keys](https://qtrade.io/settings/api_keys)
There is a configuration file `config.json` where you set your trading parameters.

### Config File
Bot configuration is set at `config.json` file.
Buy orders are placed on top of the buy order book, with an increase of `price_adjustment`.

Sell orders are placed on top of the sell order book, with a decrease of `price_adjustment`.

The minimum spread between orders is defined by `spread_pct_min`.

Order book recalculation is set by `ttl` in seconds. However, pauses between runs are set at 90 seconds static.

### What returns can I expect?

The bot profits the most from a stable price range with a high spread. It works actively towards lowering the spread in order to beat other trading bots and humans.

### What should I be aware of?

This bot does **not** track individual order performance, because that would require static orders. Static orders are not favorable due to their inert nature, which results in them getting stuck forever outside the price range.

A very strong trend where there is only one type of trading going on (buys / sells only), this bot cannot operate properly. However, such situation should only be temporary.

### Tips

In an uptrend scenario, it might be a good idea to have a higher `sell_amount` than `buy_amount` in magnitude strong enough to knock down the price back to your buy orders.
The opposite is true for a downtrend.

### Requirements
`python-dateutil`

`pip3 install --upgrade --user git+https://github.com/qtrade-exchange/qtrade-py-client.git`

### Configuration example
```
[
  {
    "name": "BIS",
    "sell_amount": "150",
    "min_sell_price": "0.00001400",
    "buy_amount": "150",
    "max_buy_price": "0.00002000",
    "ttl": "120",
    "spread_pct_min": "1",
    "price_adjustment": "0.00000001",
    "max_stash": "5000",
    "min_stash": "500"
  },
  {
    "name": "NYZO",
    "sell_amount": "150",
    "min_sell_price": "0.00002000",
    "buy_amount": "150",
    "max_buy_price": "0.00002000",
    "ttl": "120",
    "spread_pct_min": "1",
    "price_adjustment": "0.00000001",
    "max_stash": "10000",
    "min_stash": "1000"
  },
  {
    "name": "VEO",
    "sell_amount": "0.15",
    "min_sell_price": "0.005",
    "buy_amount": "0.1",
    "max_buy_price": "0.15",
    "ttl": "120",
    "spread_pct_min": "1",
    "price_adjustment": "0.00000001",
    "max_stash": "10",
    "min_stash": "0.1"
  },
    {
    "name": "ARO",
    "sell_amount": "1500",
    "min_sell_price": "0.0000001",
    "buy_amount": "1500",
    "max_buy_price": "0.00000015",
    "ttl": "120",
    "spread_pct_min": "1",
    "price_adjustment": "0.00000000",
    "max_stash": "20000",
    "min_stash": "10000"
  }
]
```
![alt text](thumb.png "Thumbnail")