# Parametric Estimation and Distribution Fitting for Air Quality Index Data in Mexico City

---

## Overview

In this project, we apply parametric estimation techniques to fit distributions to the air quality index (AQI) data for the Mexico City Metropolitan Area (CDMX). We use two specific distributions: the Gamma distribution and the Rayleigh distribution. By deriving estimators analytically and applying them to real-world data, we aim to understand the suitability of these distributions for modeling AQI data. The process involves deriving estimators using both the Method of Moments (MoM) and Maximum Likelihood Estimation (MLE), implementing these estimators in Python, and evaluating the performance of the fitted models.

---

## Methodologies

### Analytical Derivation

1. **Method of Moments Estimators**:
   - Rayleigh Distribution
     - Parameter: \(\sigma\)
     - Probability density function: \(pdf(x; \sigma) = \frac{x}{\sigma^2} \exp\left(-\frac{x^2}{2\sigma^2}\right)\)
   - Gamma Distribution
     - Parameters: \(\alpha\) (shape) and \(\beta\) (scale)
     - Probability density function: \(pdf(x; \alpha, \beta) = \frac{x^{\alpha - 1} \exp\left(-\frac{x}{\beta}\right)}{\Gamma(\alpha) \beta^\alpha}\)

2. **Maximum Likelihood Estimators**:
   - Derive the MLE for \(\sigma\) for the Rayleigh distribution.
   - Derive the MLE for \(\alpha\) and \(\beta\) for the Gamma distribution, noting the resulting transcendental equation.

### Application to Real Data

1. **Implementing Estimators in Python**: Develop Python functions to compute the estimators for the Rayleigh and Gamma distributions using both the Method of Moments and Maximum Likelihood Estimation.
   - Create a function that computes the MoM and MLE estimators for a given sample and distribution type.
   - Ensure the function handles the complexity of the Gamma-MLE estimator.

2. **Estimation for Selected Pollutant Across All Zones**: Using a single pollutant across all zones, compute the four probability density functions (pdfs) for each zone.
   - Calculate the MoM and MLE estimators for both Rayleigh and Gamma distributions for each zone.
   - Create a plot with five panels, each representing a zone, showing the empirical distribution (histogram) and the four estimated pdfs.

### Evaluation

1. **Comparing Gamma-MLE and Rayleigh-MLE**: Evaluate the performance of the Gamma-MLE and Rayleigh-MLE models for each region.
   - For each region, compute:
     - The log-likelihood of the sample evaluated at the MLE estimators.
     - The Bhattacharyya distance between the empirical distribution and the estimated distributions.
   - Determine the best-fitted model based on these metrics.

---

## Dependencies

- `numpy`: For numerical computations.
- `pandas`: For data manipulation and analysis.
- `matplotlib`: For plotting and visualization.
- `scipy.special`: For special functions like the digamma function.
- `scipy.optimize`: For numerical optimization, specifically for solving equations using `fsolve`.
- `scipy.stats`: For statistical functions, including the probability density functions for the Rayleigh and Gamma distributions.

---

## Resources

- **AQI Data**: Sourced from the Secretaría del Medio Ambiente (SEDEMA), which provides hourly AQI readings by zone and atmospheric pollutant, as per the environmental standard NADF-009-AIRE-2017. Provided in CSV files named `indice_20XX.csv` for each year.
- **Method of Moments**: A method of estimation where population moments are equated to sample moments to solve for the parameters of the distribution.
- **Maximum Likelihood Estimation**: A method of estimation where the parameters are determined by maximizing the likelihood function.

---

## Theoretical Principles

- **Rayleigh Distribution**: A continuous probability distribution for positive-valued random variables.
- **Gamma Distribution**: A two-parameter family of continuous probability distributions.
- **Probability Density Function (pdf)**: A function that describes the likelihood of a random variable taking on a given value.
- **Log-Likelihood**: The natural logarithm of the likelihood function, used for parameter estimation in MLE.
- **Bhattacharyya Distance**: A measure of similarity between two probability distributions.
- **Digamma Function**: The logarithmic derivative of the gamma function, used in the derivation of MLE for the Gamma distribution.

---

## Conclusion

The Gamma distribution model (Gamma-MLE) consistently performed better than the Rayleigh distribution model (Rayleigh-MLE) across all zones, as determined by higher log-likelihood values and lower Bhattacharyya distances. This suggests that the Gamma distribution is more suitable for modeling AQI data in the Mexico City Metropolitan Area.
