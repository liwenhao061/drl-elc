# DRL-ELC

Dynamic Recursive Logit with En-route Learning and Choice.

## Overview

DRL-ELC is a framework for sequential route choice in time-varying networks. It combines discounted recursive utilities, latent information refreshing, and a mixture of planned and myopic choices. A hidden-state representation tracks the most recently refreshed traffic snapshot and enables likelihood evaluation through forward recursion.

The Python implementation includes value-function solvers, latent-state inference, parameter estimation, route simulation, and predictive evaluation. Static, current-information, and path-based models provide comparison benchmarks.

## Models

| Model | Description |
|---|---|
| **RL / BETA_RL** | Static recursive logit with undiscounted or discounted continuation values. |
| **DRL_CI / BETA_DRL_CI** | Current-information recursive logit, refreshing the traffic snapshot at every decision. |
| **DRL_CQ** | Snapshot retention with a constant refresh probability. |
| **DRL_EU** | Snapshot retention with a covariate-dependent refresh probability. |
| **DRL_ELC** | Information refreshing and retention with a mixture of snapshot-plan and current myopic choices. |
| **INDEPENDENT_UPDATE** | Current versus departure information redrawn at each decision, without retaining the latest refresh. |
| **DRL_DI** | Delayed or periodically updated information under an externally specified timing rule. |
| **DRL_ORACLE / BETA_DRL_ORACLE** | Reference models with knowledge of the future traffic profile. |
| **MYOPIC_STATIC / MYOPIC_CI** | Immediate-utility choices using static or current costs. |
| **Path-MNL / Ref-PSL** | Path-based benchmarks over routes without repeated links; Ref-PSL uses a fixed reference set for path-size terms. |

## Code structure

Planned public-release layout, based on the current implementation:

```text
drl-elc/
├── src/recursive_logit_hmm/
│   ├── domain/          # Networks, trajectories, attributes, and specifications
│   ├── dynamics/        # Time-expanded network representation
│   ├── kernels/         # Value functions, choice kernels, and sensitivities
│   ├── models/          # Static, dynamic, and latent-information models
│   ├── inference/       # Likelihood, forward-backward inference, and estimation
│   ├── simulation/      # Stochastic route generation
│   ├── evaluation/      # Prediction metrics, ablation, and diagnostics
│   └── preprocessing/   # Network and trajectory preparation
├── experiments/
│   ├── braess/          # Synthetic-network experiments and recovery studies
│   ├── sec513/          # Mechanism ablation experiments
│   ├── chengdu/         # Empirical estimation and predictive evaluation
│   └── path_baselines/  # Path-MNL and Ref-PSL benchmarks
├── configs/             # Model and experiment configurations
├── examples/            # Usage examples
├── tests/               # Unit, integration, and regression tests
├── pyproject.toml       # Package metadata and dependencies
└── README.md
```

## Installation and usage

The implementation uses Python, NumPy, and SciPy, with additional dependencies for geospatial preprocessing and experiments. Installation instructions and runnable examples will accompany the source-code release.

## Code availability

Source code will be released in this repository after manuscript acceptance. Empirical data availability will be documented separately, subject to the source data's redistribution conditions.

## Citation

Publication details and a BibTeX entry will be added when available.

## License

The software license will be specified with the source-code release.
