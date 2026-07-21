# Crypto H0 Edge

**Research notebook for the 5‑second BTC/USDT directional edge.**
Discovery, validation, and honest documentation of what worked and what didn't.

---

## What This Is

This repository contains the complete research pipeline that discovered and
validated a **+8 pp directional edge** in 5‑second Bitcoin predictions. It
is a historical record — the production code lives in a separate repository.

---

## Key Findings

| Question | Answer |
|----------|--------|
| Is there a real edge? | ✅ Yes — 60 % accuracy vs 52 % baseline, confirmed with walk‑forward, block bootstrap, and permutation testing. |
| Is it economically viable? | ❌ No — standard exchange fees consume the edge. Documented openly. |
| Does it work at longer horizons? | ❌ No — tested 30 min and 1 h; no edge found. |
| Were there false positives? | ✅ Yes — initial models showed inflated accuracy due to autocorrelation and temporal leakage. All documented. |

---

## Validation Pipeline

The same rigorous pipeline used across all EventHorizon products:

- Walk‑forward analysis with spaced sampling
- Block bootstrap (multiple block sizes)
- Permutation test (shuffled targets, aligned mask)
- Gap bootstrap (real vs. permuted)
- Temporal stability across 6 partitions

This pipeline is extracted into a standalone library:
**[honest‑validation‑toolkit](https://github.com/EventHorizon-ia/honest-validation-toolkit)**.

---

## Repository Contents

crypto-h0-edge/    
notebooks/ # Jupyter notebooks (discovery, validation, simulation)    
data/ # Sample datasets (or links to Kaggle datasets)    
README.md    

---

## Links

- [Production Code](https://github.com/EventHorizon-ia/eventhorizon-crypto)
- [Main Hub](https://github.com/EventHorizon-ia/eventhorizon)
- [Public Audit Dashboard](https://eventhorizon-ia.github.io/trader-ai/dashboard-en.html)

---

*Crypto H0 Edge — Proof that the edge exists. Proof that it's not enough.*
