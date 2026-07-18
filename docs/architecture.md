# EditorialAfrica MVP Architecture

## Overview

EditorialAfrica is an AI-assisted editorial production platform that generates a complete daily editorial package from the editorials published by approved newspapers within a selected African country.

The platform is intentionally designed to be simple, repeatable, and configuration-driven.

The MVP uses a single Google Gemini Gem, one production prompt, one country configuration, and one execution date to generate all editorial deliverables.

---

# Architecture Principles

The MVP is built around the following principles:

1. Simplicity over complexity.
2. One master production prompt.
3. Configuration over hardcoding.
4. Repeatable daily workflow.
5. Human review before publication.
6. Editorial integrity above automation.

The objective is to prove a reliable editorial workflow before introducing automation.

---

# High-Level Architecture

```
                 EditorialAfrica Repository

        ┌─────────────────────────────────────────┐
        │                                         │
        │  editorial-date                         │
        │  countries/                             │
        │  config/                                │
        │  prompts/                               │
        │  templates/                             │
        └─────────────────────────────────────────┘
                          │
                          ▼
                 Google Gemini Gem
                          │
                          ▼
             Editorial Production Prompt
                          │
                          ▼
              Daily Editorial Generation
                          │
                          ▼
                  Generated Artifacts
```

---

# Repository Components

## editorial-date

Defines the production date.

Example

```
2026-07-18
```

This becomes the temporal reference for the entire production run.

---

## countries/

Contains country-specific editorial configuration.

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

Only newspapers listed in the country file may be used.

---

## config/

Contains shared production configuration.

These files define how EditorialAfrica behaves rather than what it writes.

Examples include:

- Branding
- Output definitions
- Validation rules
- Filename conventions
- Production settings

---

## prompts/

Contains the single master production prompt.

The production prompt is responsible for:

- Reading repository configuration
- Analysing editorials
- Producing every required artifact
- Performing validation
- Reporting execution status

The MVP intentionally uses one prompt instead of multiple prompt chains.

---

## templates/

Contains reusable output templates.

Templates define the expected structure of generated reports.

---

## artifacts/

Contains all generated content.

Each production run creates a dated folder.

Example

```
artifacts/

    2026-07-18/

        Editorial Summary

        Comparative Analysis

        HeyGen Script

        Facebook

        LinkedIn

        Instagram

        TikTok

        X
```

---

# Production Workflow

EditorialAfrica follows the same workflow every day.

```
Update execution date
        │
        ▼
Verify country configuration
        │
        ▼
Open Gemini Gem
        │
        ▼
Load repository
        │
        ▼
Read production prompt
        │
        ▼
Analyse editorials
        │
        ▼
Generate editorial package
        │
        ▼
Save artifacts
```

The workflow never changes.

Only the execution date and country configuration change.

---

# Runtime Inputs

Every production run is driven by three inputs.

## 1. Execution Date

The production date.

## 2. Country Configuration

Defines the newspapers and presenter.

## 3. Shared Configuration

Defines production behaviour.

No other runtime inputs are required.

---

# Editorial Production Pipeline

The production prompt performs the following sequence.

```
Read Repository

↓

Load Configuration

↓

Read Country

↓

Identify Approved Newspapers

↓

Collect Editorials

↓

Analyse Editorial Positions

↓

Rank Stories

↓

Generate Outputs

↓

Validate Outputs

↓

Generate Execution Report
```

Each execution follows the same sequence.

---

# Generated Outputs

Every production run generates:

1. Editorial Summary
2. Comparative Analysis
3. HeyGen Script
4. Facebook
5. LinkedIn
6. Instagram
7. TikTok
8. X

No output is optional during the MVP.

---

# Validation

Before the production run is considered complete, Gemini verifies:

- Approved newspapers only
- Correct execution date
- Required URLs included
- No duplicated editorials
- All required outputs generated
- Editorial package complete

If any requirement cannot be satisfied, Gemini reports the issue rather than inventing missing information.

---

# Human Review

EditorialAfrica is an AI-assisted platform.

All generated content should be reviewed by a human editor before publication.

The AI assists the editorial process but does not replace editorial judgement.

---

# Current MVP Scope

Included:

- Single country execution
- Single master production prompt
- Daily editorial generation
- Configuration-driven workflow
- Manual execution using Gemini

Not Included:

- Scheduled execution
- Google Drive automation
- API integrations
- Automatic publishing
- Multi-country execution
- Continuous monitoring

These capabilities will be introduced in future milestones after the editorial workflow has been validated.

---

# Future Evolution

Once the MVP has demonstrated consistent editorial quality, future milestones may introduce:

- Automated artifact storage
- Scheduled daily execution
- Additional country configurations
- Publishing integrations
- Operational monitoring

These enhancements will build upon the architecture described in this document without changing the core editorial workflow.

---

# Summary

EditorialAfrica is intentionally designed as a simple, configuration-driven editorial production platform.

The repository provides the production rules.

Google Gemini performs the editorial analysis.

Human editors retain final editorial responsibility.

This balance keeps the MVP easy to understand, straightforward to operate, and ready to evolve through future milestones.