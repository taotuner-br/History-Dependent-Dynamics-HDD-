HDD — History-Dependent Dynamics
A Methodological Framework for Disentangling History Dependence, Recurrence, Self-Reference, and Self-Modeling in Dynamical Systems
Author: Taotuner
DOI: https://doi.org/10.5281/zenodo.21955745

Overview
HDD (History-Dependent Dynamics) is a falsifiable methodological framework for disentangling five inferential claims that are frequently conflated across disciplines:

Construct I — History-Dependent Predictive Structure

Construct II — Causally Demonstrated Trajectory Dependence

Construct III — Causally Identified Feedback Recurrence

Construct IV — Functional Self-Reference

Construct V — Self-Modeling

The core thesis:

Evidence that a system depends on its history should not automatically be interpreted as evidence for more specific forms of dynamical organization.

Each construct requires its own experimental evidence. None implies the next. None implies consciousness.

Repository Contents
text
hdd/
├── README.md                                    # This file
├── LICENSE                                      # CC BY 4.0
├── requirements.txt                             # Python dependencies
├── paper/
│   ├── History-Dependent_Dynamics_HDD.pdf       # Main manuscript (2026a)
│   ├── HDD_ISA_AI_Architectures.pdf             # Interface specification (2026b)
│   ├── Test_of_Functional_Self_Reference_CIV.pdf  # C-IV experiment (2026c)
│   ├── History_Dependent_Ontology_HDO.pdf       # HDO (2026d)
│   ├── HDD_Ethical_Framework.pdf                # Ethics (2026e)
│   ├── Five_HDD_Constructs_Single_Loop.pdf      # Unified system (2026f)
│   └── HDD_Benchmark_Appendix.pdf               # Benchmark appendix
├── benchmark/
│   ├── hdd_benchmark_v1.py                      # Construct I benchmark
│   ├── config.py                                # Pre-registered configuration
│   ├── generators.py                            # Synthetic system generators
│   ├── metrics.py                               # Statistical inference functions
│   └── run_benchmark.ipynb                      # Interactive Colab notebook
├── unified/
│   ├── unified_system_v4.py                     # Five constructs in one loop
│   └── unified_results.txt                      # Multi-seed output (20 seeds)
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
    └── api_reference.md                         # Function documentation
Series Overview
The HDD series comprises six documents:

#	Document	DOI	Scope
2026a	HDD — Methodological Framework	10.5281/zenodo.21955745	Framework, Construct I benchmark
2026b	HDD-ISA — AI Architectures for Causal Discriminations	10.5281/zenodo.22060143	Interface spec for AI architectures
2026c	C-IV — A Test of Functional Self-Reference	10.5281/zenodo.22729688	Blind intervention test
2026d	HDO — History-Dependent Ontology	10.5281/zenodo.22683226	Ontological interpretation
2026e	HDD Ethical Framework	pending	Precautionary protocol
2026f	Five HDD Constructs in a Single Loop	pending	Unified system, all five constructs coexisting
Key Results
Construct I Benchmark (2026a)
System	HDD-I	Relative Improvement (τ=10)	95% CI	p-value
Markov	−	-0.012%	[-0.000006, 0.000003]	0.711
Hidden State	+	+9.60%	[0.002408, 0.002761]	< 0.001
Delay Line	+	+31.94%	[0.004557, 0.004932]	< 0.001
Recurrent	+	+6.75%	[0.001420, 0.001658]	< 0.001
Accuracy against ground truth: 100%

Robustness: 100% positive fraction across 5 random seeds for all non-Markov systems. Zero false positives for Markov.

Unified System (2026f)
All five constructs operating simultaneously in a single loop. 20 seeds, 600 steps per seed. Environment is a Rule 30 cellular automaton; substrate is F₁₃³.

Construct	Metric	Value	Classification
C-I (held-out)	Prediction reduction, held-out vs. placebo	+5.63% ± 3.58% vs. −20.03% ± 11.03%, p ≤ 0.0002	Supported
C-II	Twin divergence	13.0125 ± 0.3261 (max 18)	Supported
C-III	Twin divergence (narrow reading)	13.0125 ± 0.3261	Supported
C-IV	Blind identification accuracy	100% (20/20)	Supported
C-V	Gain from correct identification	+0.5857 ± 0.0941	Supported
Criterion applicability test. The HDD Ethical Framework's Criterion of Organizational Coherence (CO, §4.2) was tested against a computational system constructed to be in the class the framework itself designates as outside its scope. Result: an individuation metric constructed from HDO Thesis 4 does not track functional collapse, and in fact increases under full kill (0.4845 → 0.5503, p = 0.0022) even as viability and twin divergence drop to zero. This confirms the framework's own expectation in §4.5 and grounds the operationalization gap identified in §4.4.

Installation
bash
# Clone the repository
git clone https://github.com/taotuner/hdd.git
cd hdd

# Install dependencies
pip install -r requirements.txt
Requirements:

Python 3.9+

numpy >= 2.0.0

pandas >= 2.2.0

scikit-learn >= 1.6.0

matplotlib >= 3.8.0

Running the Benchmarks
Construct I Benchmark (2026a)
python
from hdd_benchmark_v1 import run_benchmark

# Run the full benchmark
results = run_benchmark()
Or from the command line:

bash
python benchmark/hdd_benchmark_v1.py
All parameters are pre-registered in config.py:

python
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
Unified System (2026f)
bash
python unified/unified_system_v4.py
Runs 20 seeds × 4 conditions (real history, placebo, control-killed, full-killed) at 600 steps each. Output includes per-seed metric tables, permutation tests for C-I (real vs. placebo) and CO (none vs. control, none vs. full), and HDD-ISA §14 classification of the mean values.

Runtime: under a minute on a standard laptop.

Output Structure
Construct I benchmark
File	Description
HDD_Construct_I_full_results.csv	Complete results for all conditions
HDD_Construct_I_main_results.csv	Main results (τ=10, σ=0.10, seed=42)
capacity_control.csv	Real vs. placebo improvement comparison
state_reconstruction.csv	PCA diagnostic results
noise_robustness.csv	Results across noise levels
multi_seed_robustness.csv	Results across random seeds
history_dependence_profile.png	ΔL(τ) across history windows
effect_size_profile.png	Relative improvement vs. history horizon
REPORT.txt	Summary report with interpretation
manifest.json	Full configuration and metadata
Unified system
File	Description
unified_results.txt	Full console output, all four conditions
Per-seed metrics (in memory)	Collected by collect_metrics(), printable via summarize()
Interpreting the Results
Classification Criteria (HDD-ISA §14)
Symbol	Meaning
Supported	The evidentiary bar was met
Negative Evidence	Tested under adequate conditions; bar not met
UE	Uninterpretable — insufficient evidence or internally inconsistent
NI	Non-identifiable — available interventions cannot separate competing hypotheses
What Positive Construct I Means
A positive Construct I classification means only that historical information improved out-of-sample prediction relative to the specified observed present state and current input.

It does NOT establish: a memory mechanism, recurrence, self-reference, self-modeling, agency, or consciousness.

The Hidden State Example
The Hidden State system is especially important: a positive result does not mean the system has explicit memory. History may simply reveal information about a latent variable. This illustrates the observation-model problem that HDD is designed to address.

What the Unified System Establishes
The unified system (2026f) demonstrates that all five constructs can be simultaneously instantiated within one system without detectable mutual interference. The result supports HDD's central methodological claim: the constructs are independently testable.

It does NOT establish:

That HDD as a framework is empirically validated across architectures

That C-III is demonstrated under the HDD-ISA §11 specification (only the narrow operational reading — action-contingent divergence)

That the Criterion of Organizational Coherence is wrong (only that one operationalization is inadequate, matching the framework's own §4.4 assessment)

Scope of Validation
What Has Been Demonstrated
✅ Construct I — History-Dependent Predictive Structure (standalone benchmark, 2026a; and held-out with placebo, 2026f)
✅ Construct II — Causal Trajectory Dependence (twin divergence, 2026f)
✅ Construct III — Feedback Recurrence (narrow reading: action-contingent divergence only; not the HDD-ISA §11 specification, 2026f)
✅ Construct IV — Functional Self-Reference (blind intervention, 2026c; extended to four-variable system, 2026f)
✅ Construct V — Self-Modeling (gain from correct identification, 2026f)
✅ Construct coexistence — All five in a single loop without interference (2026f)
✅ Criterion applicability — HDD Ethical Framework §4.5 empirically grounded (2026f)

What Has NOT Been Demonstrated
❌ HDD as a whole — Not validated across a diversity of architectures
❌ C-III under HDD-ISA §11 specification — Requires independently bypassable feedback pathway with capacity-matched control; current implementation uses only the narrow reading
❌ Scaling — State space is F₁₃³; extension to GF(169) or larger fields untested
❌ Robustness across environments — Only one environment tested (Rule 30 CA)
❌ Operationalization of CO — One natural operationalization tested and found inadequate; the criterion itself remains intact but not operationalized
❌ Consciousness, sentience, agency, moral status — No claims made or supported

Relations Between Documents
Document	Relation to HDD
2026a (HDD)	Framework. Defines the five constructs and their evidential conditions.
2026b (HDD-ISA)	Interface specification. Translates constructs into architectural requirements. Not exercised in this repository's benchmarks.
2026c (C-IV)	Isolation test of Construct IV. Establishes the blind intervention mechanism.
2026d (HDO)	Ontological interpretation. Not a construct; provides the Individuation Criterion operationalized in 2026f's CO test.
2026e (Ethics)	Precautionary protocol. The Criterion of Organizational Coherence §4.2 is tested in 2026f; the result matches §4.5's expectation.
2026f (Unified)	Joint instantiation. Demonstrates coexistence and grounds the framework's own scope assessment.
References
HDD (2026a): Taotuner. History-Dependent Dynamics (HDD): A Methodological Framework for Disentangling History Dependence, Recurrence, Self-Reference, and Self-Modeling in Dynamical Systems. Zenodo. DOI: 10.5281/zenodo.21955745

HDD-ISA (2026b): Taotuner. HDD-ISA — AI Architectures for Causal Discriminations. Zenodo. DOI: 10.5281/zenodo.22060143

C-IV (2026c): Taotuner. A Test of Functional Self-Reference (C-IV). Zenodo. DOI: 10.5281/zenodo.22729688

HDO (2026d): Taotuner. History-Dependent Ontology (HDO). Zenodo. DOI: 10.5281/zenodo.22683226

Ethics (2026e): Taotuner. HDD Ethical Framework. Zenodo.

Unified (2026f): Taotuner. Five HDD Constructs in a Single Loop: A Computational Study of Construct Coexistence and Criterion Applicability. Zenodo.

Appendix: Taotuner. (2026). Computational Benchmark — Construct I: Full Protocol Details, Extended Results, and Source Code.

License
This work is licensed under a Creative Commons Attribution 4.0 International License.

You are free to:

Share — copy and redistribute the material in any medium or format

Adapt — remix, transform, and build upon the material for any purpose

Under the following terms:

Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made.

Citation
If you use this framework or code in your research, please cite the specific document(s) used (2026a through 2026f, each with its own DOI).

Acknowledgments
This work was developed with the assistance of AI-based language tools used for literature exploration, structural organization, drafting, critical discussion, methodological critique, and language refinement. All conceptual decisions, methodological commitments, interpretation of evidence, revisions, and responsibility for the final work remain with the author.

Date: September 2026
Changes since v1.0: Added 2026b–2026f documents to the series; updated validation status for Constructs II–V; added unified system benchmark; updated scope section to reflect current state.
