# CDS Pricing on Convertible Bonds

This project develops a hybrid credit-equity pricing framework for a Credit Default Swap (CDS) written on a convertible bond.

The work was developed as part of an academic credit risk project at ISFA. It combines credit risk modeling, convertible bond valuation, equity optionality and Monte Carlo simulation.

## Objective

The objective of this project is to study how the valuation of a CDS changes when the underlying reference asset is not a standard corporate bond, but a convertible bond.

A convertible bond combines:

- a debt component, similar to a straight corporate bond;
- an embedded equity conversion option;
- exposure to the credit quality of the issuer;
- sensitivity to equity market variables such as stock price and volatility.

This makes the pricing of a CDS on a convertible bond more complex than the pricing of a standard CDS, because the credit exposure depends on whether the bond remains a debt instrument or is converted into equity.

## Financial Context

A standard CDS protects the buyer against the default of a reference entity in exchange for periodic premium payments.

For a standard bond, the credit exposure is mainly driven by:

- default probability;
- recovery rate;
- loss given default;
- maturity;
- risk-free discounting.

For a convertible bond, the situation is more subtle. The investor may choose to convert the bond into shares when conversion becomes optimal. As a result, the relevant credit exposure depends on the probability that default occurs before conversion.

This project therefore focuses on the interaction between:

- credit risk;
- equity optionality;
- conversion timing;
- default intensity;
- recovery assumptions;
- market parameters such as volatility and interest rates.

## Methodology

The project follows four main steps.

### 1. Convertible Bond Modeling

The convertible bond is analyzed as a hybrid instrument combining a straight bond component and an embedded conversion option.

The value of the convertible bond depends on:

- the nominal amount;
- the maturity;
- the coupon structure;
- the conversion ratio;
- the conversion price;
- the stock price of the issuer;
- interest rates;
- credit risk;
- equity volatility.

### 2. Credit Risk Modeling

Default risk is modeled using a reduced-form intensity framework.

The default time is represented through a hazard rate model, allowing the survival probability and default probability to be linked to market-implied credit risk assumptions.

The framework uses:

- a default intensity / hazard rate;
- a recovery rate assumption;
- risk-neutral discounting;
- premium leg and protection leg valuation.

### 3. Optimal Conversion with Least-Squares Monte Carlo

The key challenge is to estimate whether the convertible bond is likely to be converted before default.

To address this, the project uses the Least-Squares Monte Carlo method introduced by Longstaff and Schwartz to approximate the optimal conversion decision.

The method consists of:

- simulating stock price paths;
- working backward from maturity;
- estimating continuation values by regression;
- comparing immediate conversion value with continuation value;
- identifying the optimal conversion strategy;
- estimating the probability of default before conversion.

### 4. CDS Spread and Sensitivity Analysis

Once the probability of default before conversion is estimated, the CDS spread is computed by equating the premium leg and the protection leg.

The project then studies the sensitivity of the CDS spread to key parameters:

- stock price;
- volatility;
- risk-free interest rate;
- maturity;
- default intensity;
- conversion price;
- recovery rate.

## Numerical Case Study

The project includes a numerical case study based on a real issuer and market-inspired assumptions.

The implementation includes:

- historical volatility estimation from market data;
- calibration assumptions for default intensity and recovery rate;
- simulation of equity paths;
- Least-Squares Monte Carlo pricing;
- CDS spread computation;
- convergence analysis;
- Greeks and sensitivity analysis.

## Repository Structure

```text
notebooks/
  01_volatility_calibration.ipynb
  02_cds_convertible_bond_lsm_pricing.ipynb

report/
  Credit_Equity_Hybrid_CDS_Convertible_Bond_Report_FR.pdf

requirements.txt
README.md
```

The original academic report is written in French. This README provides an English summary of the project for international readability.

## Tech Stack

- Python
- NumPy
- pandas
- scipy
- matplotlib
- Monte Carlo simulation
- Least-Squares regression
- Credit risk modeling
- Convertible bond pricing

## Key Skills Demonstrated

- Credit derivatives pricing
- Convertible bond modeling
- Reduced-form credit risk modeling
- Hazard rate modeling
- Least-Squares Monte Carlo
- Optimal stopping
- Equity volatility estimation
- Sensitivity analysis
- Financial engineering
- Quantitative risk modeling

## References

- Longstaff, F. A. and Schwartz, E. S. (2001). *Valuing American Options by Simulation: A Simple Least-Squares Approach*. The Review of Financial Studies.
- Academic project report: *Modélisation hybride crédit–action d’un CDS sur obligation convertible*, ISFA, 2026.

## Authors

Academic group project by:

- Christ Ange Dylan Kouamé
- Aboubakar Ouattara
- Souleymane Ouattara

## Disclaimer

This project is for academic and educational purposes only. It does not constitute financial advice, investment advice or a production-ready pricing tool.
