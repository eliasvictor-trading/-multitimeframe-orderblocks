# -multitimeframe-orderblocks
A multi‑timeframe checklist dashboard + ORB (Opening Range Break) breakout zones + VWAP “warn-only” markers + a Latest Order Blocks panel.

This repo is **connector‑agnostic**. Automated execution is configured in TradingView Alerts and your connector settings.

---

## What’s included

### MTF Checklist Dashboard (“Matrix”)
Configurable timeframe list (e.g., `1,5,15,30,60,240`) with per‑timeframe status for:
- Candle direction (current/previous)
- ORB position
- VWAP position
- EMA200 position
- Near current day high/low
- Near prior day high/low
- EMA9 vs EMA21
- EMA9&21 vs EMA200

### ORB (Opening Range Break)
- ORB computed using `ORB Minutes` timeframe.
- Robust session start detection:
  - Works with traditional sessions (recommended)
  - Also works with `0000-2359` via a new‑day fallback

### Breakout Zones (ORB-based)
- Long zone: `ORH + buffer` to `ORH + maxExtension`
- Short zone: `ORL - maxExtension` to `ORL - buffer`
- Optional “zone gate” to restrict breakout entries to these zones
- Compatibility plots: `BO_HIGH` and `BO_LOW`

### VWAP Warning (warn-only)
- Marks entries where price is extended from VWAP (does NOT block entries)

### Pullback Entries
- Pullback logic based on EMA9/EMA21 on the chart timeframe
- Optional pullback alignment checks:
  - VWAP
  - EMA200

### Latest Order Blocks Panel
- Displays latest bullish/bearish OB High/Avg/Low
- Panel position is independent from the dashboard
---

## Alerts (connector‑agnostic)

The script includes alert conditions:

- `Long Entry Signal` → `LONG_ENTRY`
- `Short Entry Signal` → `SHORT_ENTRY`
- `Long Exit Signal` → `LONG_EXIT`
- `Short Exit Signal` → `SHORT_EXIT`

> For automation: create TradingView alerts using these conditions, and paste your connector-specific JSON/webhook in the TradingView alert configuration UI (not in this repo).

---

## Notes / Troubleshooting

- Breakout zones and breakout entries only activate once ORB is **ready** for the session.
- If ORB values show `na`, check:
  - Timezone selection
  - Session string formatting (`HHMM-HHMM`)
  - Chart has data during that session

---

## License

Licensed under the **Mozilla Public License 2.0 (MPL‑2.0)**. See `LICENSE`.

---

## Disclaimer

This project is for informational/educational use only and is not financial advice.
Trading involves risk. Test thoroughly (paper trading and/or small size) before enabling any automated execution.
