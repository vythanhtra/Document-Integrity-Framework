# Document-Integrity-Framework
A structured prompt framework for reducing PDF table extraction errors, false proximity bias, and reasoning failures in AI document analysis workflows.
# PDF & Excel Structured Document Guardrail Prompt

## Why this project exists

Large Language Models (LLMs) are increasingly used to analyze technical specifications, procurement documents, contracts, bills of quantities (BOQ), and engineering datasets stored in PDF and Excel formats.

While modern AI systems demonstrate strong reasoning capabilities, they remain vulnerable to a class of failures caused by document extraction pipelines rather than reasoning itself.

Common failure modes include:

* PDF table extraction errors
* Loss of row-column relationships
* Snippet truncation during search retrieval
* False context association ("False Proximity")
* Hallucinated links between adjacent records
* Conclusions generated from incomplete document context

In high-impact domains such as construction, procurement, engineering, compliance, and contract review, these failures can lead to incorrect supplier attribution, specification mismatches, compliance risks, and contractual disputes.

This project introduces a structured prompt framework designed to reduce those risks.

---

## Design Philosophy

The objective is not to make the AI "more intelligent".

The objective is to make the AI:

1. Read before reasoning.
2. Preserve table structure.
3. Verify row-to-column relationships.
4. Detect extraction uncertainty.
5. Refuse unsupported conclusions.
6. Prioritize source fidelity over retrieval speed.

The framework treats document analysis as a data integrity problem before it becomes a reasoning problem.

---

## Key Failure Modes Addressed

### 1. PDF Table Extraction Disorder

Multi-column PDF tables are frequently converted into linear text streams during extraction.

As a result, values from different columns or rows may become incorrectly associated.

### 2. False Proximity Bias

Information appearing close together in extracted text can be incorrectly interpreted as belonging to the same record.

The underlying data may be correct while the contextual relationship becomes corrupted.

### 3. Search-First Retrieval Errors

Keyword search often returns truncated snippets rather than complete document context.

This creates a high risk of reasoning over partial information.

### 4. Cross-Source Consistency Failures

Critical conclusions are sometimes generated from a single source without validation against supporting documents.

---

## Core Principles

* READ before SEARCH whenever structured tables are involved.
* Preserve original table hierarchy.
* Verify entity-to-row relationships before citation.
* Require source attribution for every conclusion.
* Detect confidence degradation caused by extraction quality.
* Escalate uncertainty instead of guessing.

---

## Intended Use Cases

* Technical Data Sheets
* Procurement Specifications
* Construction BOQs
* Engineering Submittals
* Vendor Comparison Matrices
* Compliance Documentation
* Contract Review Workflows
* Enterprise Knowledge Retrieval Systems

---

## Expected Outcome

This framework does not eliminate extraction errors.

Instead, it significantly reduces the probability that extraction errors propagate into reasoning errors.

In other words:

> The goal is not merely to retrieve the correct data.
>
> The goal is to preserve the correct context of the data.

Because in structured documents, data integrity depends on both value accuracy and relationship accuracy.
