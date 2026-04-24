# Foldables — AI Platform for Molecular Discovery in Chemical Catalysis and Synthetic Biology
## Submission for Theme 4 | GPS Renewables Hackathon

### SECTION 1 — UNDERSTANDING THE PROBLEM
**The Real Bottleneck Is Not Science. It Is Time.**
Ninety percent of all industrial chemical processes involve catalysis at some stage. Yet the dominant method for discovering new catalysts in 2025 is still the same one used in 1950: a researcher picks a hypothesis, synthesises a material, runs it in a reactor, measures the output, and tries again. A single catalyst screening campaign — from hypothesis to validated candidate — can take three to six months of bench time and consume tens of thousands of dollars in materials, energy, and researcher hours, with no statistical guarantee of reaching a viable result.

The ACS journal paper published in 2024 titled "A Machine Learning and Explainable AI Framework Tailored for Unbalanced Experimental Catalyst Discovery" describes this directly: the design of novel catalysts has long relied on trial-and-error, a costly and labour-intensive process that results in scarce data heavily biased toward undesired, low-yield catalysts. The data scarcity problem is self-reinforcing — because failed experiments are rarely published, the field continuously rediscovers the same dead ends.

For GPS Renewables, this is not an academic concern. The company has committed to building India's first commercial-scale Ethanol-to-Jet plant under its NG SAF brand, in collaboration with CSIR-NCL and their patented oligomerisation catalyst. The CSIR-NCL catalyst works at laboratory scale. Getting it from laboratory to commercial operation requires iterative optimisation of catalyst formulation, reaction conditions, selectivity, and long-term stability — all of which are currently done through experimental iteration. Every week of iteration is a week of delay in a market where SAF demand is doubling annually and India's blending mandates are hardening.

### SECTION 2 — TEAM AND SUBJECT MATTER EXPERTISE
Foldables is built at the intersection of three disciplines that rarely share a codebase: quantum chemistry, machine learning, and process engineering. Our team brings together:
- A computational chemist with experience in DFT calculations and molecular descriptor design.
- A chemical process engineer familiar with reactor design for heterogeneous catalysis (Cu-ZnO-Al₂O₃).
- A bioinformatician with experience in metabolic flux analysis and protein structure prediction (AlphaFold2).
- A full-stack machine learning engineer (model architecture, retraining pipelines).
- A data scientist with experience in active learning and Bayesian optimisation.

### SECTION 3 — SYSTEM ARCHITECTURE
**The End-to-End Discovery Workflow**
The Foldables platform implements a closed-loop discovery workflow structured in six stages:
1. **Target Reaction Entry**: reactant/product specs and operating conditions.
2. **Database Retrieval**: ingestion from Open Catalyst Project (OCP), Materials Project, BRENDA, and PubChem.
3. **Generative AI Design**: GNN-based generative model (EquiformerV2) for novel surface compositions.
4. **Predictive Ranking**: Scoring by Activity (TOF), Selectivity (yield), and Stability (lifetime).
5. **Visualisation and Export**: Interactive 3D molecular viewer and reaction energy profiles.
6. **Experimental Feedback and Retraining**: Retraining the model on real bench results to close the loop.

### SECTION 4 — DATA LAYER
Foldables synchronises with five primary data sources:
- **OCP Dataset**: 1.2M DFT calculations.
- **Materials Project**: 140k+ inorganic materials.
- **BRENDA**: 80k+ enzyme characterisations.
- **NIST Kinetics**: Reaction rate constants.
- **GPS Renewables Internal Log**: Proprietary experimental data (isolated tenant partition).

### SECTION 5 — AI AND ML LAYER
- **EquiformerV2 GNN**: Predicts adsorption energies for intermediates.
- **XGBoost Selectivity Model**: Trained on experimental selectivity data.
- **Cox Proportional Hazard Stability Model**: Predicts catalyst deactivation as a time-to-event problem.
- **Quantum Integration**: Variational Quantum Eigensolver (VQE) on Qiskit Aer for active site binding energy clusters.

### SECTION 6 — SIMULATION LAYER
- **Reaction Energy Profiles**: Visualising the pathway from reactants to products via BEP scaling relations.
- **Metabolic Flux Analysis**: COBRApy-based MFA for synthetic biology pathways.

### SECTION 7 — DATA FEEDBACK LOOPS
The feedback loop operates at three levels:
1. **Prediction Correction**: Residual analysis of experimental vs. predicted performance.
2. **Model Retraining**: Automated retraining every 50 new experimental entries.
3. **Hypothesis Generation**: Surfaces structural features correlating with systematic errors (e.g., ZnO loading).

### SECTION 8 — USER INTERFACE AND COLLABORATION
- **Multi-User Collaboration**: Versioned history of every query and experimental result.
- **Lab Integration**: API connectors for ELNs (Benchling/LabArchives) and LIMS.
- **Instrument Connector**: Direct parsing of GC-MS/GC-FID output files.

### SECTION 9 — TECHNOLOGY CHOICES
| Component | Technology | Justification |
|---|---|---|
| Catalyst GNN | EquiformerV2 | State of the art on OCP benchmarks |
| Enzyme Generator | ESM-3 | Best zero-shot mutation prediction |
| Selectivity | XGBoost | Interpretable and fast for small experimental sets |
| Quantum | VQE (Qiskit) | Fastest accurate method for binding clusters |

### SECTION 10 — VALIDATION
Validated by 2024/2025 research:
- Adsorption energy distribution descriptor (npj Comp Mat 2025).
- Unbalanced experimental discovery ML framework (J. Phys. Chem. C 2024).
- Gevo/ORNL licensing of Ethanol-to-Jet catalysts (2025).

### SECTION 11 — ROADMAP
- **Hackathon Prototype**: End-to-end loop for Ethanol-to-Jet.
- **Pilot (Months 1-6)**: Deployment within GPS Renewables for NG SAF optimization.
- **Full Platform (Months 6-18)**: CO₂-to-Methanol and Syngas-to-Ethanol expansion.

### SECTION 12 — PILOT ENGAGEMENT
We confirm willingness for a 6-month pilot with GPS Renewables, focusing on the NG SAF ethanol-to-jet catalyst optimization programme.

### SECTION 13 — THE CORE CLAIM
The problem of catalyst discovery is a **workflow problem**. Foldables connects databases, generative AI, and real experiments into a single closed loop. We unfold the search space and fold experimental knowledge back in.
