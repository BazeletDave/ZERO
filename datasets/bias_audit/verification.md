# Verification Record

Version 0.1.0 | October 10, 2026

The supplied audit was executed against synthetic_pilot.jsonl. It reported 36 records in 18 scenarios, with 24 training, six validation, and six test records. Every split contains all three labels and both communication styles. The exact file digest is recorded in audit_report.json.

The verification script also confirmed that the audit rejects five deliberately introduced failures: scenario leakage across splits, an unsupported label, a missing policy, a duplicate record identifier, and inconsistent labels within a style pair. Python compilation succeeded. The original fixture was preserved during these checks.

Reproduce the checks from the repository root:

```bash
python datasets/bias_audit/verify_pilot.py
```

These results demonstrate the implemented integrity checks only. Human annotation, model training, model accuracy, fairness, semantic leakage review, and release approval have not been completed.
