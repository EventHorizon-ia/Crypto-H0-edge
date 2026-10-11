# Crypto H0 Edge

**Research notebook for 5-second BTC/USDT directional prediction.**  
Discovery, temporal validation, uncertainty analysis and honest documentation
of what worked, what did not work, and what remains unproven.

---

## What This Is

This repository contains the research pipeline used to investigate whether
short-horizon BTC/USDT price movements contain a predictable directional
signal.

It is a historical research record. The production-oriented code, execution
simulation and deployment research live in a separate repository:

**[EventHorizon-Crypto](https://github.com/EventHorizon-ia/EventHorizon-Crypto)**

---

## Key Findings

| Question | Answer |
|---|---|
| Did the research find a promising H0 result? | A focused H0 model reached **60.7% validation accuracy**. This was a validation-set result used for checkpoint selection. |
| Was this confirmed as a final out-of-sample edge? | **No.** The result was not evaluated as a final, independent test of the selected checkpoint. |
| Was it economically viable? | **No.** Under the evaluated maker-execution assumptions, the strategy was economically unviable. |
| Did longer horizons work? | The research focused primarily on H0. Longer-horizon results were not established as an edge. |
| Were false positives found? | **Yes.** Initial models showed inflated accuracy due to autocorrelation and temporal leakage. These issues were documented and addressed in later validation. |

---

## Important Distinction

The 60.7% H0 result came from a validation set used to compare checkpoints
and select the best epoch.

It should not be interpreted as a final out-of-sample result.

A validation set supports model selection and early stopping. A separate,
untouched test set is required for an unbiased final evaluation after the
model and checkpoint have been fixed. [440][442][445]

---

## Research Models

| Model | Scope | Validation result | Interpretation |
|---|---|---:|---|
| **Multi-horizon model** | H0–H9 | 51.2% mean honest-validation accuracy; H0 59.9% | Research result |
| **H0-focused model** | H0 only | 60.7% H0 validation accuracy | Promising validation result, not final proof |

The H0-focused result motivated further research, but it did not establish a
tradable edge.

---

## Validation Pipeline

The research pipeline included:

- Temporal validation with embargo
- Walk-forward analysis
- Block bootstrap for uncertainty estimation
- Paired gap bootstrap comparing model and baseline
- Permutation testing with shuffled targets and aligned masks
- Temporal-stability analysis across partitions

The validation methodology is available through the standalone library:

**[honest-validation-toolkit](https://github.com/EventHorizon-ia/honest-validation-toolkit)**

---

## Economic-Viability Study

The economic study used a different checkpoint:

```text
mente_h0_v2_h0_20260717_161041.pt
```

It simulated maker limit orders rather than assuming immediate execution at
the current price.

The simulation used:

- A one-tick distance from the current price
- A five-second order-waiting window
- Trade closure five seconds after the signal
- Maker-fee sensitivity analysis

Under these assumptions, the strategy was economically unviable.

### Honest limitations

- The validation period was also used for checkpoint selection.
- The economic simulation used a different checkpoint from the best H0
  validation result.
- A limit order was considered filled when price touched its level; queue
  position, partial fills and adverse selection were not modeled.
- Signals could overlap; position limits and order cancellation were not
  modeled.
- Results are specific to BTC/USDT data and the evaluated period.

---

## What Was Learned

- Temporal leakage and autocorrelation can create misleadingly strong
  short-horizon results.
- A high validation accuracy does not establish a final out-of-sample edge.
- A predictive result can still be economically unviable after execution
  constraints and fees.
- Negative results and false positives are essential parts of honest research.

---

## Repository Contents

```text
crypto-h0-edge/
├── notebooks/   # Discovery, validation and simulation research
├── data/        # Sample data or links to source datasets
└── README.md
```

---

## Links

- [Production Code](https://github.com/EventHorizon-ia/EventHorizon-Crypto)
- [Main Hub](https://github.com/EventHorizon-ia/EventHorizon)
- [Public Audit Dashboard](https://eventhorizon-ia.github.io/trader-ai/dashboard-en.html)

---

*Crypto H0 Edge — honest research, documented limitations and negative
results.*