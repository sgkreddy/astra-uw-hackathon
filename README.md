# ASTRA × Unusual Whales

Submission for the **Unusual Whales Hackathon** (Oct 2026).

ASTRA is my personal trading desk. It pulls options flow, dealer positioning and big-trade data from the Unusual Whales API and shows it next to the chart and the order ticket, so you don't have to switch tabs before a trade.

## Demo

[▶ Watch the demo (astra-uw-demo.mp4)](https://github.com/sgkreddy/astra-uw-hackathon/blob/main/astra-uw-demo.mp4)

(2.5 min, 1920×912)

## What the UW API drives

| Feature | Where it shows | UW data used |
|---|---|---|
| **Flow summary**: net call vs put premium plus a bullish/bearish read | Chart header and ticket | Options flow per ticker |
| **Dealer positioning**: long/short gamma, above or below the call or put wall | Chart header and ticket | Greek exposure (GEX) by strike |
| **Call wall / put wall / gamma flip lines** drawn on the price chart | Chart LEVELS tab | Greek exposure by strike |
| **Big trades tape**: the largest recent prints for the ticker (expiry, strike, premium, ask/bid side, sweep) | Under the chart | Flow alerts per ticker |
| **IV rank and next earnings** | Chart header and ticket | Volatility stats, earnings calendar |
| **Flow filters**: filter the alert queue by flow source | Queue panel | Flow alerts |

## How it fits a trade

1. A flow alert lands in the queue.
2. Clicking it loads the chart with the UW levels drawn (walls, gamma flip) and the big-trades tape.
3. The ticket shows a one-line UW context string, e.g. *"MRVL flow bullish · IV rank 22 · earnings 12-01 · long gamma, below the put wall"*, before you choose **Take / Caution / Pass**.

## Stack

- Unusual Whales REST API (Bearer auth, `api.unusualwhales.com`)
- TradingView Lightweight Charts for the price and level overlay
- Broker integrations for order routing (not part of this submission)

The trading app's source code is private. This repo holds the demo and the integration write-up.
