# False Proximity Case

## Case Study: False Proximity Bias in PDF Table Extraction

This case documents a real-world failure scenario where an AI system incorrectly attributed supplier information from one specification item to another during document analysis.

The underlying source data was correct. The error occurred because table structure was lost during PDF extraction and the model reasoned over a truncated search snippet rather than the complete document.

---

## Problem

Supplier information from item III.4 was incorrectly assigned to item III.5 due to snippet truncation.

**Original Table:**

| Item | Description | Manufacturer |
|------|-------------|---------------|
| III.4 | Equipment A | Viking |
| III.5 | Equipment B | Not Specified |

**Extracted Snippet (after PDF processing):**

```
III.4 Viking III.5 Equipment B
```

**AI Interpretation (incorrect):**

```
III.5 → Viking
```

---

## Root Cause

- **Root Cause 1:** PDF table extraction disorder — row-column structure flattened into linear text
- **Root Cause 2:** Search snippet truncation — retrieval layer returned only partial context
- **Root Cause 3:** False Proximity Bias — two entities appearing close together in extracted text were incorrectly assumed to be related

**Failure Propagation Path:**

```
PDF Table
    ↓
Extraction (Structure Loss)
    ↓
Search Snippet (Context Corruption)
    ↓
False Proximity
    ↓
Wrong Supplier Attribution
```

---

## Resolution

- READ full document before SEARCH
- Verify row-column relationships explicitly
- Require source citation for critical conclusions
- Reject conclusions when confidence is low

---

## Failure Classification

| Code | Type |
|------|------|
| FT-01 | PDF_TABLE_EXTRACTION_ERROR |
| FT-03 | FALSE_PROXIMITY_BIAS |
| FT-04 | SNIPPET_TRUNCATION |

---

## Lessons Learned

> Correct data is not sufficient.
>
> Correct context is equally important.

For structured documents, preserving relationships between rows, columns, entities, and attributes is essential for reliable AI-assisted analysis.

---

## Mitigation Strategy

1. Prefer READ over SEARCH for structured documents
2. Validate table integrity before reasoning
3. Verify row-column relationships explicitly
4. Require source citation for critical conclusions
5. Reject conclusions when confidence is low

---

**Severity:** Medium  
**Potential Impact:** Supplier Misidentification, Technical Specification Errors, Procurement Risk, Contract Review Risk  
**Status:** Resolved through full-document verification
