# Implied Volatility of European SPX Options

A numerical finance project investigating the implied volatility of European S&P 500 (SPX) options using the Black–Scholes model and Newton's Method. The project also constructs an interpolated U.S. Treasury yield curve for accurate option pricing and demonstrates the volatility smile observed in real markets.

## Overview

This project was completed as part of **MAT264 – Numerical Analysis**.

Using historical market data from **27 February 2026**, we:

- Construct an interpolated risk-free interest rate curve.
- Implement the Black–Scholes pricing model.
- Compute implied volatility using Newton's Method.
- Compare model prices against market prices.
- Visualize the volatility smile and volatility skew.
- Discuss why real markets violate the Black–Scholes constant volatility assumption.

---

## Repository Structure

```
.
├── IVP MAT264.ipynb                 # Jupyter notebook containing all computations
├── MAT264 Implied Volatility.docx   # Final project report
└── README.md
```

---

## Methodology

### 1. Data Collection

- SPX European option prices obtained from Bloomberg Terminal.
- U.S. Treasury yield curve data collected using Bloomberg YCGT0025.
- Dividend yield and SPX spot price incorporated into pricing model.

### 2. Yield Curve Construction

Two interpolation methods were implemented:

- Lagrange Polynomial Interpolation
- Natural Cubic Spline Interpolation

The cubic spline was ultimately used because it:

- avoids Runge's phenomenon,
- provides smooth interest-rate estimates,
- behaves locally rather than globally,
- produces realistic yield curves suitable for option pricing.

---

### 3. Black–Scholes Pricing

European call option prices were computed using the Black–Scholes model with:

- Spot price
- Strike price
- Time to maturity
- Risk-free rate (interpolated)
- Dividend yield
- Volatility

---

### 4. Implied Volatility

Implied volatility was obtained by solving

\[
BS(\sigma)=P_{market}
\]

using **Newton's Method**.

The implementation includes:

- Vega computation
- Iterative Newton updates
- Convergence tolerance of \(10^{-6}\)
- Handling of near-zero Vega cases

---

### 5. Volatility Smile

The notebook produces:

- Implied volatility vs strike price
- Comparison across multiple maturities
- Volatility smile and volatility skew visualizations

---

## Key Results

- Fast Newton convergence (typically fewer than 4 iterations)
- Accurate implied volatility estimates
- Cubic spline interpolation significantly outperformed high-degree polynomial interpolation
- Clear volatility smile observed in SPX options
- Longer maturities exhibit flatter volatility structures

The results illustrate why the constant-volatility assumption of Black–Scholes does not hold in practice.

---

## Technologies Used

- Python
- NumPy
- Pandas
- SciPy
- Matplotlib
- Jupyter Notebook

---

## Files

### `IVP MAT264.ipynb`

Contains:

- Yield curve interpolation
- Black–Scholes implementation
- Newton solver
- Implied volatility calculations
- Figures and visualizations

### `MAT264 Implied Volatility.docx`

Final report describing:

- Mathematical derivations
- Numerical methods
- Experimental results
- Discussion of volatility smiles and model assumptions

---

## Learning Outcomes

This project demonstrates practical applications of numerical analysis in quantitative finance, including:

- Numerical interpolation
- Root-finding algorithms
- Option pricing
- Implied volatility estimation
- Financial data analysis
- Model validation against market data

---

## Authors

- Josh Villas
- Marko Rajicic
- Nikita Nathania Rudy
- Reynard Jonatan Kusnadi
- Venturio Talenta Kusuma

---

## References

- Black, F., & Scholes, M. (1973). *The Pricing of Options and Corporate Liabilities*. Journal of Political Economy.
- MAT264 Lecture Notes – Introduction to Numerical Analysis.
