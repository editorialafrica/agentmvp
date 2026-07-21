# EditorialAfrica Platform Validators

## Purpose

The Validators module provides the governance layer responsible for verifying the integrity, consistency, and compliance of the EditorialAfrica platform.

Validators ensure that every repository resource complies with the platform specifications before execution.

Unlike AI Agents, validators never generate editorial content. Their sole responsibility is to verify the health of the platform.

---

# Objectives

Validators ensure:

- Repository integrity
- Configuration correctness
- Schema compliance
- Contract compliance
- Pipeline correctness
- Context integrity
- Agent integrity
- Artifact integrity

Together these validators provide deterministic quality assurance across the entire platform.

---

# Validator Architecture

```
                Repository
                     │
                     ▼
          Repository Validator
                     │
      ┌──────────────┼──────────────┐
      ▼              ▼              ▼
Schema Validator  Contract Validator  Pipeline Validator
      │              │              │
      └──────┬───────┴───────┬──────┘
             ▼               ▼
     Context Validator   Agent Validator
             │
             ▼
      Validation Report
```

Every validator operates independently.

Validators may depend on the results produced by earlier validators but never modify repository resources.

---

# Validator Execution Order

Recommended execution order:

1. Repository Validator
2. Schema Validator
3. Contract Validator
4. Pipeline Validator
5. Context Validator
6. Agent Validator

Execution stops if a Critical failure occurs.

---

# Validator Responsibilities

| Validator | Responsibility |
|-----------|----------------|
| Repository Validator | Validates repository structure and required resources |
| Schema Validator | Validates all JSON against schemas |
| Contract Validator | Ensures platform contracts are respected |
| Pipeline Validator | Validates execution graph and orchestration |
| Context Validator | Validates shared contexts |
| Agent Validator | Validates AI Agents and prompt definitions |

---

# Validation Severity

Validation issues are classified using four levels.

| Severity | Meaning |
|----------|---------|
| Information | Informational message |
| Warning | Potential issue |
| Error | Invalid configuration |
| Critical | Platform execution must stop |

---

# Validation Report

Every validator produces a standardized report.

Example:

```json
{
  "validator": "Schema Validator",
  "version": "1.0.0",
  "status": "PASS",
  "summary": {
    "passed": 126,
    "warnings": 1,
    "errors": 0
  }
}
```

---

# Design Principles

Validators must be:

- Deterministic
- Stateless
- Idempotent
- Non-destructive
- Traceable
- Reproducible

Validators never modify repository resources.

---

# Future Evolution

Future platform releases may introduce additional validators, including:

- Template Validator
- Artifact Validator
- Country Validator
- Branding Validator
- Publication Validator
- Runtime Validator

All validators must conform to the Validator Contract.