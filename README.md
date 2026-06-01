# Skilled-Agent AI Governance Project

## Overview

This repository contains an AI engineering ruleset designed to control and standardize AI-assisted software development.

The goal is to prevent:
- broken code being merged into main
- uncontrolled refactoring by AI
- missing tests or CI validation
- security and dependency issues
- regression bugs reappearing

---

## Core files

### AGENTS.md
Main AI ruleset defining:
- coding rules
- architecture constraints
- testing requirements
- git workflow rules
- scope control rules
- security rules

### AI_QUALITY_PLAN.md
Explains:
- risks of AI-assisted development
- mitigation strategies
- CI/CD and branch protection role

### ai_changelog.md
Append-only log of all AI-driven changes.

### .github/workflows/ci.yml
Basic CI pipeline ensuring repository validity.

### .github/pull_request_template.md
PR checklist for enforcing quality gates.

---

## Development / validation commands

(Example environment – adjust if needed)

```bash
npm install
npm run test
npm run lint
npm run build