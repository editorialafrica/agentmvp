# Report Agent Template

Template: report-agent-template

Version: 1.0.0

Extends: agent-template v1.0.0

Status: Stable

Owner: EditorialAfrica

---

# Purpose

The Report Agent Template defines additional requirements for AI agents responsible for generating structured reports about pipeline execution, repository health, production quality, or analytical results.

This template extends the universal runtime contract defined by `agent-template.md`.

---

# Applicable Agents

This template applies to:

- ExecutionReport.Agent

Future examples:

- QualityReport.Agent
- ValidationReport.Agent
- AnalyticsReport.Agent

---

# Responsibilities

Report agents SHALL:

- summarise execution
- report validation outcomes
- record warnings
- record failures
- report production metrics
- produce auditable documentation

---

# Inputs

## Required Context

- executionContext
- productionContext

## Optional Context

- editorialContext
- contentContext

---

# Report Structure

Every report should contain:

- Metadata
- Executive Summary
- Pipeline Status
- Validation Results
- Agent Status
- Artifact Summary
- Warnings
- Errors
- Recommendations

---

# Reporting Standards

Reports SHALL:

- be factual
- be traceable
- avoid speculation
- include timestamps
- include execution identifiers
- clearly distinguish warnings from failures

---

# Metrics

Report agents should summarise:

- execution duration
- completed stages
- failed stages
- retry count
- generated artifacts
- validation results

---

# Validation

Validate:

✓ report completeness

✓ execution statistics

✓ warnings recorded

✓ errors recorded

✓ artifact inventory

---

# Generated Artifacts

Examples

artifacts/execution-report.md

artifacts/validation-report.md

artifacts/metrics-report.md

---

# Completion Criteria

Execution completes only when:

✓ Report generated

✓ Metrics summarised

✓ Validation completed

✓ Artifacts registered

✓ Context updated

✓ Repository state recorded