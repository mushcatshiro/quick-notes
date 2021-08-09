# surrogate modelling

an affordable approach to address expensive simulation process. its a subset of supervised learning which reduce simulation (including defining physical properties) into a simple mapping problem. the general approach to build the surrogate model is to collect a set of carefully curated dataset with DOE and continuously improving the model through active learning. supposed there is a search algorithm to determined what is the next most-valuable experiment parameter set to further improve the model. model can be further validated by benchmarking against virtual/actual data and uncertainty quantification analysis (eg. monte carlo).

## clarifications

- latent variable?
- sample size
  - addressed by choosing the correct model?
- dataset credibility
- different correlation between parameters (eg a mix betweeen linear and polynomial)?
- how and how well the model adopts when new parameters is introduced

## advanced surrogate modelling

### gradient-enhanced surrogate models

instead of having just `(x, f(x))`, expand it into `(x, f(x), df(x)/dx)`. this allows achieving higher accuracy with lesser samples and better extrapolation?

#### challenges

- data explosion
  - data increase exponentially, assume n is the number of parameters and m is the number of samples, the total data grows in the fashion of `m + nm`.
- high-order derivatives induced data explosion
  - if n = 2, first order will yield 2 terms and second order will yield 5 terms

### multi-fidelity surrogate models

using lots of low-fidelity models (provides a coarse resolution at faster runtime) and a few high-fidelity models (provides a fine resolution at slower runtime)to improve performance.

### active learning

a search space usually is not evenly distributed and not equivalently important, regions that distincts itself worth spending resources to explore. a learning function is meant to figure out these regions where predictions are inaccurate. one of the example learning function is expected prediction error which allocates the next training sample to the location where the model is expected to have the largest prediction error. its similar to ML's bias-variance decomposition.

## reference matetials

- An adaptive sampling approach for Kriging metamodeling by maximizing expected prediction error
- Engineering Design via Surrogate Modelling: A Practical Guide
- A Python surrogate modeling framework with derivatives
- https://github.com/SMTorg/smt
