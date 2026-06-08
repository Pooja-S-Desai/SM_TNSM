# SM_TNSM

# Congestion-Aware Routing-Based Dynamic Switch Migration for SDN Controller Load Balancing

This repository contains the implementation used for evaluating congestion-aware switch migration strategies for Software-Defined Networks (SDNs). The framework jointly considers controller load balancing, migration cost, response time, and routing feasibility during switch reassignment.

The repository compares the proposed optimization models against optimization-based and heuristic baselines across multiple network topologies and traffic scenarios.

## Algorithms Included

### 1. LB-MCF

LB-MCF (Load-Balancing Multi-Commodity Flow) is the proposed arc-based optimization model. It jointly optimizes switch migration, controller load balancing, and routing feasibility using a multi-commodity flow formulation over physical network links.

### 2. PB-MCF

PB-MCF (Path-Based Multi-Commodity Flow) is a path-oriented approximation of LB-MCF that restricts routing decisions to a predefined candidate path set, reducing optimization complexity while preserving congestion awareness.

### 3. SP

SP is a shortest-path-based migration approach that routes control traffic over shortest paths while performing controller reassignment.

### 4. B1

B1 is an optimization-based baseline that performs switch migration for controller load balancing while incorporating migration-related costs.

### 5. B2 / EASM

B2 corresponds to the Efficiency-Aware Switch Migration (EASM) heuristic. It performs migration decisions using controller load reduction and migration efficiency metrics without explicit congestion-aware routing constraints.

## Objective Functions

The framework supports five controller load-balancing objectives commonly used in SDN controller assignment and switch migration studies.

### B1 – Min-Max Utilization

Minimize the maximum controller utilization across all controllers.

### B2 – Min-Sum Utilization

Minimize the total controller utilization across the network.

### B3 – Min-Variance

Minimize the variance of controller loads to achieve a more uniform load distribution.

### B4 – Min-Deviation

Minimize the overall deviation of controller loads from the average controller load.

### B5 – Max-Min Difference

Minimize the difference between the most-loaded and least-loaded controller.

These objectives can be evaluated using all implemented algorithms:

- LB-MCF
- PB-MCF
- SP
- B1
- B2 (EASM)

allowing a comprehensive comparison of optimization-based and heuristic switch migration strategies under different load-balancing formulations.
These objectives can be evaluated using LB-MCF, PB-MCF, SP, B1, and B2 under different topology and traffic settings.

## Main Features

* Dynamic SDN switch migration
* Controller load balancing
* Congestion-aware routing
* Multi-commodity flow optimization
* Migration cost modeling
* Response-time-aware evaluation
* Controller capacity constraints
* Bandwidth feasibility constraints
* Comparative evaluation across multiple algorithms
* CSV-based result generation
* Automated figure generation

## Repository Structure

```text
.
├── data/                  # Input topology files
├── results/               # Generated experiment results
├── plots/                 # Output figures
├── src/                   # Source code
├── run_experiments.py     # Main experiment driver
├── plot_results.py        # Figure generation scripts
└── README.md
```

## Requirements

The code was developed and tested using:

* Python 3.x
* Gurobi Optimizer
* NumPy
* Pandas
* NetworkX
* Matplotlib

## Installation

Install the required Python packages:

```bash
pip install numpy pandas networkx matplotlib
```

## Note

Gurobi must be installed separately and a valid academic or commercial license must be activated before running the code.

## Running the Experiments

```bash
python run_experiments.py
```

The script generates experiment outputs and stores the results in the `results/` directory.

## Generating Figures

```bash
python plot_results.py
```

Generated figures are stored in the `plots/` directory.

## Output Metrics

Typical output metrics include:

* Initial controller load deviation
* Final controller load deviation
* Load-balancing improvement
* Number of migrated switches
* Migration cost
* Response time
* Maximum link utilization
* Congested links
* Solver runtime
* Feasibility status

## Reproducibility

Experiments use deterministic seeds wherever applicable. Runtime and optimization results may vary slightly depending on the Gurobi version, machine configuration, and solver settings.

## Citation

If you use this code in academic work, please cite the corresponding publication.
