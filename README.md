# LUXEM Prediction Lab

**Entropy-Based Regime Detection** | Real-Time Market Intelligence & Volatility Classification

---

## Overview

LUXEM (Live Universal eXtropy Engine for Markets) is a **real-time regime detection system** that classifies market states using entropy-based signal analysis.

Traditional market indicators lag during volatility because they rely on backward-looking statistics. LUXEM monitors **structural entropy** — detecting regime transitions (CALM → FRACTAL → CASCADE) before traditional indicators react.

**Core capability:** Identify when market dynamics are shifting regimes, not just moving prices.

---

## Problem Statement

Markets don't just move — they **change behavior**.

A price drop in a CALM regime is fundamentally different from a price drop in a CASCADE regime. Traditional indicators treat them the same.

**LUXEM distinguishes between:**
- **CALM:** Low entropy, mean-reverting, predictable structure
- **FRACTAL:** Transitional state, increasing complexity, emergent patterns
- **CASCADE:** High entropy, breakdown of structure, regime collapse

This enables:
- ✅ Early warning of volatility regime shifts
- ✅ Context-aware risk assessment
- ✅ Adaptive strategy selection based on market state

---

## Architecture

### Core Components

**Entropy Engine**  
Computes structural entropy (Φ) from multi-source market data:
- Price action (tick-level granularity)
- Order flow dynamics
- Sentiment signals (news, social)
- Cross-asset correlation shifts

**Regime Classifier**  
Maps entropy measurements to stability bands:
- GREEN (CALM): Φ in stable range
- YELLOW (FRACTAL): Φ approaching transition boundary
- RED (CASCADE): Φ indicating structural breakdown

**Signal Aggregator**  
Combines multiple data streams into unified confidence measure:
- Weighted consensus across sources
- Divergence detection (when signals disagree)
- Temporal smoothing with drift awareness

**WebSocket Streaming Backend**  
Real-time telemetry delivery:
- FastAPI server with async message bus
- 100Hz update frequency
- Priority queue for critical regime shifts

**React Observatory Dashboard**  
Live visualization interface:
- Real-time Φ charts
- Regime state indicators
- Multi-timeframe analysis
- Alert configuration

---

## System Flow
```text
┌──────────────────────────────────────────────┐
│         Data Sources (Market Feeds)          │
│  Price • Volume • Sentiment • Correlations   │
└──────────────────────────────────────────────┘
                    │
                    ▼
        ┌───────────────────────┐
        │   Signal Aggregator   │
        │  (Multi-source Fusion)│
        └───────────────────────┘
                    │
                    ▼
        ┌───────────────────────┐
        │    Entropy Engine     │
        │   (Φ Computation)     │
        └───────────────────────┘
                    │
                    ▼
        ┌───────────────────────┐
        │   Regime Classifier   │
        │  CALM/FRACTAL/CASCADE │
        └───────────────────────┘
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
   ┌────────┐  ┌────────┐  ┌─────────┐
   │Database│  │WebSocket│ │Dashboard│
   │Storage │  │Stream   │ │ (React) │
   └────────┘  └────────┘  └─────────┘
```

---

## Key Features

### 1. Real-Time Regime Detection
Continuous classification of market state:
- **CALM:** Orderly price action, low volatility, predictable patterns
- **FRACTAL:** Transitional dynamics, increasing complexity, emergent structure
- **CASCADE:** Breakdown of correlation structure, high volatility, unpredictable moves

### 2. Multi-Source Signal Fusion
Integrates heterogeneous data streams:
- Price and volume microstructure
- Sentiment scoring from news feeds
- Cross-asset correlation matrices
- Order book depth analysis (where available)

### 3. Entropy-Based Classification
Structural measurement rather than statistical volatility:
- Detects **how markets are moving**, not just how much
- Identifies regime transitions before price breakdowns
- Distinguishes between healthy volatility and structural instability

### 4. Adaptive Alert System
Context-aware notifications:
- YELLOW transitions (regime shift warning)
- RED triggers (cascade detection)
- Divergence alerts (signal disagreement)
- Custom threshold configuration

### 5. Live Dashboard
Real-time visualization:
- Entropy timeseries charts
- Current regime state indicators
- Historical regime transitions
- Multi-timeframe correlation

---

## Use Cases

### Volatility Regime Trading
Adapt strategy based on detected market state:
- CALM: Mean-reversion strategies
- FRACTAL: Reduced position sizing, increased monitoring
- CASCADE: Risk-off positioning, protective stops

### Risk Management
Early warning system for portfolio exposure:
- Detect regime shifts before traditional VIX spikes
- Cross-asset correlation breakdown alerts
- Systemic risk monitoring

### Market Intelligence
Understand market structure, not just price movement:
- Identify when "business as usual" assumptions break down
- Track entropy trends across asset classes
- Monitor structural stability of trading environments

### Research & Backtesting
Evaluate strategy performance across regime types:
- Classify historical periods by entropy regime
- Test strategy robustness across CALM/FRACTAL/CASCADE states
- Understand when strategies work vs. when they fail

---

## Technical Stack

**Backend:** Python, FastAPI, AsyncIO  
**Frontend:** React, Recharts, Tailwind CSS  
**Data:** NumPy, Pandas, SQLite  
**Streaming:** WebSockets, Real-time message bus  
**APIs:** Market data providers (alpaca, polygon, etc.)

---

## What's Public vs. Proprietary

| **Public (Architecture)** | **Proprietary (Implementation)** |
|---------------------------|-----------------------------------|
| Regime classification framework | Entropy calculation formulas |
| Multi-source fusion approach | Signal weighting algorithms |
| Dashboard design patterns | Threshold calibration methods |
| WebSocket protocol structure | Φ computation core |
| Integration methodology | Optimization parameters |

**System design:** Openly documented  
**Mathematical core:** Protected IP

---

## Design Philosophy

> **Markets don't just move — they change behavior.**

LUXEM operates on three principles:

1. **Entropy over volatility** — Structural complexity matters more than price magnitude
2. **Regime awareness** — Context determines interpretation (same move, different meaning)
3. **Early detection** — Transitions appear in entropy before they appear in price

---

## Validation Approach

### Historical Regime Mapping
Backtested classification against known market events:
- 2020 COVID crash (CALM → CASCADE transition)
- 2021 meme stock volatility (FRACTAL persistence)
- 2022 rate hike cycles (CALM → FRACTAL oscillation)

**Goal:** Verify that entropy regimes align with observable market structure changes.

### Cross-Asset Correlation
Testing structural similarity across markets:
- Equity volatility regimes vs. crypto
- Commodity cascade detection
- FX regime synchronization

**Hypothesis:** True regime shifts appear across uncorrelated assets simultaneously.

### Live Monitoring
Real-time validation in production environment:
- Continuous entropy tracking
- Regime transition logging
- Performance metrics (detection latency, false positive rate)

---

## Current Status
```text
DEVELOPMENT: [▮▮▮▮▮▮▮▮▯▯] 85% — Live Prototype
```

**Completed:**
- ✅ Entropy engine implementation
- ✅ Multi-source signal aggregation
- ✅ Regime classification logic
- ✅ WebSocket streaming backend
- ✅ React dashboard (live updates)
- ✅ SQLite historical storage

**In Progress:**
- ⚙️ Additional market data source integrations
- ⚙️ Backtesting infrastructure
- ⚙️ Alert API for programmatic access

**Next Phase:**
- 🔜 Public API release (rate-limited access)
- 🔜 Extended asset class coverage
- 🔜 Strategy performance analytics by regime

---

## Example Workflow

### Conceptual API Usage
```python
# Conceptual interface (implementation proprietary)
from luxem import EntropyEngine, RegimeMonitor

engine = EntropyEngine()
monitor = RegimeMonitor(engine)

# Subscribe to regime changes
@monitor.on_regime_change
async def handle_transition(old_regime, new_regime, phi_value):
    if new_regime == "CASCADE":
        print(f"Alert: Market entering CASCADE state (Φ={phi_value})")
        # Trigger risk-off protocols

# Start monitoring
await monitor.stream()
```

### Dashboard Access

Live monitoring interface:
```text
http://localhost:3000/dashboard
```

Real-time WebSocket feed:
```text
ws://localhost:8000/ws/regime-stream
```

---

## Integration with Sovereign Nexus

LUXEM feeds into the broader intelligence framework:

**→ [Stallion Core](https://github.com/derekwins88/stallion-core)**  
Cross-validates market regime against physics simulations (structural homology detection)

**→ [Unified Phi Layer](https://github.com/derekwins88/unified-phi-oracle)**  
Contributes entropy measurements to multi-domain confidence consensus

**→ [PredictIQ Platform](https://github.com/derekwins88/predictiq-platform)**  
Provides regime context for prediction market intelligence

---

## Research Context

LUXEM tests a core hypothesis:

> **Entropy-based regime detection can identify structural market transitions before traditional indicators.**

This is part of broader research into **Invariant-Preserving Intelligence** — investigating whether systems can detect when fundamental operational assumptions are breaking down.

In markets, this means:
- Detecting when mean-reversion assumptions fail (CALM → FRACTAL)
- Identifying when correlation structures collapse (FRACTAL → CASCADE)
- Recognizing when "normal" volatility becomes structural instability

---

## Related Projects

- **[Stallion Core](https://github.com/derekwins88/stallion-core)** — Cross-domain validation engine
- **[PredictIQ Platform](https://github.com/derekwins88/predictiq-platform)** — Market intelligence aggregation
- **[Sovereign Intelligence Nexus](https://github.com/derekwins88/sovereign-intelligence-nexus)** — Full portfolio overview

---

## Contact

For collaboration, data partnerships, or API access:

📧 Derekalexanderespinoza@gmail.com  
💼 [LinkedIn](https://www.linkedin.com/in/derek-espinoza-27981477)  
🌐 [Portfolio](https://github.com/derekwins88/sovereign-intelligence-nexus)

---

**Detecting regime shifts before markets break.**

*Designed and maintained by Derek Espinoza • Los Angeles, CA • 2026*
