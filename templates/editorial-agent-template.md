# Editorial Agent Template

Template: editorial-agent-template

Version: 1.0.0

Extends: agent-template v1.0.0

Status: Stable

Owner: EditorialAfrica

---

# Purpose

The Editorial Agent Template defines additional requirements for AI agents responsible for editorial analysis and intelligence.

This template extends the universal runtime contract defined by `agent-template.md`.

All editorial agents SHALL implement the Agent Template in addition to the requirements defined here.

---

# Applicable Agents

This template applies to:

- EditorialSummary.Agent
- ComparativeAnalysis.Agent
- Enterprise.Agent

---

# Editorial Responsibilities

Editorial agents are responsible for transforming validated editorial content into structured editorial intelligence.

They SHALL:

- analyse editorial content
- preserve factual accuracy
- remain politically neutral
- avoid introducing unsupported conclusions
- maintain traceability to original sources

---

# Editorial Inputs

Editorial agents typically consume:

## Required Context

- editorialContext.editorials
- productionContext.metadata

## Optional Context

- editorialContext.entities
- editorialContext.keywords

---

# Editorial Outputs

Editorial agents typically produce:

- Editorial summaries
- Comparative analysis
- Enterprise intelligence
- Editorial themes
- Key findings
- Supporting evidence

---

# Editorial Standards

Every editorial output SHALL:

- preserve meaning
- preserve chronology
- distinguish facts from analysis
- avoid sensational language
- avoid speculation

---

# Source Attribution

Editorial conclusions SHALL be traceable to collected sources.

Every significant finding should reference:

- newspaper
- publication date
- headline
- source identifier

---

# Editorial Validation

Validate:

✓ editorial completeness

✓ factual consistency

✓ source attribution

✓ neutrality

✓ duplicate findings

---

# Editorial Quality Checklist

Before completion verify:

✓ Every story analysed

✓ Themes extracted

✓ Duplicates removed

✓ Findings supported

✓ Context updated

---

# Additional Context Updates

Editorial agents typically update:

editorialContext

- summaries
- themes
- findings
- comparisons
- enterpriseInsights

---

# Generated Artifacts

Examples:

artifacts/editorial-summary.md

artifacts/comparative-analysis.md

artifacts/enterprise-intelligence.md

---

# Editorial Completion Criteria

Execution completes only when:

✓ All editorials processed

✓ Summary generated

✓ Validation passed

✓ Context updated

✓ Artifact registered

✓ No unsupported conclusions remain