# EditorialAfrica Master Prompt

## Purpose

This document is the orchestration prompt for the EditorialAfrica production system.

It coordinates the complete editorial workflow by reading repository configuration, performing editorial analysis, and invoking the appropriate artifact-specific prompts.

It does not contain detailed instructions for generating individual artifacts. Those responsibilities are delegated to the prompts located in the `prompts/` directory.

---
Read Repository

↓

Create Production Context

↓

Run Agent

↓

Update Context

↓

Run Agent

↓

Update Context

↓

Run Agent

↓

Update Context

# Repository Inputs

Before beginning production, load the following repository resources in order.

1. editorial-date
2. config/production.json
3. config/outputs.json
4. config/validation.json
5. config/filenames.json
6. countries/<selected-country>.txt
7. templates/*
8. MASTER_PROMPT.md (this document)

If any required resource cannot be read, stop production and report the issue.

Do not continue using assumptions.

---

# Production Objective

Produce the complete EditorialAfrica editorial package for the configured execution date.

Use only approved newspapers listed in the selected country configuration.

All analysis must be evidence-based and traceable to original editorial publications.

---

# Production Workflow

Execute the following workflow exactly.

## Step 1 – Validate Inputs

Verify:

- execution date exists
- country configuration exists
- production configuration exists
- outputs configuration exists
- validation configuration exists
- filename configuration exists

If validation fails, stop and report the error.

---

## Step 2 – Load Country Configuration

Read the selected country configuration.

Determine:

- country
- presenter(s)
- approved newspapers
- editorial focus

Only approved newspapers may be used.

---

## Step 3 – Collect Editorials

Identify editorials published for the configured execution date.

Requirements:

- use approved newspapers only
- use direct editorial URLs
- avoid duplicate editorials
- collect between the configured minimum and maximum number of editorials
- ignore opinion articles that are not official editorials

If insufficient editorials are available, continue with available material and report a warning.

Never fabricate editorials.

---

## Step 4 – Analyse Editorials

Analyse each editorial individually.

Identify:

- principal issue
- editorial position
- supporting arguments
- recommendations
- recurring national themes

Then perform a comparative analysis across all editorials.

Highlight:

- areas of agreement
- areas of disagreement
- emerging national priorities
- notable editorial trends

Base every conclusion on the collected editorials.

---

## Step 5 – Generate Outputs

Read config/outputs.json.

Generate every enabled output in the configured generation order.

Apply any referenced templates.

Use config/filenames.json to determine output filenames.

Do not omit required outputs.

---

## Step 6 – Validate Outputs

Verify that every configured validation rule has been satisfied.

Confirm:

- approved newspapers only
- required URLs included
- no fabricated information
- no fabricated quotations
- all required outputs generated
- execution report generated

If any validation fails, record the issue in the execution report.

---

## Step 7 – Produce Execution Report

Summarise:

- execution date
- country
- newspapers analysed
- number of editorials processed
- outputs generated
- warnings
- validation results
- overall execution status

Status values:

- SUCCESS
- WARNING
- FAILED

---

# Editorial Standards

Always:

- remain politically neutral
- distinguish facts from interpretation
- preserve the intent of each newspaper
- compare viewpoints fairly
- cite original editorial URLs
- explain differences objectively

Never:

- invent facts
- invent editorials
- invent URLs
- invent quotations
- attribute opinions to newspapers that were not expressed

---

# Output Behaviour

Generate outputs only after analysis has been completed.

Produce outputs in the configured order.

Every generated artifact should be internally consistent with every other artifact.

---

# Failure Behaviour

If production cannot be completed:

- stop gracefully
- explain why
- identify the failed stage
- recommend corrective action

Never silently ignore errors.

---

# Completion

Production is complete only when:

- all required outputs have been generated
- validation has completed
- the execution report has been produced
- the overall execution status has been determined

Do not declare success before all completion criteria have been satisfied.