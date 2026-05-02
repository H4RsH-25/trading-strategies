### Gold Indicator — README

#### Overview

This script is a **price–mean reversion + confirmation tool** designed for trading gold on lower timeframes (e.g., 5M NY session).
It identifies when price returns to the **20 SMA zone** and filters entries using **MACD momentum**.

---

#### Core Logic

**1. Trend Context**

* `SMA 20` → short-term mean
* `EMA 150` → higher timeframe trend bias

**2. Entry Zone**

* A ±$2 range around the 20 SMA:

  * Upper: `SMA + 2`
  * Lower: `SMA - 2`
* Signal triggers **only on first entry into this zone**

**3. Momentum Confirmation (MACD 12/26/9)**

* Bullish → Histogram > 0
* Bearish → Histogram < 0

---

#### Signal Types

**Strong Signals (Preferred)**

* Long:

  * Price > SMA 20
  * MACD bullish
* Short:

  * Price < SMA 20
  * MACD bearish

**Weak Signals (Use discretion)**

* Price at SMA zone but **MACD not aligned**

---

#### Visuals

* White line → 20 SMA
* Orange line → 150 EMA
* Yellow band → ±$2 zone around SMA
* Green triangle → Confirmed long
* Red triangle → Confirmed short
* Yellow triangle → Weak signal

---

#### Alerts

Four alert types:

* Confirmed Long
* Confirmed Short
* Weak Long
* Weak Short

All alerts indicate:

* Price interaction with SMA zone
* MACD confirmation status

---

#### Intended Use

* Best for **intraday trading (Gold, 5M)**
* Works as a **reaction-based system**, not breakout
* Requires:

  * Market structure reading
  * Session awareness (NY preferred)
  * Trade grading before execution

---

#### Notes

* Signals are **context-dependent**, not standalone entries
* Weak signals should be filtered with:

  * Structure
  * Liquidity
  * Higher timeframe bias

---
