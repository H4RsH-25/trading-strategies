### Gold Larp-cator — README

Source: 

---

#### Overview

A **multi-layer confluence indicator** combining:

* Mean reversion (SMA zone)
* Trend strength (EMA slope)
* Momentum (MACD + SAR)
* Structure (session highs/lows, VWAP, BB, Gann)
* Trade management (trail exits)

Built for **Gold intraday (5M NY)** with stricter filtering than the previous version.

---

#### Core Components

**1. Trend Filter**

* `EMA 150 slope` → must be strong (`> 0.8`)
* Removes sideways conditions

**2. Entry Zone**

* ±$1.5 around SMA
* No “first-touch only” restriction → more signals

**3. MACD Confirmation**

* Uses **crossovers (not just >0)**

  * Bullish → histogram crosses above 0
  * Bearish → crosses below 0

**4. SAR Logic**

* Detects **trend flips**
* Used as entry trigger + exit condition

---

#### Signal Logic

**Primary Buy (buy_v2)**

* Above EMA200
* Not overheated (BIAS filter)
* SAR flip up OR golden cross
* No resistance pressure (MA60/120 nearby)
* Positive EMA slope + strong trend

**Primary Sell (sell_v2)**

* SAR flip down OR
* Price breaks trailing stop OR
* Falls below SMA context

---

#### Trade Management

**Trailing Stops**

* Conservative → 5% pullback
* Wide → 8% pullback
* Based on highest price after entry

**State Tracking**

* Tracks if “in trade”
* Updates highest price dynamically

---

#### Additional Layers

**Bollinger Bands (20,2)**

* Volatility + expansion zones

**Gann Levels (25/50/75%)**

* Derived from 50-bar range
* Acts as structure levels

**VWAP**

* Institutional mean

**Session Levels (NY)**

* Current + previous highs/lows

**BIAS Filter**

* Prevents entries when price too far above MA200

---

#### Visuals

* White → SMA
* Orange → EMA
* Yellow → zone + Gann
* Purple → Bollinger
* Teal → VWAP
* Green/Red → session levels
* SAR dots → trend direction
* Buy/Sell markers → entries/exits
* Orange background → overheated market

---

#### Alerts

* Same base alerts as previous system
* Additional visual triggers:

  * `buy_v2`
  * `sell_v2`

---

#### Intended Use

* **Intraday gold (5M NY session)**
* Designed for:

  * Pullback entries in trend
  * Continuation trades
* Requires:

  * Structure reading
  * Liquidity awareness
  * Discipline on weak signals

---

#### Key Difference vs Previous Version

* Adds **trend strength filter**
* Uses **MACD cross instead of static bias**
* Introduces **full trade lifecycle (entry → trail → exit)**
* Includes **multi-confluence environment (VWAP, BB, Gann, sessions)**

---

#### Notes

* More signals ≠ better trades → rely on filters
* Strong trades = alignment of:

  * Trend
  * Momentum
  * Structure
* Weak signals should often be ignored unless context is clear
