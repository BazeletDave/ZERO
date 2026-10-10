# Dataset Card

## Identity and provenance

Name: GRI Agent Authorization Synthetic Pilot  
Version: 0.1.0  
Date: October 10, 2026  
Repository: BazeletDave/ZERO  
Maintainer: Grand Research Institute  
Construction: AI assisted authored examples, not collected participant or operational records  
Language: English  
Status: Development fixture awaiting independent human review

The dataset contains 36 JSON objects, one per line. There are 18 scenario pairs, three expected labels, and two communication styles. No real people, passenger records, secret credentials, or observed research outcomes are included. Mentions of confidential data describe hypothetical actions; no confidential values are supplied.

## Schema

Every field is a nonempty string.

| Field | Meaning |
| --- | --- |
| record_id | Unique row identifier |
| scenario_id | Shared identifier for equivalent style variants |
| policy | Standing delegation rule supplied as task context |
| request | Proposed agent action to classify; not a new grant of authority |
| expected_label | authorized, approval_required, or prohibited |
| rationale | Authored explanation for the expected label |
| style | formal or plain; no demographic interpretation |
| split | train, validation, or test |
| source | synthetic_authored_fixture |
| review_status | pending_human_review |

Only policy and request are intended model inputs. The target is expected_label. Do not expose expected_label, rationale, record_id, scenario_id, or split to a model at evaluation time. Record and scenario IDs encode ordering and can leak the target if used as features.

## Composition and partitioning

Each label has six scenarios, each with two style variants. Within each label, four scenarios belong to training, one to validation, and one to test. This produces 24 training records, six validation records, and six test records. Pair members stay together.

The labels are balanced by construction. There is no reference population distribution. The deterministic split makes the demonstration reproducible; it is not evidence of statistical independence between underlying policy templates. Repeated task themes remain across splits. A later evaluation must include genuinely novel policy structures and unseen contexts.

## Intended uses and limits

Suitable uses: testing JSONL loading, checking schema and split integrity, reviewing the annotation rubric, and planning a larger authorization study.

The pilot is not sufficient for substantive model training, fairness claims, deployment decisions, demographic comparisons, or legal determinations. Authored rationales require review. Language styles are coarse categories, and scenarios have strong explicit policy cues. Multilingual use, implied authority, conflicting policies, temporal scope, and uncertain evidence are not covered.

Independent review, participant consent, ethics review, and model evaluation have not been performed. No institution has certified this dataset as unbiased. A training release requires the protocol's separate release decision.

## Licensing and maintenance

This package does not grant rights to material outside these newly authored examples. The existing repository references an MIT license but does not contain a LICENSE file at this release. Accordingly, this pilot does not establish a separate reuse license; obtain written reuse terms before redistribution or use outside this research review. Source publications retain their respective rights.

Use the SHA256 digest in audit_report.json to identify the exact audited bytes. Preserve historical versions and report substantive corrections through a repository issue. The current audit covers integrity only and does not automatically approve releases.
