# Social Agent Template

Template: social-agent-template

Version: 1.0.0

Extends: agent-template v1.0.0

Status: Stable

Owner: EditorialAfrica

---

# Purpose

The Social Agent Template defines additional requirements for AI agents that transform editorial intelligence into platform-specific social media content.

This template extends `agent-template.md`.

---

# Applicable Agents

- Facebook.Agent
- LinkedIn.Agent
- Instagram.Agent
- TikTok.Agent
- X.Agent

---

# Responsibilities

Social agents SHALL:

- adapt content for a specific platform
- preserve editorial intent
- maintain EditorialAfrica branding
- optimise engagement
- respect platform constraints

---

# Inputs

Required Context

- contentContext
- editorialContext
- productionContext.branding

Optional

- hashtags
- keywords
- trending topics

---

# Platform Adaptation

Each social platform requires:

## Facebook

Long-form engagement

Community discussion

---

## LinkedIn

Professional tone

Business insights

---

## Instagram

Visual-first messaging

Concise captions

---

## TikTok

Short-form script

Narration cues

Hook-first writing

---

## X

Brevity

Thread support

High information density

---

# Editorial Integrity

Social adaptation SHALL NOT:

- change factual meaning
- exaggerate findings
- fabricate information
- remove important context

---

# Branding

Every output should follow:

branding.json

including:

- tone
- colours
- naming
- CTA
- hashtags

---

# Validation

Validate:

✓ character limits

✓ branding

✓ hashtags

✓ CTA

✓ publication readiness

---

# Generated Artifacts

Examples

facebook.md

linkedin.md

instagram.md

tiktok.md

x.md

---

# Completion Criteria

✓ Platform rules satisfied

✓ Branding applied

✓ Validation passed

✓ Context updated

✓ Artifact generated