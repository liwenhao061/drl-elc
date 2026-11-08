# DRL-ELC: Dynamic Route Choice with Information Refreshing

Public research companion for the manuscript:

**Dynamic Route Choice with Cognitive Updating and Information Delays: A Recursive Logit–HMM Model on a Time-Expanded Supernetwork**

> **Release status:** This repository currently contains only this README. The research source code will be released here after the manuscript is accepted for publication. No runnable implementation, installation package, or empirical dataset is included at this stage.

## Overview

Route choices depend on both traffic conditions and the information available to a traveller. This project studies sequential link choices when travellers may retain an earlier traffic snapshot, refresh their information during a trip, and deviate from the resulting plan.

The proposed **Dynamic Recursive Logit with En-route Learning and Choice (DRL-ELC)** combines recursive continuation values, a latent information-refreshing process, and an execution mixture. A hidden-state representation tracks the retained information snapshot and supports likelihood evaluation by forward recursion. The framework distinguishes the discount factor, information availability, snapshot retention, and execution behaviour rather than treating them as interchangeable mechanisms.

## Models

The research implementation covers the following model families and comparison specifications. Their descriptions below refer to the manuscript; code is not yet available in this public repository.

| Model | Main specification |
|---|---|
| **RL / BETA_RL** | Static recursive logit using time-averaged link costs, with undiscounted or discounted continuation values. |
| **DRL_CI / BETA_DRL_CI** | Current-information recursive logit; the traffic snapshot is refreshed at every decision. |
| **DRL_CQ** | A retained information snapshot with a constant probability of refreshing during the trip. |
| **DRL_EU** | A retained snapshot with a covariate-dependent refresh probability. |
| **DRL_ELC** | The refresh-and-retention model extended by a mixture of snapshot-plan choices and current myopic choices. |
| **INDEPENDENT_UPDATE** | An information-memory comparison that redraws current versus departure information at each decision instead of retaining the latest refresh. |
| **DRL_DI** | Delayed or periodically updated information under an externally specified timing rule. |
| **DRL_ORACLE / BETA_DRL_ORACLE** | Reference models with knowledge of the future traffic profile on a time-expanded network. |
| **MYOPIC_STATIC / MYOPIC_CI** | Immediate-utility choices using static or current costs, without continuation values. |
| **Path-MNL / Ref-PSL** | Path-based benchmarks over routes without repeated links; Ref-PSL uses path-size terms defined by a fixed reference set. |

Fixed and estimated discount factors, training penalties, and information assumptions are separate specification choices. Not every model is used in every experiment, and the comparisons do not assume a universal predictive advantage for the more elaborate models.

## Research scope

- **Synthetic experiments:** information timing, parameter recovery, and contrasts for refreshing, snapshot memory, and execution mixing.
- **Chengdu application:** parameter estimation and inference, observed-route probability scoring, route generation, and spatial link-usage comparisons.
- **Behavioural diagnostics:** destination arrival, cycles, finite-horizon truncation, and a local fixed-coefficient discount-factor contrast.
- **Computational comparisons:** clearly separated objective-and-gradient evaluation, estimation, and probability-scoring costs for recursive and path-based implementations.

Observed-route probability and generated-route similarity answer different questions. Truncated routes remain in the declared generation evaluation, and Monte Carlo precision and finite-pool approximation limits are retained for the path-based benchmarks. The empirical evaluation conditions on a reconstructed traffic field and includes historically inspected test folds; it is not presented as an untouched confirmatory test.

## Planned code release

After acceptance, the public release is planned to include:

- Model implementations, value-function solvers, latent-state likelihood routines, and estimation utilities.
- Synthetic-network examples and the scripts needed to run the reported model comparisons.
- Probability scoring, route generation, and diagnostic evaluation tools.
- Environment requirements, usage instructions, and documented experiment configurations.

The release will identify its version and software license. Empirical data availability will be documented separately and will depend on the source data's redistribution conditions; the planned code release does not imply that raw taxi trajectories can be redistributed.

This public repository is separate from the private development repository. Development history, credentials, and internal execution records are not part of this README-only release.

## Paper and citation

The manuscript is not yet accepted. Journal information, DOI, and a verified citation will be added when available. Please do not cite this placeholder repository as an already released software implementation.

## Contact

Maintainer: [liwenhao061](https://github.com/liwenhao061).

For questions about the forthcoming release, please open an issue in this repository.
