### Cable Indicator 

#### Overview

A **multi-confluence forex indicator** built for **GBP/USD (cable)**.
Combines:

* Mean reversion (SMA zone)
* Volatility (Bollinger Bands, ATR)
* Trend (EMA + ATR direction)
* Structure (VWAP, session highs/lows, Gann)
* Momentum (MACD)

Designed for **tight spreads + small pip precision**.

---

#### Core Logic

**1. Moving Averages**

* `SMA 20` → mean reference
* `EMA 150` → macro trend

**2. Entry Zone**

* ±0.0007 around SMA
* Fires only when price re-enters after being away

---

#### Filters

**Bias Filter**

* Blocks trades when price is too far from EMA200
* Prevents chasing extended moves

**ATR Trend Filter**

* Uses dynamic trailing stop logic
* Only allows:

  * Long → ATR bullish
  * Short → ATR bearish

---

#### Momentum

**MACD (12/26/9)**

* Bullish → histogram > 0
* Bearish → histogram < 0

---

#### Signal Types

**Strong**

* Price in SMA zone
* MACD aligned
* ATR trend aligned
* Bias filter passed

**Weak**

* Same but **no MACD confirmation**

---

#### Trade Management

**ATR Trailing Stop**

* Dynamic support/resistance line
* Flips direction when trend changes
* Also acts as **trend filter + exit logic**

---

#### Structure Tools

**Bollinger Bands**

* Expansion / contraction zones

**Gann Levels (25/50/75%)**

* Derived from 50-bar range

**VWAP**

* Institutional mean

**Session Levels (NY)**

* Current session high/low
* Previous session reference

---

#### Visuals

* White → SMA
* Orange → EMA
* Yellow → SMA zone
* Aqua → Bollinger Bands
* Purple → Gann levels
* Teal → VWAP
* Lime/Gray → session levels
* Green/Red → ATR trail
* SAR-style dots → trend bias
* Red background → bias blocked

---

#### Alerts

* Confirmed Long
* Confirmed Short
* Weak Long
* Weak Short

---

#### RSI Note (Important)

You attempted to include RSI **inside same script with `overlay=false`**.

This causes:

* Entire indicator moves to separate pane
* Chart becomes unusable

**Correct approach:**

* Keep this script → `overlay=true`
* Create **separate RSI script** (same as previous fix)

---

#### Intended Use

* **GBP/USD intraday (5M–15M)**
* Focus:

  * Pullbacks to mean
  * Continuations with ATR trend
* Requires:

  * Clean structure reading
  * Avoiding overextended bias zones

---

#### Key Characteristics

* Much **tighter thresholds** than gold version
* More reliance on:

  * ATR direction
  * Bias control
* Better suited for:

  * Lower volatility pairs

---

#### Notes

* Over-filtering can reduce trades → intentional
* Best setups = alignment of:

  * SMA reaction
  * ATR trend
  * MACD
* Weak signals should be ignored unless strong structure present
