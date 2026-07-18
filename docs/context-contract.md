# EditorialAfrica Context Contract

**Document Version:** 1.0.0

**Repository Version:** 1.0.0

**Status:** Approved

**Owner:** EditorialAfrica Architecture

**Last Updated:** July 2026

---

# Purpose

This document defines the Context Contract for the EditorialAfrica production platform.

The Context Contract establishes the authoritative data structures exchanged between the PLATFORM and every AI Agent during a production run.

Its objectives are to:

- provide a single source of truth
- eliminate ambiguity between agents
- prevent duplicate processing
- support deterministic execution
- enable future workflow automation
- support auditability and traceability

All EditorialAfrica agents MUST comply with this contract.

---

# Architectural Principles

EditorialAfrica uses shared execution contexts rather than direct communication between agents.

Agents NEVER communicate with one another directly.

Instead, every interaction occurs through approved Context documents managed by the PLATFORM.

```
PLATFORM
        │
        ▼
Production Context
        │
        ▼
Editorial Context
        │
        ▼
Content Context
        │
        ▼
Execution Context
```

This ensures:

- loose coupling
- deterministic execution
- independent agents
- simplified maintenance
- future parallel execution

---

# Context Types

EditorialAfrica defines four official Context documents.

| Context | Purpose | Mutable |
|---------|----------|----------|
| Production Context | Workflow orchestration | Yes |
| Editorial Context | Editorial intelligence | Limited |
| Content Context | Publishing intelligence | Yes |
| Execution Context | Audit and telemetry | Yes |

No additional runtime context files should be introduced without updating this contract.

---

# Production Context

## Purpose

The Production Context represents the current state of the production workflow.

It is the operational control document for the entire pipeline.

It includes:

- execution metadata
- workflow state
- repository configuration
- generated artifact references
- publication readiness

---

## Owner

PLATFORM

---

## Consumers

All agents

---

## Update Rules

Agents MAY update only:

- workflow status
- owned artifact references
- completion status

Agents MUST NOT modify repository metadata.

---

# Editorial Context

## Purpose

The Editorial Context contains the validated editorial intelligence for the current production run.

It is the canonical editorial dataset.

It should never contain presentation-specific wording.

---

## Contents

Examples include:

- Editorial Summary
- National Themes
- Comparative Analysis
- Enterprise Intelligence
- Shared Facts
- Editorial Entities

---

## Owner

EditorialSummary.Agent

ComparativeAnalysis.Agent

Enterprise.Agent

Each owns only its assigned section.

---

## Consumers

HeyGen

Facebook

LinkedIn

Instagram

TikTok

X

ExecutionReport

---

## Update Rules

Publishing agents MUST treat this context as read-only.

No publishing agent may modify editorial intelligence.

---

# Content Context

## Purpose

The Content Context transforms editorial intelligence into publication-ready messaging.

This context exists to decouple editorial analysis from publishing.

---

## Contents

Examples:

- Dominant Story
- Headline
- Key Insights
- Policy Insights
- Business Insights
- Suggested Call To Action
- Recommended Hashtags
- Platform Tone Guidance

---

## Owner

Content Context Builder

---

## Consumers

HeyGen

Facebook

LinkedIn

Instagram

TikTok

X

---

## Update Rules

Publishing agents may add platform-specific metadata only if explicitly allowed.

Publishing agents MUST NOT alter shared messaging.

---

# Execution Context

## Purpose

The Execution Context records everything that happened during production.

It is the permanent operational audit.

---

## Contents

Examples:

- Agent execution history
- Validation results
- Warnings
- Errors
- Performance metrics
- Timeline
- Runtime telemetry

---

## Owner

ExecutionReport.Agent

PLATFORM

---

## Consumers

ExecutionReport.Agent

Operations

Future automation

---

# Context Ownership

Every context section has exactly one owner.

Ownership defines write permissions.

Read access may be broader.

No two agents may own the same section.

---

# Read Rules

Agents should read only the sections required to perform their responsibilities.

Reading unrelated context is discouraged.

---

# Write Rules

Agents may update only their assigned sections.

Agents must never overwrite another agent's output.

Context updates should be additive whenever possible.

---

# Immutable Data

The following fields become immutable after creation:

- executionId
- executionDate
- country
- repositoryVersion
- promptLibraryVersion

Editorial facts become immutable once validated.

---

# Mutable Data

Examples:

- workflow status
- completion state
- warnings
- execution metrics
- publication readiness

---

# Context Lifecycle

Every production run follows the same lifecycle.

```
Context Created

↓

Repository Loaded

↓

Workflow Started

↓

Editorial Intelligence Built

↓

Content Context Generated

↓

Publishing Artifacts Produced

↓

Execution Recorded

↓

Production Completed
```

Contexts should never be reused across production runs.

---

# Validation

Every context update must preserve:

- valid JSON
- ownership rules
- required fields
- version compatibility

Invalid context updates should immediately fail validation.

---

# Versioning

Every Context document must include:

- schemaVersion
- contextVersion
- repositoryVersion
- generatedBy
- lastUpdatedBy
- lastUpdatedAt

Breaking changes require a new Context version.

---

# Context Compatibility

Agents should verify compatibility before execution.

If incompatible versions are detected:

- stop execution
- report the incompatibility
- return control to PLATFORM

---

# Security

Context documents must never expose:

- hidden prompts
- system instructions
- repository secrets
- unpublished internal reasoning

Only production data should be stored.

---

# Performance

Contexts should remain concise.

Avoid duplication.

Reference generated artifacts rather than embedding large outputs whenever practical.

---

# Future Expansion

Additional Context documents may be introduced for future capabilities such as:

- Translation Context
- Analytics Context
- Image Context
- Podcast Context
- Video Context
- Research Context

Each must have:

- a clearly defined owner
- documented lifecycle
- ownership rules
- validation rules

---

# Compliance Checklist

Before an agent updates a Context it must verify:

✓ Context version is compatible

✓ Required fields exist

✓ Ownership is respected

✓ JSON remains valid

✓ No unrelated sections are modified

✓ Update is recorded

✓ Validation succeeds

---

# Conclusion

The EditorialAfrica Context Contract establishes the rules governing how production data flows through the EditorialAfrica platform.

By separating workflow state, editorial intelligence, publishing intelligence and execution telemetry into dedicated Context documents, the platform achieves deterministic execution, clear ownership boundaries, operational transparency and long-term scalability.
