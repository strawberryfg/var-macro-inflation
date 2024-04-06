# var-macro-inflation
One of the most important macro economics indicator : inflation forecast using Vector Autoregressive Model

## Disclaimer

Some code is borrowed from [here](https://github.com/stefan-jansen/machine-learning-for-trading/blob/main/09_time_series_models/04_vector_autoregressive_model.ipynb).

## Introduction

$y_t \in \mathcal{R}^{k\times 1}$ = $\mathbf{A}$ $\mathbf{\hat{Y}}$ where $\mathbf{A} \in \mathcal{R}^{k \times kp}$ = $[ \mathbf{A}_1, \mathbf{A}_2, ... , \mathbf{A}_p]$, $\mathbf{A}_i$ (for $i=1..p$) $\in \mathcal{R}^{k\times k}$


and $p$ is the order for $AR$ (SARIMAX) which is the time lag value

$\mathbf{\hat{Y}}$ $\in \mathcal{R}^{kp \times 1}$ = $[y_{t-1}, y_{t-2}, ... , y_{t-p}]^T$,  $y_{t-i}$ (for $i=1..p$) $\in \mathcal{R}^{k \times 1}$

## Results
### Modelling core, headline, expected inflation, consumer sentiment, VIX (which tracks volatility of S&P 500) all together

<img width="922" alt="Screenshot 2024-04-06 at 14 43 31" src="https://github.com/strawberryfg/var-macro-inflation/assets/8860188/8e3ff9c5-13a8-4bb8-ab8c-0daa6799dd5f">

Model does not seem to predict consumer sentiment and VIX even for in-sample data points.

### Keeping only the necessary - headline inflation, core inflation, PCE (personal consumer expenditure), and Fed Funds Rate (which is the overnight interbank loan offer rate)

the london equivalent for Fed Funds rate is LIBOR rate. And for prediction focusing on the UK market or Eurozone inflation please refer to [Fred](https://fred.stlouisfed.org/searchresults?st=inflation+year+over+year) and search for relevant data. ECB also has its target rate as Fed Funds rate counterpart.

Fed Discount rate was not taken into account as it is the interest rate for which central bank charges commercial banks on borrowing funds from the Fed, and is tangential to the topic.

The motivation behind setting these four indicators is that they should (*at least appear to be*) be kind of related to each other.

Other factors that may come in handy:

- Producer Price Index (as apposed to CPI)
- Industrial Production (as in this original [notebook](https://github.com/stefan-jansen/machine-learning-for-trading/blob/main/09_time_series_models/04_vector_autoregressive_model.ipynb))


<img width="940" alt="Screenshot 2024-04-06 at 14 52 15" src="https://github.com/strawberryfg/var-macro-inflation/assets/8860188/f062c46a-0147-4fce-a6a9-80ae262c6812">

## Summary
in any case, the core inflation is ticking up and the headline inflation remains sticky. Fed interest rate stays high and there's no easing of PCE as well.
