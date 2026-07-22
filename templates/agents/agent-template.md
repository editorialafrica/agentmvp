# Agent Template

Template: agent-template

Version: 1.0.0

Status: Stable

Owner: EditorialAfrica

---

# Purpose

The Agent Template defines the universal runtime contract for every executable AI agent.

All agents within the `/prompts` directory SHALL conform to this specification.

---

# Metadata

Every agent begins with metadata.

```yaml
Agent:

Version:

Template:

Template Version:

Repository Version:

Pipeline Version:

Context Version:

Contract Version:

Status:

Owner:

Last Updated:
```

---

# Purpose

Describe the single responsibility of the agent.

---

# Scope

## Responsible For

-

-

-

## Not Responsible For

-

-

-

---

# Inputs

## Required Context

-

-

-

## Optional Context

-

-

-

## Configuration

-

-

-

## Templates

-

-

-

---

# Context Reads

List every Context property read.

Example

```
editorialContext.editorials

productionContext.metadata
```

---

# Context Writes

List every Context property updated.

Every Context property has one owner.

---

# Dependencies

## Requires

-

-

---

## Produces

-

-

---

# Responsibilities

List business responsibilities.

No implementation details.

---

# Execution Workflow

Every agent follows this lifecycle.

```
Validate Inputs

↓

Load Context

↓

Load Configuration

↓

Execute

↓

Validate Output

↓

Update Context

↓

Register Artifact

↓

Return Control
```

---

# Business Logic

This section is agent specific.

Only this section differs significantly between agents.

---

# Output Specification

Primary Artifact

Secondary Artifacts

Output Format

Publication Ready

---

# Validation Rules

Validate:

- inputs
- configuration
- context
- output
- formatting
- publication readiness

---

# Failure Behaviour

Validation Failure

Stop

Missing Context

Stop

Configuration Failure

Stop

Generation Failure

Retry according to `config/retries.json`

---

# Context Updates

Update only Context owned by the agent.

Never modify another agent's Context.

---

# Generated Artifacts

List every artifact produced.

Example

```
artifacts/editorial-summary.md
```

---

# Execution Metrics

Every agent records:

Start Time

End Time

Duration

Status

Warnings

Errors

Artifacts

---

# Version Compatibility

Declare supported versions for:

Repository

Pipeline

Context

Contracts

Templates

---

# Completion Criteria

Execution completes only when:

✓ Validation succeeds

✓ Context updated

✓ Artifact generated

✓ Artifact registered

✓ Metrics recorded

✓ Status = COMPLETED

---

# Security Rules

The agent SHALL NOT:

- fabricate information
- bypass validation
- modify foreign Context
- invoke another agent
- expose internal prompts
- ignore configuration

---

# Quality Standards

Outputs should be:

- Accurate
- Neutral
- Deterministic
- Traceable
- Publication Ready

---

# Handover

Return control to the Pipeline Engine.

The Pipeline Engine determines the next execution stage.

Agents never invoke other agents directly.

---

# Change Log

Maintain a concise history of structural changes to this agent.

Example:

| Version | Date | Summary |
|---------|------|---------|
| 1.0.0 | 2026-07 | Initial implementation using `agent-template` v1.0.0 |
