# Agent Validator

Version: 1.0.0

---

# Purpose

The Agent Validator verifies that every AI Agent registered within the EditorialAfrica platform complies with the AI Agent Contract and all associated platform specifications.

The validator guarantees that every executable agent is structurally complete, correctly configured, and ready for deterministic execution.

---

# Scope

The Agent Validator validates:

- Agent metadata
- Agent configuration
- Prompt structure
- Context references
- Template references
- Artifact definitions
- Dependencies
- Version compatibility

---

# Responsibilities

The Agent Validator shall:

- Validate every registered AI Agent
- Ensure mandatory metadata exists
- Verify template conformance
- Verify context references
- Verify artifact references
- Verify dependency integrity
- Validate lifecycle status
- Produce validation reports

The validator shall never modify agent definitions.

---

# Validation Rules

## Metadata Validation

Each agent must contain:

- id
- name
- description
- version
- owner
- status
- category

---

## Template Validation

Every agent shall reference an existing template.

Example

```
editorial-agent-template.md
```

Validation fails if the template cannot be found.

---

## Context Validation

Referenced contexts must exist.

Example:

```
editorial-context

production-context

execution-context
```

Missing contexts generate an Error.

---

## Artifact Validation

Every declared output artifact shall exist within the Artifact Registry.

Example:

```
Editorial Summary

Facebook Post

Video Script
```

---

## Prompt Validation

The validator verifies:

- Prompt sections
- Placeholder syntax
- Variable definitions
- Required instructions
- Reserved keywords
- Context placeholders

---

## Dependency Validation

The validator verifies:

- Required agents exist
- Circular dependencies
- Missing dependencies
- Invalid references

---

## Version Validation

The validator ensures:

- Semantic version compliance
- Compatible template version
- Compatible contract version
- Compatible schema version

---

# Validation Checklist

| Rule | Required |
|-------|----------|
| Agent ID | ✓ |
| Name | ✓ |
| Version | ✓ |
| Owner | ✓ |
| Status | ✓ |
| Category | ✓ |
| Template Exists | ✓ |
| Context Exists | ✓ |
| Artifacts Exist | ✓ |
| Dependencies Valid | ✓ |
| Prompt Valid | ✓ |

---

# Failure Severity

| Condition | Severity |
|-----------|----------|
| Missing ID | Critical |
| Missing Template | Error |
| Missing Context | Error |
| Missing Artifact | Error |
| Invalid Metadata | Error |
| Invalid Version | Warning |
| Deprecated Template | Warning |

---

# Validation Report

Example:

```json
{
  "validator": "Agent Validator",
  "version": "1.0.0",
  "status": "PASS",
  "summary": {
    "agentsValidated": 14,
    "passed": 14,
    "warnings": 0,
    "errors": 0
  },
  "results": [
    {
      "agent": "Editorial Summary Agent",
      "status": "PASS"
    },
    {
      "agent": "Video Script Agent",
      "status": "PASS"
    }
  ]
}
```

---

# Design Principles

The Agent Validator shall be:

- Deterministic
- Stateless
- Non-destructive
- Reproducible
- Traceable

The validator performs verification only and shall never alter agent definitions.

---

# Dependencies

The Agent Validator depends on:

- AI Agent Contract
- Template Contract
- Context Contract
- Artifact Contract
- Validator Contract
- Agent Schema

---

# Success Criteria

Validation is successful when:

- Every registered agent complies with the AI Agent Contract.
- All referenced templates exist.
- All referenced contexts exist.
- All referenced artifacts exist.
- All dependencies are valid.
- No Critical validation failures are detected.

A successful validation indicates that the platform's AI Agents are ready for execution.