---
title: Package Padé
---

<!-- badges: start -->
[![CRAN Latest Version & Release](https://www.r-pkg.org/badges/version-last-release/Pade)](https://CRAN.R-project.org/package=Pade)
[![](http://cranlogs.r-pkg.org/badges/last-month/Pade)](https://cran.r-project.org/package=Pade)
[![](http://cranlogs.r-pkg.org/badges/grand-total/Pade)](https://cran.r-project.org/package=Pade)
[![R-CMD-check](https://github.com/aadler/Pade/workflows/R-CMD-check/badge.svg)](https://github.com/aadler/Pade/actions)
[![Codecov test coverage](https://codecov.io/gh/aadler/Pade/graph/badge.svg?token=471DIW465K)](https://app.codecov.io/gh/aadler/Pade)
[![OpenSSF Best Practices](https://bestpractices.coreinfrastructure.org/projects/2033/badge)](https://bestpractices.coreinfrastructure.org/projects/2033)
<!-- badges: end -->

## Mathematics
### Introduction
For a given function, its
[Taylor series](https://en.wikipedia.org/wiki/Taylor_series) is the "best"
polynomial representations of that function. If the function is being evaluated
at 0, the Taylor series representation is also called the Maclaurin series. The
error is proportional to the first "left-off" term. Also, the series is only a
good estimate in a small radius around the point for which it is calculated
(e.g. 0 for a Maclaurin series).

Padé approximants estimate functions as the quotient of two polynomials.
Specifically, given a Taylor series expansion of a function \(T(x)\) of order
\(L + M\), there are two polynomials, \(P_L(x)\) of order \(L\) and \(Q_M(x)\)
of order \(M\), such that \(\frac{P_L(x)}{Q_M(x)}\), called the Padé approximant
of order \([L/M]\), "agrees" with the original function in order \(L + M\).
More precisely, given

\begin{equation}
A(x) = \sum_{j=0}^\infty a_j x^j 
\end{equation}

the Padé approximant of order \([L/M]\) to \(A(x)\) has the property that

\begin{equation}
A(x) - \frac{P_L(x)}{Q_M(x)} = \mathcal{O}\left(x^{L + M + 1}\right) 
\end{equation}

The Padé approximant consistently has a wider radius of convergence than its
parent Taylor series, often converging where the Taylor series does not. This
makes it very suitable for numerical computation.

### Calculation
With the normalization that the first term of \(Q(x)\) is always 1, there is a
set of linear equations which will generate the unique Padé approximant
coefficients. Letting \(a_n\) be the coefficients for the Taylor series,
one can solve:

\[
\begin{align}
&a_0 &= p_0\\
&a_1 + a_0q_1 &= p_1\\
&a_2 + a_1q_1 + a_0q_2 &= p_2\\
&a_3 + a_2q_1 + a_1q_2 + a_0q_3 &= p_3\\
&a_4 + a_3q_1 + a_2q_2 + a_1q_3 + a_0q_4 &= p_4\\
&\vdots&\vdots\\
&a_{L+M} + a_{L+M-1}q_1 + \ldots + a_0q_{L+M} &= p_{L+M}
\end{align} 
\]

remembering that all \(p_k, k > L\) and \(q_k, k > M\) are 0.

### Function Input and Output
Given integers `L` and `M`, and vector `A`, a vector of Taylor series
coefficients, in increasing order and length at least `L + M + 1`, the `Pade`
function returns a list of two elements, `Px` and `Qx`, which are the
coefficients of the Padé approximant numerator and denominator respectively,
in increasing order.

## Citation
If you use the package, please cite it per
[CITATION](https://CRAN.R-project.org/package=Pade/citation.html).

## Contributions
Please see
[CONTRIBUTING.md](https://github.com/aadler/Pade/blob/master/CONTRIBUTING.md).

## Roadmap
### Major

 * There are no plans for major changes at this time
 
### Minor
 
 * There are no plans for minor changes at this time

## Security
Please see
[SECURITY.md](https://github.com/aadler/Pade/blob/master/SECURITY.md).
