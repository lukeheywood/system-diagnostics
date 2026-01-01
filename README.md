# System Diagnostics

**Purpose:** Practical patterns, checklists, and playbooks for diagnosing when real systems lose coherence under operational load.

This repo is part of the **ONE Glass Case**. It contains **inspection tools** (documents), not production code.

- **Audience:** senior engineers, technical hiring managers, architects
- **Status:** Active (content is intentionally compact and evidence-oriented)
- **Last verified:** 2026-01-01
- **Canonical hub:** `one-platform` (System Atlas)

## What this repo is
A small, reusable toolkit for:
- detecting *drift* (systems changing without the story changing)
- spotting *competing intents* (multiple goals fighting in one surface)
- mapping system structure so you can explain it without hand-waving

## What this repo is not
- Not an incident response runbook for a specific org
- Not a monitoring/logging product
- Not a philosophy of “coherence” — only concrete diagnostic patterns and steps

## Contents
- `playbooks/`
  - `system_mapping_playbook.md` — how to reconstruct a system map from partial signals
- `checklists/`
  - `drift_checklist.md` — black‑and‑white drift detection checklist
- `patterns/`
  - `competing_intents.md` — how competing goals show up and how to separate them safely

## Links
- ONE System Atlas (hub): `../one-platform`
- Case studies (Atlas): `../one-platform/case-studies/`
