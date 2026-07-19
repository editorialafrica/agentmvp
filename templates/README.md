# EditorialAfrica Template Library

Version: 1.0.0

---

# Purpose

The Template Library defines the development standards used throughout the EditorialAfrica AI Platform.

Templates are **development artifacts**.

Templates are **never executed** by the AI runtime.

Only files within the `/prompts` directory are executable AI agents.

The purpose of templates is to ensure every AI agent, artifact, report and context definition follows the same architecture, lifecycle and governance standards.

---

# Design Principles

The EditorialAfrica platform follows six design principles.

## 1. Single Responsibility

Each template defines exactly one type of component.

Examples:

- Editorial Agent
- Social Publishing Agent
- Video Agent
- Reporting Agent

---

## 2. Consistency

Every AI agent should have identical top-level structure.

This allows:

- easier maintenance
- easier reviews
- deterministic behaviour
- automated validation

---

## 3. Separation of Concerns

Templates define structure.

Agents implement business logic.

Configuration controls execution.

Contexts hold shared state.

---

## 4. Configuration Driven

Templates must never contain execution order.

Pipeline execution is controlled by:

```
config/pipeline.json
config/dependencies.json
```

---

## 5. Context First

Agents communicate only through Contexts.

Agents must never invoke one another.

Agents must never exchange hidden messages.

---

## 6. Deterministic Output

Every template should encourage deterministic, repeatable execution.

---

# Template Library

```
templates/

README.md

agent-template.md

editorial-agent-template.md

social-agent-template.md

video-agent-template.md

report-agent-template.md

artifact-template.md

context-template.json

execution-report.md

sources-manifest.md

story-ranking.md
```

---

# Template Hierarchy

```
                         agent-template.md
                                 │
          ┌──────────────────────┼──────────────────────┐
          │                      │                      │
          ▼                      ▼                      ▼
editorial-agent      social-agent       video-agent

                                 │
                                 ▼
                         report-agent
```

The Agent Template defines the universal runtime contract.

Specialised templates extend that contract by adding domain-specific business logic.

---

# Template Responsibilities

| Template | Purpose |
|-----------|---------|
| agent-template.md | Universal runtime contract |
| editorial-agent-template.md | Editorial analysis agents |
| social-agent-template.md | Social publishing agents |
| video-agent-template.md | Video production agents |
| report-agent-template.md | Reporting agents |
| artifact-template.md | Generated artifact structure |
| context-template.json | Context definition |
| execution-report.md | Standard execution reports |
| sources-manifest.md | Source registration |
| story-ranking.md | Story ranking output |

---

# Template Lifecycle

Templates are governed assets.

```
Platform Contract Changes

↓

Update Template

↓

Increase Template Version

↓

Update Agents

↓

Validate Repository

↓

Update CHANGELOG

↓

Release
```

---

# Updating Templates

Templates should only be updated when the platform contract changes.

Examples include:

- new metadata fields
- new validation rules
- new execution lifecycle
- new completion requirements

Templates should **not** be updated for:

- editorial improvements
- better prompts
- improved hashtags
- country-specific behaviour

Those belong in the individual agents.

---

# Template Versioning

Every template declares:

- Template Name
- Version
- Status
- Owner
- Last Updated

Example

```yaml
Template: editorial-agent-template

Version: 1.0.0

Status: Stable

Owner: EditorialAfrica
```

---

# Agent Conformance

Every executable agent must declare:

```yaml
Template: editorial-agent-template

Template Version: 1.0.0
```

Repository validation should verify template compatibility.

---

# Drift Detection

Repository validation should report:

✓ Missing template

✓ Version mismatch

✓ Missing metadata

✓ Missing sections

✓ Invalid structure

---

# Review Checklist

Before approving a new AI agent:

- Correct template selected
- Metadata complete
- Context reads declared
- Context writes declared
- Validation defined
- Outputs registered
- Artifact documented
- Completion criteria defined

---

# Backward Compatibility

Template changes follow Semantic Versioning.

Patch

Documentation only.

Minor

Backward compatible additions.

Major

Breaking structural changes.

---

# Future Templates

Additional templates may be added without modifying existing templates provided they follow the Agent Contract.

---

# Summary

Templates are governance documents.

Agents implement templates.

The Pipeline executes agents.

Contexts coordinate agents.

Configuration controls the platform.