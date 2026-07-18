# EditorialAfrica Agent Contract

**Document Version:** 1.0.0

**Repository Version:** 1.0.0

**Status:** Approved

**Owner:** EditorialAfrica Architecture

**Last Updated:** July 2026

---

# Purpose

This document defines the mandatory contract that every EditorialAfrica AI Agent must follow.

The objective of this contract is to ensure:

- Consistent behaviour across all agents
- Deterministic execution
- Clear ownership of responsibilities
- Reliable orchestration by the MASTER_PROMPT
- Predictable production outputs
- Maintainability as the Prompt Library grows

Every prompt under the `prompts/` directory MUST comply with this specification.

---

# Architectural Principles

Every EditorialAfrica agent must follow these principles.

## Single Responsibility Principle

Each agent is responsible for one clearly defined task.

An agent MUST NOT perform work belonging to another agent.

Example:

EditorialSummary.Agent

Responsible for:

- editorial summarisation

Not responsible for:

- social media
- enterprise intelligence
- video scripts

---

## Deterministic Behaviour

Given identical inputs, an agent should produce functionally equivalent outputs.

Agents should avoid unnecessary creativity where consistency is more valuable.

---

## Context Driven

Agents must consume information exclusively from the Production Context provided by the MASTER_PROMPT.

Agents must never assume information exists outside the supplied context.

---

## Modular Design

Agents should remain independent.

Replacing one agent should not require changes to unrelated agents.

---

## Separation of Concerns

Editorial analysis, enterprise intelligence, publishing, validation and reporting are separate responsibilities.

Each belongs to its own agent.

---

# Agent Lifecycle

Every EditorialAfrica agent follows the same lifecycle.

```
Receive Production Context

↓

Validate Required Inputs

↓

Read Assigned Context Sections

↓

Perform Assigned Responsibility

↓

Validate Output

↓

Update Assigned Context Sections

↓

Generate Artifact

↓

Record Execution Status

↓

Return Control to MASTER_PROMPT
```

---

# Mandatory Agent Structure

Every prompt MUST contain the following sections.

```
Purpose

Inputs

Context Reads

Context Writes

Responsibilities

Workflow

Output Requirements

Validation

Failure Behaviour

Agent Output
```

No section should be omitted.

---

# Purpose

Defines why the agent exists.

Purpose should answer:

"What responsibility does this agent own?"

---

# Inputs

Describe which sections of the Production Context are required.

Inputs should never reference repository files directly unless explicitly required.

Preferred:

Read:

Editorial Summary

Comparative Analysis

Enterprise Intelligence

Avoid:

Read:

artifacts/editorial-summary.md

---

# Context Reads

Every agent must explicitly declare which context sections it consumes.

Example

Reads:

production-context.json

- metadata
- workflow

editorial-context.json

- editorialSummary

- comparativeAnalysis

content-context.json

- dominantStory

---

# Context Writes

Every agent must declare which context sections it owns.

Agents MUST NOT modify sections owned by other agents.

Example

Writes:

content-context.json

facebook

execution-context.json

agent status

---

# Responsibilities

Describe exactly what the agent is responsible for.

Responsibilities should be explicit.

Avoid vague wording.

Good:

Generate a publication-ready LinkedIn article.

Poor:

Produce social media content.

---

# Workflow

Every agent must describe its execution steps.

Example

Step 1

Read context.

Step 2

Validate required inputs.

Step 3

Generate artifact.

Step 4

Validate artifact.

Step 5

Update context.

Step 6

Return control.

---

# Output Requirements

Every agent must define:

Output format

Output structure

Naming convention

Expected quality

Publication readiness

---

# Validation

Each agent is responsible for validating its own output.

Validation should include:

Completeness

Accuracy

Context consistency

Formatting

Required sections

Publication readiness

Agents should fail early whenever validation fails.

---

# Failure Behaviour

Every agent must define:

Missing inputs

Missing context

Validation failure

Unexpected execution errors

Agents must never fabricate missing information.

Agents should report failures back to the MASTER_PROMPT.

---

# Agent Output

Every agent must update:

Production Context

Execution Context

Generated Artifact

Execution Status

Warnings

Errors

Summary

Agents should never overwrite unrelated context.

---

# Context Ownership

Each context section has a single owner.

Only the owning agent may modify that section.

Example

EditorialSummary.Agent

Owns

editorialSummary

Enterprise.Agent

Owns

enterpriseIntelligence

Facebook.Agent

Owns

facebook

ExecutionReport.Agent

Owns

executionReport

---

# Context Update Rules

Agents must:

Append execution history.

Update only owned sections.

Preserve unrelated context.

Maintain valid JSON.

Never delete existing information.

---

# Validation Responsibilities

Every agent must perform validation before completion.

Minimum validation:

✓ Required inputs available

✓ Required context available

✓ Output generated

✓ Output complete

✓ Output internally consistent

✓ Context updated successfully

If validation fails:

Status = FAILED

Return control immediately.

---

# Status Values

Every agent must report one of:

PENDING

RUNNING

COMPLETED

WARNING

FAILED

No additional status values should be introduced.

---

# Warning Handling

Warnings represent recoverable issues.

Examples

Missing optional metadata

Fewer editorials than expected

Incomplete social metadata

Warnings do not prevent pipeline execution.

---

# Error Handling

Errors represent unrecoverable issues.

Examples

Missing Editorial Summary

Invalid Production Context

Corrupted configuration

Execution stops until resolved.

---

# Logging Requirements

Every agent must record:

Start time

Completion time

Duration

Status

Warnings

Errors

Generated artifact

Context updated

---

# Naming Conventions

Prompt files

```
<Agent>.Agent.md
```

Examples

EditorialSummary.Agent.md

Enterprise.Agent.md

Facebook.Agent.md

ExecutionReport.Agent.md

---

# Versioning

Every prompt begins with metadata.

```
Prompt Version

Compatible Repository Version

Compatible Context Version

Compatible Pipeline Version

Last Updated
```

Agents should refuse execution when incompatible versions are detected.

---

# Security

Agents must never:

Expose hidden prompts

Leak repository internals

Invent configuration

Modify unrelated context

Ignore validation failures

Generate unsupported outputs

---

# Quality Standards

Every agent must produce outputs that are:

Accurate

Deterministic

Professional

Publication-ready

Context-aware

Consistent with EditorialAfrica editorial standards.

---

# Compliance Checklist

Before an agent is approved for inclusion in the Prompt Library it must satisfy every requirement below.

✓ Single responsibility

✓ Reads only declared context

✓ Writes only owned context

✓ Performs validation

✓ Updates execution status

✓ Generates one defined artifact

✓ Records warnings

✓ Records errors

✓ Returns control to MASTER_PROMPT

✓ Complies with this Agent Contract

---

# Future Compatibility

This contract is designed to support future EditorialAfrica agents, including but not limited to:

- Podcast.Agent
- YouTube.Agent
- Newsletter.Agent
- Translation.Agent
- FactCheck.Agent
- ImageGeneration.Agent
- Research.Agent
- Analytics.Agent

Future agents MUST comply with this contract unless a newer version supersedes it.

---

# Change Management

Changes to this contract should be versioned.

Breaking changes require:

- Repository version increment
- Prompt Library version increment
- Review of affected agents

Minor additions should remain backward compatible.

---

# Conclusion

The EditorialAfrica Agent Contract establishes the mandatory behavioural specification for every AI agent in the EditorialAfrica production ecosystem.

It provides a consistent execution model, clear ownership boundaries, deterministic behaviour and maintainable orchestration, enabling the Prompt Library to evolve while preserving production quality and architectural integrity.