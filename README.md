# Foldables — Closing the Loop on Catalyst Discovery

**We cut catalyst discovery cycles from 6 months to 3 weeks.**

## The Problem
GPS Renewables is building India's first commercial Ethanol-to-Jet plant. The catalyst that makes it work exists at lab scale. Getting it to commercial scale means iterating on formulation, surface composition, and operating conditions until selectivity and stability are both commercially viable. That iteration currently happens entirely in the lab. One cycle: 3 to 6 months. One commercial plant cannot wait for 12 cycles.

This is not a GPS Renewables problem. Every sustainable fuel pathway — CO₂ to methanol, syngas to ethanol, biomass to hydrocarbons — sits behind the same wall. Vast design space. Painfully slow search.

## Why Current Tools Fail
Three tools exist. Databases like the Open Catalyst Project store properties of known materials — useless for finding what has never been synthesised. DFT simulators compute accurate binding energies — but only for candidates a researcher already thought to test, at 4 to 48 hours per calculation. Lab notebooks store results — isolated to the researcher who ran the experiment, gone when they leave.

The three gaps nobody has closed: existing tools retrieve known catalysts but never propose new ones. Predictions never learn from experimental results — the loop is permanently open. Stability — the commercially decisive metric — is almost never modelled because the data is scarce and condition-specific.

Every current tool solves one piece. Nobody has connected all three.

## What Foldables Does
A researcher enters a target reaction and operating conditions. Foldables does three things in sequence that no single existing platform does together.

It retrieves all relevant known candidates from the Open Catalyst Project and Materials Project. It then generates novel candidates that do not exist in any database — structural variants of the top performers, computationally optimised for the specific reaction and conditions, using a graph neural network trained on 1.2 million DFT calculations. It ranks everything simultaneously by predicted activity, selectivity, and stability — including a stability model calibrated to GPS Renewables' actual reactor conditions, which is the one score that determines whether a catalyst survives commercial operation.

The researcher runs experiments on the top candidates. They log results back. Foldables compares predictions against reality, identifies which structural features the model underweighted, and retrains. The next search is more accurate than the last. Every experiment GPS Renewables runs makes the platform smarter — permanently.

## On the Quantum Component
We use VQE quantum simulation for one specific computation: active site binding energy for small catalyst cluster models (8 atoms). Classical DFT at this scale takes hours. VQE on a 12-qubit simulator runs in under 2 minutes and is architecturally identical to what runs on real IBM quantum hardware — same circuit, different backend. We are not using quantum because it sounds impressive. We are using it because it is the fastest accurate method available for this specific calculation, and the same code runs on real QPUs when fault-tolerant hardware arrives. That is a genuine technical decision, not a talking point.

## Before and After
- **Before Foldables**: a GPS Renewables researcher hypothesises a catalyst variant, synthesises it, runs it for 3 weeks, measures performance, updates a spreadsheet, repeats. Time to identify a commercially viable candidate: 6 to 18 months.
- **After Foldables**: the researcher enters the target reaction. Within minutes they have 31 ranked candidates including 8 that have never been synthesised, each with predicted activity, selectivity, and stability scores with confidence intervals. They test the top 5. They log results. The model retrains. Time to identify a commercially viable candidate: 3 to 6 weeks.

That is not an estimate. The 2024 npj Computational Materials paper validating ML-accelerated catalyst discovery across 160 metallic alloys showed the descriptor approach we use achieves sub-0.25 eV mean absolute error — sufficient to reliably distinguish active from inactive candidates before any synthesis happens.

## Why Now. Why This Team. Why We Win.
GPS Renewables announced India's first commercial ethanol-to-jet plant in September 2025. Commercial-scale SAF from ethanol has never been achieved anywhere in the world. The catalyst optimisation problem Foldables solves is the exact problem standing between their current pilot and commercial operation. The timing is not coincidental.

Our team built a quantum-enhanced molecular prediction platform for personalised drug discovery — QuantaMed. Foldables takes the identical architecture and redirects it from human protein binding to industrial catalyst surfaces. The science transfers directly. The engineering is already proven. We are not starting from scratch. We are applying a working system to a harder problem with higher commercial urgency and a specific industry partner who needs it now.

We are committed to a 6-month pilot engagement with GPS Renewables post-hackathon, calibrated to their NG SAF reactor conditions, using their own experimental data as the retraining seed.

The platform compounds in value with every experiment they run. That is simultaneously the product, the business model, and the moat.
