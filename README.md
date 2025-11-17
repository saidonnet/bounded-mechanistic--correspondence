# Bounded Mechanistic Correspondence (BMC)

A framework and production-ready pipeline for bounded, falsifiable mechanistic interpretability. BMC reframes interpretability as hypothesis testing: find a low-dimensional Abstract Dynamical Model (ADM) for a Stable Computational Substrate (SCS), then adversarially test it. The framework focuses on four challenges: superposition resolution, context-dependent polysemanticity, attention flow tracing, and ground-truth validation.

## Key ideas

- Stable Computational Substrate (SCS): local, geometrically stable activation regions used as units of analysis.
- Abstract Dynamical Model (ADM): a low-dimensional surrogate model that predicts network behavior under interventions.
- Correspondence Criterion: ADMs must make adversarially testable predictions about external behavior to be considered valid.
- Contextual Dependency Score (CDS): quantifies how much local explanations depend on global context.

## What this repository contains

This repository collects the Bounded Mechanistic Correspondence (BMC) paper and accompanying implementation sketches and notes. The included material describes:

- The BMC conceptual framework and multi-tiered validation protocol (intrinsic, extrinsic, ground-truth, negative-control).
- Component sketches and pseudocode for: PCMCI-based causal discovery, distributed path-patching workers (Ray), hierarchical feature clustering (HDBSCAN), automated planted-circuit benchmarks, multi-context analysis, and a Gradio human-in-the-loop workbench.
- Experimental summaries and benchmarking results reported in the paper (GPT-2 scale tests and synthetic planted-circuit benchmarks).

## High-level workflow

1. Identify candidate SCSs by clustering activations (hierarchical clustering / HDBSCAN + topological regularization).
2. Generate candidate ADMs via causal discovery (PCMCI) and path-patching interventions.
3. Validate ADMs with the multi-tiered protocol: intrinsic hypothesis generation → extrinsic cross-model tests → ground-truth benchmarking → negative-control falsification.
4. Report Contextual Dependency Scores, uncertainty bounds, and adversarial test outcomes alongside any mechanistic claims.

## Reported results (paper highlights)

- Synthetic planted-circuit benchmarks: precision ~94%, recall ~87%, false positive rate ~6%.
- Superposition resolution (synthetic tests): hierarchical clustering + topological regularization achieved ~89% precision / 76% recall vs a Sparse Autoencoder baseline (~45% precision).
- Attention flow tracing on GPT-2: identified multiple statistically significant attention-mediated causal links (FDR-corrected p < 0.01) and associated heads with specific linguistic behaviors.
- Cross-seed generalization: ~73%; cross-architecture generalization: ~31% (suggesting some architecture-specific patterns).

## Limitations

- BMC performs bounded analyses; computational and combinatorial limits remain and require distributed computation and approximations.
- Causal discovery methods (e.g., PCMCI) make assumptions that may not fully hold in transformer dynamics; results are probabilistic, not guaranteed.
- Generalization of discovered circuits across architectures is imperfect; mechanistic claims should be reported with CDS and negative-control outcomes.

## How to use / reproduce

This repository contains conceptual and implementation sketches rather than a single installable package. To reproduce the pipeline, users should:

1. Prepare activation datasets from models of interest (e.g., GPT-2) across relevant contexts.
2. Run hierarchical clustering / HDBSCAN to identify candidate SCSs.
3. Apply PCMCI-based causal discovery and run path-patching interventions (distributed via Ray) to generate and verify ADMs.
4. Use the automated benchmark suite with synthetic planted circuits to calibrate precision/recall and run negative-control tests.

Detailed code examples and runnable scripts are provided in the repository files; consult the PDF and code sketches for component-level details.

## Citation

If you use these ideas or the code in research or projects, please cite:

Bounded Mechanistic Correspondence (BMC). saidonnet, 2024. (See PDF in this repository.)

## License

Add or confirm a LICENSE file for this repository. If no license is present, please contact the repository owner for reuse terms.

## Contact / Contributions

Open issues, PRs, and reproducibility reports are welcome. For questions about the BMC framework or experimental details, open an issue or contact the repository owner.
