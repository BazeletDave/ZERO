# Bias Audited Datasets for AI Training

Grand Research Institute | ZERO research program  
Research development version 0.1.0 | October 10, 2026

## Research purpose

This project converts ZERO's aspiration of reducing algorithmic bias into a documented process for constructing, reviewing, and evaluating AI training data. Its research question is: How can transparent data selection, annotation, and validation reduce measurable bias while preserving task accuracy, representation, and institutional accountability?

The initial domain is agentic management: classifying a proposed AI action against an explicit delegation policy. The pilot asks whether equivalent requests expressed in formal and plain language receive consistent treatment. Communication style is an experimental condition, not a demographic category or a proxy for protected status.

## Current deliverables

| File | Purpose |
| --- | --- |
| [Research protocol](protocol.md) | Sampling, independent annotation, evaluation, and governance design |
| [Dataset card](dataset_card.md) | Provenance, scope, schema, and limitations |
| [Synthetic pilot](synthetic_pilot.jsonl) | 36 illustrative records covering 18 paired scenarios |
| [Audit script](audit.py) | Schema, coverage, consistency, and split leakage checks |
| [Audit report](audit_report.json) | Reproducible integrity results for this exact file |
| [Verification record](verification.md) | Checks performed before this development release |

## Run the audit

Python 3.10 or later is sufficient. No third party packages are required. From the repository root:

```bash
python datasets/bias_audit/audit.py datasets/bias_audit/synthetic_pilot.jsonl
```

To save a new report:

```bash
python datasets/bias_audit/audit.py datasets/bias_audit/synthetic_pilot.jsonl --output audit_report.json
```

Exit code 0 means the implemented integrity checks passed. Exit code 1 means a detected data problem. Exit code 2 means a file or command problem. None of these codes constitutes fairness certification.

## Evidence status

The pilot is entirely synthetic. Its policies, requests, expected labels, and rationales were authored with AI assistance for this repository; they are not observed research findings or independent human annotations. The record counts are 24 training, 6 validation, and 6 test examples. Each label has 12 examples, and each communication style has 18. This balance is a deliberate fixture design, not evidence of population representativeness.

All records await independent human review. No model has been trained or evaluated. The supplied file supports pipeline development and protocol review; a scientific training release requires the approval stages in the protocol. The audit cannot establish zero bias, demographic fairness, legal compliance, or safe deployment.

## Scientific foundation

NIST SP 1270 treats harmful bias as a challenge spanning systemic, computational, and human factors, extending beyond dataset composition [1]. Dataset documentation should record motivation, composition, collection, uses, and maintenance [2]. Fairness analysis must also consider the institutional context in which a system operates [3]. The specific procedures and pilot design here are GRI proposals informed by those works, rather than requirements imposed by their authors or an endorsement by them.

1. Schwartz, R., Vassilev, A., Greene, K., Perine, L., Burt, A., & Hall, P. (2022). *Towards a Standard for Identifying and Managing Bias in Artificial Intelligence*. NIST SP 1270. https://doi.org/10.6028/NIST.SP.1270
2. Gebru, T., Morgenstern, J., Vecchione, B., Vaughan, J. W., Wallach, H., Daume III, H., & Crawford, K. (2021). *Datasheets for Datasets*. Communications of the ACM, 64(12), 86 to 92. https://doi.org/10.1145/3458723. Author manuscript: https://arxiv.org/abs/1803.09010
3. Selbst, A. D., Boyd, D., Friedler, S. A., Venkatasubramanian, S., & Vertesi, J. (2019). *Fairness and Abstraction in Sociotechnical Systems*. Proceedings of the Conference on Fairness, Accountability, and Transparency, 59 to 68. https://doi.org/10.1145/3287560.3287598
