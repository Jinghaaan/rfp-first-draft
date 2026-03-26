# Output File Specification

## Excel Format Requirements

The delivered Excel must:

- Preserve all original RFP columns exactly (do not rename or reorder)
- Append annotation columns to the right of the last original column
- Use consistent short labels in flag and blank cells (not full sentences)
- Have one row per RFP question

## Column Order (appended right of original content)

| Draft Answer | Source Document | Source Passage | Confidence | Flag | Blank | Gap Note |
|---|---|---|---|---|---|---|

### Column Definitions

| Column | Content |
|---|---|
| **Draft Answer** | Concise, professional answer that directly addresses the question |
| **Source Document** | Filename(s) used, with weight indicator |
| **Source Passage** | Section heading or topic reference within the source file |
| **Confidence** | High / Medium / Low (see scoring-system.md for criteria) |
| **Flag** | WEAK / NEEDS INPUT / REVIEW / BLANK (see scoring-system.md) |
| **Blank** | Yes / No |
| **Gap Note** | If Blank = Yes, what document type would fill this gap |

## End-of-Run Summary Format

After the filled Excel is delivered, print:

```
=== FIRST DRAFT SUMMARY ===
Total Questions Answered: [N]
  High Confidence:   [N]
  Medium Confidence: [N]
  Low Confidence:    [N]
  Needs Input:       [N]
  Needs Review:      [N]
  Blank (no coverage): [N]

TOP KNOWLEDGE GAPS:
1. [Topic] — suggested document type to add: [e.g. "Won proposal covering compliance"]
2. [Topic] — suggested document type to add: [e.g. "Product security certification"]

RECOMMENDED CLARIFICATION QUESTIONS TO CLIENT:
- [Any question where the RFP itself is ambiguous — do NOT speculate; flag for outreach]
```
