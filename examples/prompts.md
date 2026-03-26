# Prompt Templates

Copy-paste these prompts at each step of the workflow.

---

## Step 0b: Generate Document Inventory

```
Read all files in this project. For each document, create a document inventory table
with these columns:

| File Name | Document Type | Year | Outcome (Won / Lost / Internal) | Weight | Topics Covered | Notes |

Weight guide:
★★★ Won deal responses    — Highest trust. Prefer these as primary source.
★★☆ Active deals / strong internal docs — Good signal. Use with moderate confidence.
★☆☆ Lost deals with useful content — Borrow content, note it came from a lost bid.
✦   Internal background docs — Reference only; not client-proven.

Flag any file you could not read with: ⚠️ UNREADABLE — [reason]
```

---

## Step 1: Parse the Blank RFP

```
Read the uploaded RFP. Report:
- Total number of questions
- Section/category structure
- Any scoring criteria or evaluation weights stated by the client
- Questions that appear to require numerical evidence, certifications, or named client references
```

---

## Step 2: Generate the First Draft

```
Using the knowledge base in this project and the document inventory weight table,
fill in every question in the uploaded RFP Excel.

For each question, produce:

**Answer**: Concise, professional, directly addresses the question.
  - Do NOT fabricate metrics, client names, certifications, or roadmap claims
    that are not present in the knowledge base.
  - Frame answers around what the product actually supports today.
    If a capability is on the roadmap, say so explicitly.

**Annotation block (for internal review — remove before submission):**

| Field | Content |
|---|---|
| Source Document (file level) | [filename(s) used, with weight ★] |
| Source Passage (paragraph level) | [section heading or topic reference within that file] |
| Confidence | High / Medium / Low |
| Flag | See flag system in references/scoring-system.md |
| Blank | Yes / No |
| Gap Note | [if Blank = Yes — what document type would fill this gap] |

After all questions are answered, output a filled Excel with:
- All original columns from the blank RFP preserved
- One new column: "Draft Answer"
- One new column: "Source Document"
- One new column: "Source Passage"
- One new column: "Confidence"
- One new column: "Flag"
- One new column: "Blank"
- One new column: "Gap Note"
```

---

## Iteration Prompts

| Situation | Prompt |
|---|---|
| Answer is too long | "Tighten Q[N] to 2-3 sentences max" |
| Unsupported claim | "Remove the claim about X — we don't have a source for that" |
| Needs client clarification | "Rewrite Q[N] as a clarification question to the client, no examples or assumptions" |
| Capability is roadmap | "Update Q[N] — this is on roadmap, not yet available" |
| Wrong attribution | "Q[N] source should be [correct file], update annotation" |
