# Template Contract

**Document:** Template Contract  
**Version:** 1.0.0  
**Status:** Stable  
**Owner:** EditorialAfrica  
**Classification:** Platform Contract

---

# 1. Purpose

The Template Contract defines the governance, structure, lifecycle, versioning, validation, and compliance requirements for every template within the EditorialAfrica AI Platform.

Templates establish the development standards for reusable platform components and ensure architectural consistency across AI agents, contexts, artifacts, reports, and future platform extensions.

Templates are development assets and are never executed as part of the production pipeline.

---

# 2. Scope

This contract applies to every template contained within:

```
templates/
```

Including:

- Agent Templates
- Editorial Agent Templates
- Social Agent Templates
- Video Agent Templates
- Report Agent Templates
- Context Templates
- Artifact Templates
- Operational Templates

Future template categories SHALL conform to this contract.

---

# 3. Definition

A Template is a reusable specification that defines the structure, metadata, responsibilities, and required sections for a platform component.

Templates SHALL:

- define standards
- promote consistency
- support reuse
- guide development
- simplify maintenance

Templates SHALL NOT:

- execute
- orchestrate the pipeline
- contain runtime state
- replace AI agents

---

# 4. Design Principles

## 4.1 Templates Are Specifications

Templates define structure and governance.

They do not define runtime behaviour.

---

## 4.2 Templates Are Never Executed

Only agents within:

```
prompts/
```

may be executed.

Templates SHALL NEVER participate in runtime execution.

---

## 4.3 Reusability

Templates SHALL maximize reuse.

Duplicated structures SHOULD be extracted into shared templates.

---

## 4.4 Consistency

Templates SHALL ensure every platform component follows a consistent structure.

---

## 4.5 Extensibility

Specialized templates SHOULD extend generic templates.

Example:

```
Agent Template

↓

Editorial Agent Template

↓

EditorialSummary.Agent
```

---

# 5. Template Categories

The EditorialAfrica platform supports the following template categories.

| Category | Purpose |
|----------|----------|
| Agent | Base runtime contract |
| Editorial | Editorial processing |
| Social | Social publishing |
| Video | Video generation |
| Report | Operational reporting |
| Context | Shared context structure |
| Artifact | Generated output structure |

Future categories MAY be introduced.

---

# 6. Template Hierarchy

```
Agent Template
│
├── Editorial Agent
├── Social Agent
├── Video Agent
└── Report Agent

Context Template

Artifact Template
```

Specialized templates inherit the requirements of their parent templates.

---

# 7. Standard Metadata

Every template SHALL begin with metadata.

Example:

```yaml
Template:
Category:
Version:
Status:
Owner:
Extends:
Last Updated:
```

Mandatory fields:

- Template
- Category
- Version
- Status
- Owner
- Last Updated

Optional:

- Extends
- Description
- Compatibility

---

# 8. Versioning

Templates SHALL follow Semantic Versioning.

## Patch

Documentation improvements.

Formatting corrections.

Examples.

---

## Minor

Backward-compatible additions.

New optional sections.

Additional guidance.

---

## Major

Breaking structural changes.

Removed sections.

Renamed metadata.

Changed lifecycle.

---

# 9. Template Lifecycle

Every template follows the lifecycle below.

```
Draft

↓

Review

↓

Approved

↓

Stable

↓

Deprecated

↓

Archived
```

Template status SHALL be declared in metadata.

---

# 10. Ownership

Every template SHALL have exactly one owner.

The owner is responsible for:

- maintenance
- versioning
- compatibility
- documentation
- review

Ownership SHALL be explicit.

---

# 11. Template Compliance

A template is compliant when:

✓ Metadata complete

✓ Version declared

✓ Category declared

✓ Required sections exist

✓ Structure consistent

✓ Compatible with parent template

✓ Validation passes

---

# 12. Agent Conformance

Every executable AI Agent SHALL declare:

```yaml
Template:
Template Version:
```

Repository validation SHALL verify:

- template exists
- template version compatible
- template category correct
- required sections implemented

---

# 13. Context Conformance

Every context SHALL conform to:

```
templates/context-template.json
```

Context validation SHALL ensure structural compliance.

---

# 14. Artifact Conformance

Every artifact SHALL conform to:

```
templates/artifact-template.md
```

Artifacts SHALL preserve the required metadata and structure.

---

# 15. Repository Validation

Repository validation SHALL verify:

✓ Template exists

✓ Metadata complete

✓ Version valid

✓ Duplicate names

✓ Broken inheritance

✓ Invalid references

✓ Orphan templates

✓ Conformance declarations

---

# 16. Template Drift

Template drift occurs when a platform component no longer conforms to its declared template.

Examples include:

- Missing sections
- Missing metadata
- Incorrect template version
- Deprecated template usage
- Invalid inheritance

Template drift SHALL be reported as a validation error.

---

# 17. Change Management

Templates SHALL only change when platform contracts change.

Valid reasons include:

- New platform capability
- Updated lifecycle
- New metadata
- Validation improvements
- Governance changes

Templates SHALL NOT change because of:

- Better prompt wording
- Editorial improvements
- Social media optimisation
- Country-specific content

These belong in AI Agents.

---

# 18. Updating Templates

Template updates SHALL follow this workflow.

```
Platform Contract Change

↓

Update Template

↓

Increase Version

↓

Update CHANGELOG

↓

Update Dependent Components

↓

Repository Validation

↓

Release
```

---

# 19. Backward Compatibility

Minor template releases SHOULD remain backward compatible.

Deprecated templates SHOULD remain available for at least one platform release before removal.

Major releases MAY introduce breaking changes.

---

# 20. Security

Templates SHALL NOT:

- contain secrets
- contain runtime credentials
- redefine pipeline behaviour
- execute repository logic

Templates are specifications only.

---

# 21. Extensibility

Future template categories MAY include:

- Podcast
- Newsletter
- Translation
- Analytics
- SEO
- Country Pack
- Publishing Workflow

New template categories SHALL conform to this contract.

---

# 22. Relationship to Other Specifications

| Specification | Relationship |
|---------------|--------------|
| Platform Specification | Platform governance |
| Architecture | Platform structure |
| Pipeline Contract | Runtime orchestration |
| Context Contract | Shared state |
| AI Agent Contract | Executable components |
| Artifact Contract | Generated outputs |

The Template Contract governs reusable development specifications.

---

# 23. Summary

Templates are reusable platform specifications that define the standard structure, metadata, lifecycle, and governance of EditorialAfrica platform components.

They promote consistency, reduce duplication, simplify maintenance, and ensure every AI agent, context, and artifact conforms to a common architectural standard.

Templates are never executed; they exist solely to guide development and repository governance.