# rfp-first-draft

A Claude skill for generating first-draft RFP/RFI responses using a knowledge base of past proposals and product documents.

Designed for **B2B SaaS teams** who respond to RFPs regularly and want to accelerate the first-draft phase from days to minutes.

## What It Does

Given a blank RFP questionnaire (Excel or Word) and a knowledge base of past proposals, this skill instructs Claude to:

- Parse every question in the RFP
- Match each question against your knowledge base, weighted by document quality
- Generate a draft answer with source citations
- Score confidence (High / Medium / Low) and flag items needing human review
- Output a filled Excel with annotation columns for internal review

## Environment

This skill is built for **Claude Projects** (web/desktop chat). Your knowledge base lives in the Project Files panel — no local filesystem or CLI required.

## Installation

### Option A: Copy to your Claude skills directory

```bash
# Clone this repo
git clone https://github.com/Jinghaaan/rfp-first-draft.git

# Copy to your Claude skills directory
cp -r rfp-first-draft ~/.claude/skills/
```

### Option B: Manual setup

1. Create a folder `~/.claude/skills/rfp-first-draft/`
2. Copy all files from this repo into that folder
3. The skill will be available the next time you start a Claude session

## Folder Structure

```
rfp-first-draft/
├── SKILL.md                  # Core skill instructions (Claude reads this)
├── references/
│   ├── scoring-system.md     # Flag system + confidence logic
│   └── output-spec.md        # Excel output column specification
├── examples/
│   ├── prompts.md            # Copy-paste prompt templates for each step
│   └── sample-inventory.md   # Example document inventory table
└── README.md                 # This file (for GitHub, not loaded by Claude)
```

## Quick Start

1. **Set up a Claude Project** and upload your knowledge base documents (won proposals, product docs, compliance docs)
2. **Generate a document inventory** using the prompt in `examples/prompts.md`
3. **Upload your blank RFP** to the chat
4. **Run the first-draft generation** — Claude will produce a filled Excel with annotations

See `SKILL.md` for the full step-by-step workflow.

## Output Format

The filled Excel preserves all original RFP columns and appends:

| Draft Answer | Source Document | Source Passage | Confidence | Flag | Blank | Gap Note |
|---|---|---|---|---|---|---|

## Flag System

| Flag | Meaning |
|---|---|
| WEAK | No strong source; answer is inferred or generic |
| NEEDS INPUT | Requires a number, cert, or client name not in KB |
| REVIEW | Roadmap claim, competitor comparison, or compliance/legal statement |
| BLANK | Zero KB coverage for this question |

## Contributing

Issues and pull requests are welcome. If you've adapted this skill for a specific industry or workflow, consider sharing your variant.
