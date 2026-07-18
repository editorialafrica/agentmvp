# Repository Guide

## Purpose

This document describes the purpose and responsibility of every folder and file within the EditorialAfrica repository.

The guiding principle is simple:

> Every file should have one clear responsibility.

---

# Repository Structure

```
agentmvp/

├── README.md
├── editorial-date
├── config/
├── countries/
├── prompts/
├── templates/
├── artifacts/
├── docs/
└── google-drive/
```

---

# Root Files

## README.md

The project entry point.

Provides:

- Project overview
- Quick start guide
- Repository structure
- Daily workflow
- Current roadmap

This should be the first document every contributor reads.

---

## editorial-date

Contains the execution date for the production run.

Example:

```
2026-07-18
```

The production prompt uses this value as the temporal anchor for all generated content.

Only one date should exist in this file.

---

# config/

Contains shared configuration used during production.

Configuration files describe **how** EditorialAfrica behaves rather than **what** it writes.

---

## production.json

Defines the overall production behaviour.

Examples include:

- Output order
- Default language
- Presenter source
- Execution settings

---

## outputs.json

Lists every artifact that must be generated during a production run.

The production prompt reads this file to determine the required outputs.

---

## filenames.json

Defines the naming convention for generated artifacts.

Centralising filenames ensures consistency across all production runs.

---

## validation.json

Defines quality requirements that must be satisfied before production is complete.

Examples:

- Minimum editorials
- Required URLs
- Duplicate detection
- Required sections

---

## branding.json

Contains EditorialAfrica branding information.

Examples:

- Brand name
- Colours
- Logo filename
- Editorial disclaimer

---

## drive.json

Defines the intended folder structure for generated artifacts.

Although the MVP uses manual storage, this configuration prepares the repository for future automation.

---

# countries/

Contains country-specific editorial information.

Example:

```
countries/

    nigeria.txt
```

Each country file defines:

- Country name
- Presenter
- Approved newspapers
- Editorial focus

Only newspapers listed in the country file should be analysed.

---

# prompts/

Contains the EditorialAfrica production prompt.

```
prompts/

    MASTER_PROMPT.md
```

This is the most important file in the repository.

It is responsible for:

- Reading repository configuration
- Analysing editorials
- Generating all required artifacts
- Performing validation
- Producing the execution report

The MVP intentionally uses one production prompt.

---

# templates/

Contains reusable output templates.

Templates define the structure of generated reports.

---

## execution-report.md

Defines the format of the production execution report generated at the end of every run.

---

## story-ranking.md

Defines the structure used when ranking editorials during analysis.

---

# artifacts/

Stores generated editorial packages.

Each production run creates a folder using the execution date.

Example:

```
artifacts/

    2026-07-18/
```

This folder should contain all generated outputs for that day.

No source files should be stored here.

---

# docs/

Contains project documentation.

Current documents include:

- README
- Architecture
- Repository Guide

Additional documentation may be added as the platform evolves.

---

# google-drive/

Reserved for future automation.

The MVP does not automate storage or publishing.

This folder will contain documentation and scripts when automation is introduced in a future milestone.

---

# Repository Workflow

The repository supports the following daily workflow:

```
Update editorial-date

↓

Verify country configuration

↓

Run Gemini

↓

Generate editorial package

↓

Save outputs into artifacts/
```

The workflow remains the same regardless of the selected country.

---

# Design Guidelines

When contributing to this repository:

- Keep the repository simple.
- Prefer configuration over hardcoding.
- Avoid unnecessary folders.
- Keep documentation current.
- Preserve the MVP workflow.
- Do not introduce automation before it is required.

---

# Repository Ownership

Every file in the repository should have a clearly defined purpose.

If a file no longer serves a useful purpose, it should be removed rather than retained as a placeholder.

The goal is to maintain a repository that is easy to understand, easy to navigate, and straightforward to maintain.