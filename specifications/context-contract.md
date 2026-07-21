# Context Contract

**Document:** Context Contract  
**Version:** 1.0.0  
**Status:** Stable  
**Owner:** EditorialAfrica  
**Classification:** Platform Contract

---

# 1. Purpose

The Context Contract defines the structure, ownership, lifecycle, governance, and usage rules for all shared runtime contexts within the EditorialAfrica AI Platform.

Contexts provide the platform's shared memory during execution and enable independent AI agents to collaborate without direct communication.

This contract ensures consistency, traceability, determinism, and separation of concerns across all platform executions.

---

# 2. Scope

This contract governs:

- Context architecture
- Context ownership
- Context lifecycle
- Context versioning
- Read/write permissions
- Validation
- Context evolution
- Runtime behavior

It applies to every context within the platform.

---

# 3. Definition

A Context is a structured, versioned, shared data store representing a specific domain of runtime information.

Contexts SHALL contain state.

Contexts SHALL NOT contain executable logic.

Contexts SHALL NOT contain prompt instructions.

Contexts SHALL NOT define pipeline behavior.

---

# 4. Guiding Principles

The Context architecture follows the following principles.

## 4.1 Single Responsibility

Each context SHALL represent exactly one business domain.

Examples:

| Context | Responsibility |
|----------|----------------|
| Production | Pipeline execution |
| Editorial | Editorial intelligence |
| Content | Generated publication content |
| Execution | Runtime metrics |

---

## 4.2 Shared Communication

Contexts are the only supported communication mechanism between agents.

Agents SHALL NOT communicate directly.

Agents SHALL NOT depend on implementation details of other agents.

---

## 4.3 Ownership

Every context SHALL have exactly one owner.

The owner is responsible for:

- schema evolution
- validation
- lifecycle
- documentation
- compatibility

Ownership SHALL be declared in:

```
config/context-ownership.json
```

---

## 4.4 Structured Data

Contexts SHALL be machine-readable.

Contexts SHALL conform to a published schema.

Contexts SHALL remain deterministic.

---

## 4.5 Traceability

Every context update SHALL be attributable to:

- an agent
- a pipeline execution
- a timestamp

---

# 5. Context Registry

Every context SHALL be registered.

Example registry:

| Context | Owner |
|----------|-------|
| Production | Pipeline Engine |
| Editorial | EditorialSummary.Agent |
| Content | Publishing Agents |
| Execution | ExecutionReport.Agent |

---

# 6. Standard Metadata

Every context SHALL contain metadata.

Example

```json
{
  "context": "editorial",
  "version": "1.0.0",
  "owner": "EditorialSummary.Agent",
  "schemaVersion": "1.0.0",
  "status": "Active",
  "created": "",
  "updated": ""
}
```

---

# 7. Context Structure

Every context SHALL follow the same high-level structure.

```
Metadata

↓

Permissions

↓

Sections

↓

Validation

↓

Audit
```

Only the **Sections** component varies between context types.

---

# 8. Context Lifecycle

Every context follows the same lifecycle.

```
Definition

↓

Initialization

↓

Population

↓

Consumption

↓

Validation

↓

Completion

↓

Archival
```

Contexts SHALL be initialized before any agent executes.

---

# 9. Context Initialization

The Pipeline Engine SHALL initialize every required context.

Initialization SHALL include:

- metadata
- ownership
- schema validation
- version validation

Contexts SHALL exist before the first AI agent executes.

---

# 10. Reading Contexts

Agents MAY read any context declared within their contract.

Agents SHALL NOT depend upon undocumented context fields.

Agents SHOULD treat contexts as immutable while reading.

---

# 11. Updating Contexts

Only authorized agents MAY update a context.

Updates SHALL:

- preserve schema validity
- preserve metadata
- maintain traceability

Unauthorized updates SHALL fail validation.

---

# 12. Context Permissions

Each context SHALL define permissions.

Permissions include:

| Permission | Description |
|------------|-------------|
| Read | Agent may read |
| Write | Agent may update |
| Owner | Agent governs context |

Permissions SHALL be explicitly declared.

---

# 13. Validation

Every context SHALL be validated.

Validation includes:

- schema
- ownership
- metadata
- required fields
- permissions
- version compatibility

Validation SHALL occur:

- during initialization
- before updates
- after updates

---

# 14. Versioning

Contexts follow Semantic Versioning.

## Patch

Metadata improvements.

Documentation updates.

---

## Minor

Backward-compatible additions.

New optional fields.

---

## Major

Breaking schema changes.

Removed fields.

Renamed sections.

Changed ownership model.

---

# 15. Schema Compliance

Every context SHALL conform to:

```
schemas/context.schema.json
```

No context SHALL introduce undocumented fields.

---

# 16. Audit Trail

Every context SHALL maintain an audit history.

Minimum audit information:

- Updated By
- Timestamp
- Version
- Pipeline Run
- Change Summary

Audit data SHALL NOT affect business logic.

---

# 17. Context Evolution

Contexts SHOULD evolve through schema versioning.

Existing fields SHOULD NOT be removed during minor releases.

Deprecated fields SHOULD remain available for one platform release.

---

# 18. Runtime Behavior

During execution contexts SHALL behave as:

- shared
- deterministic
- versioned
- validated
- owned

Contexts SHALL remain available throughout pipeline execution.

---

# 19. Architectural Constraints

Contexts SHALL NOT:

- execute prompts
- contain business logic
- reference pipeline stages
- invoke agents
- contain configuration
- duplicate artifact content

---

# 20. Compliance

A context is compliant when:

✓ Metadata exists.

✓ Schema is valid.

✓ Owner is defined.

✓ Permissions are defined.

✓ Required sections exist.

✓ Validation succeeds.

✓ Version is compatible.

---

# 21. Security

Contexts SHALL NOT contain:

- repository secrets
- authentication credentials
- API keys
- runtime tokens

Sensitive information SHALL be referenced through secure platform configuration.

---

# 22. Extensibility

New contexts MAY be introduced without modifying existing contexts.

Examples:

- Analytics Context
- Publishing Context
- Translation Context
- Audience Context

Every new context SHALL conform to this contract.

---

# 23. Relationship to Other Specifications

| Specification | Relationship |
|---------------|--------------|
| Platform Specification | Defines platform governance |
| Architecture | Defines platform structure |
| Pipeline Contract | Initializes and manages contexts |
| AI Agent Contract | Defines how agents consume contexts |
| Template Contract | Defines reusable context templates |

This contract governs the shared state layer of the EditorialAfrica platform.

---

# 24. Context Interaction Model

```
Pipeline

↓

Initialize Contexts

↓

Agent Reads Context

↓

Agent Processes

↓

Agent Updates Context

↓

Next Agent Reads Updated Context

↓

Execution Complete
```

This interaction model ensures loose coupling between agents while maintaining a consistent shared state.

---

# 25. Summary

Contexts are the shared runtime memory of the EditorialAfrica AI Platform. They provide a governed, versioned, and validated mechanism for exchanging information between independent AI agents without introducing direct dependencies.

By enforcing ownership, schema validation, lifecycle management, and strict separation of responsibilities, the Context Contract ensures that platform state remains deterministic, traceable, extensible, and maintainable as the EditorialAfrica platform evolves.