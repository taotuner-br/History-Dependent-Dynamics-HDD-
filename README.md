# HDD — History-Dependent Dynamics

## A Methodological Framework for Disentangling History Dependence, Recurrence, Self-Reference, and Self-Modeling in Dynamical Systems

Author: Taotuner
DOI: https://doi.org/10.5281/zenodo.21955745

---

## Overview

**HDD (History-Dependent Dynamics)** is a falsifiable methodological framework for disentangling five inferential claims that are frequently conflated across disciplines:

1. **Construct I** — History-Dependent Predictive Structure
2. **Construct II** — Causally Demonstrated Trajectory Dependence
3. **Construct III** — Causally Identified Feedback Recurrence
4. **Construct IV** — Functional Self-Reference
5. **Construct V** — Self-Modeling

**The core thesis:**

> **Evidence that a system depends on its history should not automatically be interpreted as evidence for more specific forms of dynamical organization.**

Each construct requires its own experimental evidence. None implies the next. None implies consciousness.

---

## Repository Contents

```
hdd/
├── README.md                           # This file
├── LICENSE                             # CC BY 4.0
├── requirements.txt                    # Python dependencies
├── paper/
│   ├── History-Dependent_Dynamics_HDD.pdf    # Full manuscript
│   └── HDD_Benchmark_Appendix.pdf           # Benchmark appendix
├── benchmark/
│   ├── hdd_benchmark_v1.py             # Main benchmark script
│   ├── config.py                       # Pre-registered configuration
│   ├── generators.py                   # Synthetic system generators
│   ├── metrics.py                      # Statistical inference functions
│   └── run_benchmark.ipynb             # Interactive Colab notebook
├── results/
│   ├── HDD_Construct_I_full_results.csv
│   ├── HDD_Construct_I_main_results.csv
│   ├── capacity_control.csv
│   ├── state_reconstruction.csv
│   ├── noise_robustness.csv
│   ├── multi_seed_robustness.csv
│   ├── history_dependence_profile.png
│   ├── effect_size_profile.png
│   └── REPORT.txt
└── docs/
    └── api_reference.md                # Function documentation
```

---

## Key Results (Construct I Benchmark)

| System | HDD-I | Relative Improvement (τ=10) | 95% CI | p-value |
|--------|-------|-----------------------------|--------|---------|
| Markov | **−** | -0.012% | [-0.000006, 0.000003] | 0.711 |
| Hidden State | **+** | **+9.60%** | [0.002408, 0.002761] | < 0.001 |
| Delay Line | **+** | **+31.94%** | [0.004557, 0.004932] | < 0.001 |
| Recurrent | **+** | **+6.75%** | [0.001420, 0.001658] | < 0.001 |

**Accuracy against ground truth: 100%**

**Robustness:** 100% positive fraction across 5 random seeds for all non-Markov systems. Zero false positives for Markov.

---

## Installation

```bash
# Clone the repository
git clone https://github.com/taotuner/hdd.git
cd hdd

# Install dependencies
pip install -r requirements.txt
```

**Requirements:**
- Python 3.9+
- numpy >= 2.0.0
- pandas >= 2.2.0
- scikit-learn >= 1.6.0
- matplotlib >= 3.8.0

---

## Running the Benchmark

### Quick Start

```python
from hdd_benchmark_v1 import run_benchmark

# Run the full benchmark
results = run_benchmark()
```

### Interactive Notebook

Open `benchmark/run_benchmark.ipynb` in Google Colab or Jupyter for step-by-step execution.

### Command Line

```bash
python benchmark/hdd_benchmark_v1.py
```

### Configuration

All parameters are pre-registered in `config.py`:

```python
@dataclass
class Config:
    n_train_trajectories: int = 120
    n_test_trajectories: int = 60
    trajectory_length: int = 500
    burn_in: int = 100
    max_history: int = 10
    noise_std: float = 0.10
    history_windows: tuple = (1, 2, 3, 5, 10)
    robustness_seeds: tuple = (42, 123, 456, 789, 2026)
    noise_levels: tuple = (0.05, 0.10, 0.20, 0.30)
    # ... see config.py for full list
```

---

## Output Structure

After running the benchmark, the following files are generated:

| File | Description |
|------|-------------|
| `HDD_Construct_I_full_results.csv` | Complete results for all conditions |
| `HDD_Construct_I_main_results.csv` | Main results (τ=10, σ=0.10, seed=42) |
| `capacity_control.csv` | Real vs. placebo improvement comparison |
| `state_reconstruction.csv` | PCA diagnostic results |
| `noise_robustness.csv` | Results across noise levels |
| `multi_seed_robustness.csv` | Results across random seeds |
| `history_dependence_profile.png` | ΔL(τ) across history windows |
| `effect_size_profile.png` | Relative improvement vs. history horizon |
| `REPORT.txt` | Summary report with interpretation |
| `manifest.json` | Full configuration and metadata |

---

## Interpreting the Results

### Classification Criteria

| Symbol | Meaning |
|--------|---------|
| **+** | Positive evidence for the construct |
| **−** | Evidence against the construct |
| **UE** | Insufficient evidence / inconclusive |
| **NI** | Structurally not identifiable (not yet implemented) |
| **NT** | Not tested (not yet implemented) |

### What Positive Construct I Means

> A positive Construct I classification means **only** that historical information improved out-of-sample prediction relative to the specified observed present state and current input.

**It does NOT establish:**
- A memory mechanism
- Recurrence
- Self-reference
- Self-modeling
- Agency
- Consciousness

### The Hidden State Example

The Hidden State system is especially important: a positive result does **not** mean the system has explicit memory. History may simply reveal information about a latent variable. This illustrates the **observation-model problem** that HDD is designed to address.

---

## Limitations and Future Work

### What This Benchmark Validates

✅ Construct I — History-Dependent Predictive Structure

### What This Benchmark Does NOT Validate

❌ Construct II — Causal Trajectory Dependence
❌ Construct III — Feedback Recurrence
❌ Construct IV — Functional Self-Reference
❌ Construct V — Self-Modeling

**Validating Constructs II–V requires different experimental designs:** causal trajectory manipulations, feedback perturbations, self-reference comparisons with matched-content controls, and counterfactual self-model tests.

---

## References

- **Main Paper:** Taotuner. (2026). History-Dependent Dynamics (HDD): A Methodological Framework for Disentangling History Dependence, Recurrence, Self-Reference, and Self-Modeling in Dynamical Systems.
- **Appendix:** Taotuner. (2026). Computational Benchmark — Construct I: Full Protocol Details, Extended Results, and Source Code.
- **Related Work:** Taotuner. (2026). Informational-Processual Monism: A simulation-grounded fallibilist ontology. Zenodo. https://doi.org/10.5281/zenodo.19655115

---

## License

This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

**You are free to:**
- Share — copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material for any purpose

**Under the following terms:**
- Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made.

---

## Citation

If you use this framework or code in your research, please cite.

---

## Acknowledgments

This work was developed with the assistance of AI-based language tools used for literature exploration, structural organization, drafting, critical discussion, methodological critique, and language refinement. All conceptual decisions, methodological commitments, interpretation of evidence, revisions, and responsibility for the final work remain with the author.

---

**Version:** 1.0
**Date:** August 2026
