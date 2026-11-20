# Model Executions

**Foundational quantitative models: derived, implemented from scratch, and tested on market data.**

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?logo=jupyter&logoColor=white)
![Focus](https://img.shields.io/badge/focus-foundations-informational)

This repository is my working foundation in quantitative finance. I studied each model the same way: start from the history and the math, implement the core algorithm by hand, verify it on synthetic data where the true answer is known, and then apply it to real market data. For most models I took it one step further and turned the signal into a rules-based basket trading strategy, backtested against SPY buy-and-hold.

The aim here is depth on the basics rather than production-ready strategies. These notebooks are where I learned how each tool actually works, and they are the building blocks for my more advanced research.

---

## Repository layout

```
Model Executions/
├── intermediate models/    # core statistical and signal-processing models
│   └── <Model>/
│       ├── <theory notebook>      # history, derivation, from-scratch implementation
│       └── <strategy notebook>    # the model applied as a basket trading strategy
└── advanced models/        # information-theoretic and range-based estimators
```

Most model folders follow a **theory → strategy** pattern:

| Notebook | What it contains |
|---|---|
| **Theory** | Historical background, mathematical derivation, from-scratch implementation, verification on synthetic data, application to real prices |
| **Strategy** | Data download → rolling signal → backtest engine → performance vs SPY buy & hold → holdings and allocation analysis → rebalance log → key takeaways, with explicit lookahead-bias prevention |

---

## 1. Intermediate models

| Model | Theory | Strategy | What's covered |
|---|---|---|---|
| **Volatility** | [Volatility](intermediate%20models/Volatility/Volatility.ipynb) | — | Simple vs log returns, annualisation, close-to-close historical volatility and other estimators |
| **Entropy** | [Entropy](intermediate%20models/Entropy/Entropy.ipynb) | [Entropy basket model](intermediate%20models/Entropy/Entropy%20Model.ipynb) | Shannon entropy of returns, rolling entropy for regime detection, directional entropy via Markov chains |
| **CUSUM** | [CUSUM](intermediate%20models/CUMSUM/CUSUM.ipynb) | [CUSUM basket model](intermediate%20models/CUMSUM/basket%20cusum%20model.ipynb) | CUSUM recursions, the *k* and *h* parameters, comparison with Shewhart and EWMA charts, average run length, change-point detection on returns and volatility; rolling CUSUM momentum score for asset selection |
| **Hurst exponent** | [Hurst](intermediate%20models/Hurst/Hurst.ipynb) | [Hurst basket model](intermediate%20models/Hurst/basket%20hurst%20model.ipynb) | Persistence vs mean reversion, rescaled range (R/S) analysis with the Anis–Lloyd correction, fractals and fractional Brownian motion; rolling Hurst exponent for asset selection |
| **Hidden Markov Model** | [Hidden Markov Models](intermediate%20models/Hidden%20Markov%20Model/Hidden_Markov_Models.ipynb) | [HMM regime-switching model](intermediate%20models/Hidden%20Markov%20Model/HMM%20model.ipynb) | Forward and backward algorithms with scaling, Viterbi vs posterior decoding, Baum–Welch (EM), Gaussian emissions; regime-based allocation |
| **Kalman filter** | [Kalman](intermediate%20models/Kalman%20Filter/Kalman.ipynb) | [Kalman basket model](intermediate%20models/Kalman%20Filter/Kalman%20model.ipynb) | State-space models, the predict/update cycle, a 1D filter from scratch; Kalman-filtered signals for basket allocation |
| **Monte Carlo methods** | [Monte Carlo Methods](intermediate%20models/Monte%20Carlo%20Methods/Monte_Carlo_Methods.ipynb) | — | Law of large numbers and CLT, O(N<sup>−1/2</sup>) convergence, estimating π, Monte Carlo integration, inverse-transform and rejection sampling, variance reduction |
| **SADF / GSADF** | [SADF](intermediate%20models/SADF/SADF%20nb.ipynb) | [SADF + RSI basket model](intermediate%20models/SADF/model%20SADF.ipynb) | Unit roots and the ADF test, why ADF misses bubbles, SADF (Phillips–Wu–Yu 2011) and GSADF/BSADF (Phillips–Shi–Yu 2015), Monte Carlo critical values; bubble-aware basket strategy |
| **Wavelets** | [Wavelet transforms](intermediate%20models/Wavelet/wavelet%20nb.ipynb) | — | Wavelets vs Fourier, continuous vs discrete transforms, price denoising with the DWT, VisuShrink thresholding and inverse reconstruction |

**Ikigaii** ([system documentation](intermediate%20models/Ikigaii/IKIGAII_DOCUMENTATION.txt)): a monthly-rebalancing asset-allocation engine on NSE equities, covering factor ranking, a market regime gate, a gold-vs-cash risk-off switch, trailing stop-losses, sector caps and a survivorship-bias fix.

---

## 2. Advanced models

| Model | Theory | Strategy | What's covered |
|---|---|---|---|
| **Lempel–Ziv complexity** | [Lempel-Ziv](advanced%20models/Lempel%20Ziv/Lempel%20Ziv.ipynb) | [LZ + RSI basket model](advanced%20models/Lempel%20Ziv/model%20Lempel.ipynb) | Information theory and markets, binarising price series, the LZ76 algorithm from scratch, normalisation, synthetic verification, rolling complexity to separate information-dense from random regimes |
| **Yang–Zhang volatility** | [Yang-Zhang](advanced%20models/Yang%20Zhang/Yang%20Zhang.ipynb) | [YZ low-volatility basket model](advanced%20models/Yang%20Zhang/Model%20YZ.ipynb) | Weaknesses of close-to-close volatility, range-based estimators (Parkinson, Garman–Klass and others), the Yang–Zhang combination of variance components; low-volatility asset selection vs SPY |

---

## Tech stack

Python · NumPy · pandas · SciPy · statsmodels · scikit-learn · Matplotlib · seaborn · Plotly · yfinance · pykalman · PyWavelets · vectorbt

## Getting started

```bash
git clone https://github.com/vij-akshat/model-executions.git
cd model-executions
pip install -r requirements.txt
jupyter lab
```

Notebooks are saved with their outputs, so they can be read on GitHub without running anything.

Market data comes from yfinance, so re-running a notebook today can give slightly different numbers than the saved outputs.

## Disclaimer

This is educational and research work. Backtests are hypothetical, ignore many real-world frictions, and are not investment advice.

## Related work

More applied work, including interactive Streamlit apps on regime detection, volatility estimation and delta-hedging P&L, is on my [GitHub profile](https://github.com/vij-akshat).

---

**Akshat** · Mathematics & Finance, Northeastern University
