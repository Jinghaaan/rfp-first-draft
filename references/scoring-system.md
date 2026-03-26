# Scoring System Reference

## Flag System

Use these flags to annotate every answer in the filled RFP. A question can carry
**multiple flags** (e.g., WEAK + REVIEW).

| Flag | Trigger Condition | Action Required |
|---|---|---|
| WEAK | No strong source; answer is inferred or generic | Human should strengthen with specifics |
| NEEDS INPUT | Requires a number, cert, or client name not in KB | Sales/product team to supply |
| REVIEW | Roadmap claim, competitor comparison, compliance/legal statement | Human sign-off before submission |
| BLANK | Zero KB coverage for this question | Add relevant document to KB, or leave for SME |

## Confidence Logic

| Level | Criteria |
|---|---|
| **High** | Source weight is Won deal response, directly on-topic |
| **Medium** | Source weight is Active deal / strong internal doc with relevant content; or Won deal but only tangentially related |
| **Low** | Internal background doc only; or answer inferred without a direct source |

## Document Weight Guide

Use these weights when building the document inventory table:

| Weight | Document Type | Trust Level |
|---|---|---|
| Won deal responses | Highest trust — prefer as primary source | Primary |
| Active deals / strong internal docs | Good signal — use with moderate confidence | Secondary |
| Lost deals with useful content | Borrow content, note it came from a lost bid | Tertiary |
| Internal background docs | Reference only; not client-proven | Background |
