# Video Agent Template

Template: video-agent-template

Version: 1.0.0

Extends: agent-template v1.0.0

Status: Stable

Owner: EditorialAfrica

---

# Purpose

The Video Agent Template defines additional requirements for AI agents responsible for transforming editorial intelligence into video-ready content.

This template extends the universal runtime contract defined by `agent-template.md`.

Video agents SHALL produce scripts, narration, scene descriptions, timing, and visual guidance suitable for AI-assisted video generation.

---

# Applicable Agents

This template applies to:

- HeyGen.Agent

Future examples:

- YouTube.Agent
- Shorts.Agent
- Podcast.Agent

---

# Responsibilities

Video agents SHALL:

- transform editorial intelligence into a coherent visual narrative
- maintain factual accuracy
- preserve EditorialAfrica branding
- generate presenter-ready scripts
- generate scene-by-scene guidance
- optimise pacing for viewer retention

---

# Inputs

## Required Context

- editorialContext.enterpriseIntelligence
- contentContext
- productionContext.branding

## Optional Context

- story ranking
- visual assets
- organisation logos
- branding assets

---

# Video Structure

A video should generally include:

- Opening hook
- Programme introduction
- Headlines
- Story segments
- Closing summary
- Call to Action
- Outro

---

# Narration Standards

Narration SHALL:

- use natural spoken language
- avoid long paragraphs
- use broadcast-quality transitions
- pronounce names consistently
- maintain a professional newsroom tone

---

# Visual Standards

Every scene should specify:

- Presenter
- Background
- Visual assets
- Headlines
- Lower thirds
- B-roll suggestions
- Transitions

---

# Timing

Video agents should estimate timing for:

- Introduction
- Story segments
- Closing

Target duration should be configurable through:

config/production.json

---

# Branding

Apply branding from:

branding.json

Examples:

- logos
- typography
- colours
- lower thirds
- intro/outro identity

---

# Validation

Validate:

✓ script completeness

✓ narration flow

✓ visual continuity

✓ branding

✓ scene numbering

✓ estimated duration

---

# Generated Artifacts

Examples

artifacts/video-script.md

artifacts/scene-list.md

artifacts/heygen-prompt.md

---

# Completion Criteria

Execution completes only when:

✓ Script complete

✓ Scene breakdown complete

✓ Timing estimated

✓ Branding applied

✓ Validation passed

✓ Context updated

✓ Artifacts registered