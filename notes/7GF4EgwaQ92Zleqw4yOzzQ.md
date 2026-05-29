# Position Review Framework — Design Specification

**Purpose:** An *informative* (non-binding) framework that flags positions for review and surfaces the evidence behind each flag, to discipline conviction-driven sell decisions.
**Scope:** Equity and alternatives sleeves across PGI, ABF, C2 Atlantic. Debt handled by a parallel credit-specific track.
**Principle:** Signals inform; the PM decides. Every flag comes with its underlying values shown side by side, never as a black-box verdict.

---

## 1. Design philosophy

The framework is built on three commitments:

1. **Informative, not binding.** No auto-execution. Output is a review score plus the raw signal values that produced it. A flagged position triggers a deliberate human decision, not a trade.

2. **Pre-commitment at entry.** The thesis, invalidation conditions, target, and horizon are recorded *when the position is opened*. This is the single most important behavioral safeguard — exit logic decided in the emotional moment is where the disposition effect does its damage.

3. **Per-bucket signal sets, common machinery.** The scoring spine (how signals combine into a review score) is identical across all positions. What differs by asset class is *which signals are active*, *how they're parameterized*, and *what invalidation means*. This keeps the system auditable while respecting that a gold position and a bank stock fail in completely different ways.

---

## 2. The common scoring spine

Every position, regardless of bucket, gets scored on up to five **signal categories**. Not every category applies to every bucket (e.g. valuation doesn't apply to gold), but the structure is shared.

### 2.1 The five categories

| Category | What it captures | Direction of concern |
|---|---|---|
| **Trend / technical** | Price momentum deterioration | Breaking down |
| **Valuation** | Richness vs. own history / peers / fundamentals (detailed in §5) | Too expensive |
| **Risk / sizing** | Position's risk contribution vs. budget | Too big |
| **Thesis** | Distance from pre-committed thesis & invalidation conditions | Thesis breaking |
| **Relative strength** | Under/over-performance vs. relevant benchmark | Lagging peers |

### 2.2 Per-signal scoring

Each active signal produces:

- A **raw value** (e.g. price vs. 200d MA = −4.2%)
- A **normalized score** in [0, 100], where higher = more reason to review
- A **status**: �� OK / �� Watch / �� Flagged, based on bucket-specific thresholds

Normalization is typically a z-score against the signal's own history, mapped to [0,100] via a logistic or clipped-linear transform:

$$\text{score}_i = 100 \cdot \text{clip}\!\left(\frac{z_i - z_{\text{lo}}}{z_{\text{hi}} - z_{\text{lo}}},\, 0,\, 1\right)$$

where $z_{\text{lo}}, z_{\text{hi}}$ are the watch/flag thresholds for that signal in that bucket.

### 2.3 Composite review score

The composite is a **weighted average of active category scores**, with weights set per bucket:

$$\text{Review Score} = \sum_{c \in \text{active}} \omega_c^{(\text{bucket})} \cdot \text{score}_c$$

with $\sum_c \omega_c = 1$. The weights encode what matters for that asset class — e.g. for a momentum-driven commodity, trend gets high weight; for a value stock, valuation and thesis dominate.

**Crucially, the composite never hides its components.** The display is always: composite score, then each category score, then the raw underlying values. (This is the "score + signal values side by side" requirement.)

### 2.4 The thesis category is special

Thesis isn't a market-data signal — it's a structured check against what was written at entry. It scores on:

- **Invalidation conditions hit** (binary checks, e.g. "loss > max tolerance", "thesis KPI rolled over") → each hit adds to the score
- **Time decay**: fraction of horizon elapsed without thesis playing out
- **Target proximity**: how close price is to the recorded fair-value target (near/at target is itself a review trigger — for trimming, not necessarily exit)

This category is the connective tissue between the discretionary process and the quantitative signals. Its full mechanics — claim decomposition, the scoring formula, per-bucket data sources, and graceful degradation of manual inputs — are specified in §6.

---

## 3. The position record (entry-time commitment)

Every position carries a record, created at entry, that the framework reads:

```
Position Record
├── Identifiers: ticker, ISIN, bucket, fund
├── Entry: date, price, size, FX
├── Thesis: 2–3 falsifiable statements
├── Invalidation conditions: explicit, checkable
├── Fair-value target: price + methodology
├── Time horizon: expected months to thesis realization
├── Max loss tolerance: % from entry (review trigger, not stop)
├── Risk budget: max % of sleeve risk contribution
└── Review notes: log of past reviews + decisions
```

The thesis and invalidation conditions should be written so a third party could check them. "EDP because renewables tailwind" is not checkable. "EDP: regulated-asset-base growth >5%/yr, net debt/EBITDA stays <4x, dividend cover >1.3x; invalidated if any breaks for two consecutive quarters" is.

---

## 4. Per-bucket specifications

The buckets, per your structure:

- **Alternatives** — individual frameworks (each position is its own market)
- **Equity ETFs** — individual frameworks (each is a whole-market scope)
- **PT Equities** — uniform framework, per-company parameter tweaks
- **Debt** — split IG/HY × senior/subordinated (parallel credit track, §7)

### 4.1 Alternatives — individual frameworks

These are the most tactical positions and the best fit for mechanical trend signals. Current holdings include gold, oil (short), and the crypto allocation via GCF — which need very different treatment.

**Gold (XAU / gold ETF)**

| Category | Active? | Signal | Watch / Flag thresholds |
|---|---|---|---|
| Trend | ✓ (high weight) | Price vs. 200d MA; ATR trailing stop (k=3) | <0% / <−5% vs MA |
| Valuation | ✗ | No earnings; skip | — |
| Risk/sizing | ✓ | Risk contribution vs. budget | >budget / >1.3×budget |
| Thesis | ✓ | Hedge thesis intact? (real rates, USD, tail-hedge role) | invalidation hit |
| Rel. strength | △ (low) | vs. real-rate proxy / DXY | optional |

Weight suggestion: Trend 0.40, Risk 0.25, Thesis 0.35.

Gold is held as a strategic hedge, so thesis stays meaningful, but it's also trend-sensitive enough that the ATR stop is informative. If it's a long-term hedge, weight thesis higher; if tactical, weight trend higher.

**Oil (short position)**

Shorts need inverted trend logic and tighter risk management (unbounded loss). Active categories: Trend (inverted — concern is price *rising*), Risk/sizing (high weight — shorts are dangerous), Thesis (the macro view being expressed). Valuation and relative strength off. Weight: Trend 0.35, Risk 0.40, Thesis 0.25. ATR stop is more important here precisely because it's a short.

**Crypto allocation via GCF (UP 3CC, held by PGI)**

PGI's UP 3CC line is a feeder into the Global Crypto Fund. It is treated as a **single crypto allocation**, not coin-by-coin — the underlying coin selection is GCF's job and is out of scope here. The PGI-level decision is purely *how much crypto this book should hold*: a sizing-and-mandate control, not a trading decision.

| Category | Active? | Signal |
|---|---|---|
| Trend | △ (low / optional) | GCF NAV vs. 200d MA — informative only, not traded tactically at PGI level |
| Valuation | ✗ | No meaningful valuation anchor for crypto |
| Risk/sizing | ✓ (dominant) | Risk contribution vs. budget — highest-vol exposure in PGI, small NAV moves create large risk contribution |
| Thesis | ✓ | Strategic rationale for crypto in PGI + alternatives sub-cap (<20%) and any crypto-specific limit |
| Rel. strength | ✗ | Off |

Weight: Risk/sizing 0.55, Thesis 0.45 (Trend optional, ≤0.10 if included — reweight the other two proportionally). Review monthly, or whenever GCF NAV moves materially enough to push the allocation toward its risk or mandate limit.

The key control is risk-budget creep: because crypto is the highest-volatility holding in PGI, a rally can quietly make it the dominant risk contributor even while it's a small euro weight. The framework's job is to flag that, so the allocation decision is deliberate rather than passive drift.

### 4.2 Equity ETFs — individual frameworks

Each ETF is a whole-market exposure (S&P 500 Pure Value, MSCI Japan, MSCI Australia, MSCI Mexico, MSCI Korea, MSCI Canada, MSCI World ex-US, MSCI EM ex-China, MSCI China). The framework treats each as a market-timing/allocation decision, not a stock.

| Category | Active? | Signal | Notes |
|---|---|---|---|
| Trend | ✓ | Price vs. 200d MA; 50/200 cross | Whole-index trend |
| Valuation | ✓ | Index CAPE / forward P/E vs. own 10y history | Market-level rich/cheap |
| Risk/sizing | ✓ | Risk contribution vs. budget | Regional concentration |
| Thesis | ✓ | Allocation rationale (why this market, this weight) | Macro/regional view |
| Rel. strength | ✓ | vs. MSCI World (is this region lagging?) | Rotation signal |

Weight suggestion (balanced): Trend 0.25, Valuation 0.25, Risk 0.20, Thesis 0.20, Rel.strength 0.10.

Per-ETF tweaks: factor ETFs (S&P 500 Pure Value) add a **factor-spread valuation** signal (value-vs-growth spread vs. history); single-country EM ETFs (Mexico, Korea) weight currency and relative-strength higher.

### 4.3 PT Equities — uniform framework, per-name tweaks

Ten names (BCP, CTT, EDP, Mota-Engil, Galp, NOS, Navigator, REN, Sonae, Jerónimo Martins), held on fundamental conviction. Uniform spine, with per-company thesis and a few sector-specific signals.

| Category | Active? | Signal | Notes |
|---|---|---|---|
| Trend | ✓ (low weight) | Price vs. 200d MA | Informative only — don't fight conviction on noise |
| Valuation | ✓ (high weight) | P/E, EV/EBITDA, P/B, div yield vs. own history & PSI peers | Core for value names |
| Risk/sizing | ✓ | Risk contribution vs. budget | Trim winners |
| Thesis | ✓ (high weight) | Per-company fundamental KPIs + invalidation | The heart of it |
| Rel. strength | ✓ | vs. PSI-20 and vs. sector | Idiosyncratic underperformance |

Weight suggestion: Valuation 0.25, Thesis 0.35, Risk 0.20, Rel.strength 0.10, Trend 0.10.

Trend is deliberately down-weighted for conviction equity — a price dip your thesis explains shouldn't dominate the score. Thesis and valuation lead.

**Per-name tweaks** (sector-driven KPIs feed the thesis category):

- **Banks (BCP):** NII trajectory, NPL ratio, CET1, cost/income — and link to the Merton-style PD from the credit track
- **Utilities (EDP, REN):** regulated asset base growth, net debt/EBITDA, regulatory decisions, dividend cover
- **Retail (Jerónimo Martins, Sonae):** like-for-like sales, margin trend, Biedronka/Poland exposure for JM
- **Cyclicals (Mota-Engil, Navigator):** order book / pulp prices, leverage, FX (Navigator USD pulp exposure)
- **Telecoms (NOS):** ARPU, subscriber trend, capex cycle
- **Energy (Galp):** production, refining margin, oil-price beta, Namibia upside thesis
- **Logistics (CTT):** parcel volume, banking arm (Banco CTT) contribution

The signal machinery is identical; only the thesis KPIs and valuation comparables change per name.

---

## 5. Valuation mechanics (detailed)

Valuation is the category most easily done badly. A single multiple in isolation is meaningless — P/E of 12 is only informative *relative to something*. Every valuation signal must answer: **relative to what?** There are three reference frames, and robust valuation blends more than one.

### 5.1 The three reference frames

| Frame | Question it answers | Failure mode it guards against |
|---|---|---|
| **Own history** | Is it expensive *for itself*? | The whole asset class re-rated; "cheap vs. peers" misleads |
| **Peer / cohort** | Is it expensive *vs. comparables*? | The asset is in a self-contained bubble; "cheap vs. own history" misleads |
| **Fundamentals** | Is the price justified by what it produces? | Both relative frames drift together; only fundamentals anchor absolutely |
