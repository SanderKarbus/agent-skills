# Skilled-Agent AI Governance Project

## Overview

This repository defines a universal AI engineering ruleset for controlling and standardizing AI-assisted software development.

It is NOT a runtime application. It is a governance and quality control system used to enforce safe AI behavior in software projects.

---

## Purpose

The main goal of this repository is to reduce risks in AI-assisted development:

- Prevent broken code from reaching main
- Prevent uncontrolled refactoring
- Enforce regression safety
- Ensure CI and quality gates are respected
- Prevent security and dependency issues
- Maintain predictable AI behavior

---

## Core Components

### AGENTS.md
Defines the main AI behavior rules:
- code generation rules
- architecture constraints
- scope control
- testing requirements
- security rules
- git workflow rules

---

### AI_QUALITY_PLAN.md
Documents:
- risks of AI-assisted development
- mitigation strategies
- role of CI, PR workflow, and branch protection

---

### ai_changelog.md
Append-only log of all AI-driven changes and decisions.

---

### .github/workflows/ci.yml
CI pipeline that validates repository structure and ensures required governance files exist.

---

### .github/pull_request_template.md
PR checklist enforcing:
- CI pass requirement
- scope control
- regression safety
- AI compliance rules

---

## Validation Model

This repository is validated through CI only.

There is no runtime build system, no application execution, and no local development server.

All validation is structural and governance-based.

---

## Key Principle

> AI behavior must be constrained by rules, not trust.

This system combines:

- AI rules (AGENTS.md)
- CI validation
- PR enforcement
- changelog tracking

to ensure safe and predictable AI-assisted development.

# CI Validation Proof

<img width="1840" height="804" alt="image" src="https://github.com/user-attachments/assets/32517933-69a9-413d-8f94-1276d730276e" />
