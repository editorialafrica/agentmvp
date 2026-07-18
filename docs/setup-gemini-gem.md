# Google Gemini Gem Setup

## Purpose

This document explains how to configure the EditorialAfrica Gemini Gem.

---

## Step 1

Create a new Gemini Gem.

Suggested name:

EditorialAfrica Editorial Producer

---

## Step 2

Upload the repository.

Include:

- prompts/
- config/
- countries/
- templates/
- docs/

---

## Step 3

Use the production prompt.

Primary prompt:

MASTER_PROMPT.md

---

## Step 4

Select the country configuration.

Example:

countries/nigeria.txt

---

## Step 5

Update the execution date.

Modify:

editorial-date

before every production run.

---

## Step 6

Run production.

The Gem should:

- Read configuration
- Analyse editorials
- Generate outputs
- Validate results
- Produce an execution report

---

## Best Practices

- Keep repository files up to date.
- Update only the execution date between daily runs.
- Review all outputs before publication.
- Never modify generated content without editorial review.