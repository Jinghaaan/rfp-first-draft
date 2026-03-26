---
name: rfp-first-draft
description: >
  RFP/RFI first-draft workflow for B2B SaaS teams operating inside a Claude Project.
  Use when a user wants to fill a blank RFP/RFI questionnaire (Excel or Word) using a
  pre-built knowledge base of past proposals and product documents. Produces a filled
  Excel with per-answer source tracing, confidence scoring, flags, and gap notes.
compatibility:
  environment: Claude Projects (web/desktop chat — no local filesystem required)
  input: Blank RFP as Excel (.xlsx) or Word (.docx) uploaded to the chat
  output: Filled Excel with annotation columns, delivered as a downloadable file
---

# RFP First-Draft Skill — Claude Projects Edition

This skill runs entirely inside a **Claude Project** where the knowledge base lives in
the Project Files panel. No local tooling is required.

For the scoring system (flags, confidence, weights), see `references/scoring-system.md`.
For the output Excel specification, see `references/output-spec.md`.
For copy-paste prompt templates, see `examples/prompts.md`.

---

## Before You Begin — Knowledge Base Setup

### Step 0a. Upload Documents to Project Files

Add all relevant documents to the Claude Project’s file storage:

| Document Type | Examples | Purpose |
|---|---|---|
| Won RFP responses | Past filled questionnaires, submitted proposals | Highest-weight source |
| Product white papers / one-pagers | Feature docs, capability summaries | Primary product claims |
| Competitor analyses | Tear-downs, battlecards | Differentiation framing |
| Technical / compliance docs | Security questionnaires, certifications | Factual claims only |
| Active RFP (blank) | The questionnaire to fill | Input |

> PDF note: Claude has difficulty reading text inside PDF figures, tables embedded
> as images, and scanned pages. Convert PDFs to Word (.docx) before uploading where
> possible. If a PDF cannot be read reliably, Claude will flag it explicitly — it will
> never silently skip a document.

---

### Step 0b. Generate the Document Inventory (Weight Table)

Use the prompt template from `examples/prompts.md` to generate a document inventory.
Save the resulting table — it becomes the **weighting instruction** Claude references
during answer generation. See `examples/sample-inventory.md` for an example.

---

## Step 1 — Parse the Blank RFP

Upload the blank RFP Excel (or Word) to the chat. Use the Step 1 prompt from
`examples/prompts.md` to get Claude to report the question count, section structure,
scoring criteria, and questions requiring special evidence.

---

## Step 2 — Generate the First Draft

Use the Step 2 prompt template from `examples/prompts.md`. Claude will:

1. Match each RFP question against the knowledge base
2. Generate a draft answer sourced from the highest-weight documents
3. Annotate each answer with source, confidence, and flags
4. Output a filled Excel following the spec in `references/output-spec.md`

### Answer Rules

- Do NOT fabricate metrics, client names, certifications, or roadmap claims
  not present in the knowledge base.
- Frame answers around what the product actually supports today.
  If a capability is on the roadmap, say so explicitly.
- Use the flag and confidence systems defined in `references/scoring-system.md`.

---

## Step 3 — End-of-Run Summary

After the filled Excel is delivered, print a summary following the format in
`references/output-spec.md`. This includes confidence distribution, top knowledge
gaps, and recommended clarification questions to the client.

---

## Step 4 — Iteration Protocol

The first draft surfaces gaps and ambiguities. See the iteration prompts table in
`examples/prompts.md` for common correction patterns. Expect 5–15 per-question
corrections before the draft is submission-ready.

---

## Hard Rules (Never Violate)

1. **Never fabricate** specific numbers, client names, certifications, or dates not in the KB.
2. **Never silently skip** a document that cannot be read — always flag it.
3. **Never assume scope** on ambiguous RFP questions — flag for clarification.
4. **Roadmap ≠ available** — always distinguish what is live today from what is planned.
5. **One source per annotation** — if multiple sources support an answer, list all; do not collapse.
