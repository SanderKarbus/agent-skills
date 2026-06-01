# Research on AI Development Assistant Rules and Quality Assurance

## Objective

The purpose of this research is to investigate which instruction files are supported by modern AI development assistants and to identify software engineering practices that help ensure the quality, safety, and reliability of AI-generated code.

The research is based on official documentation and widely accepted software engineering best practices.

---

# 1. Which Instruction Files Are Supported by AI Development Tools?

Different AI development tools support different formats for project-specific instructions.

## Claude Code

Claude Code supports:

* `CLAUDE.md`
* `.claude/CLAUDE.md`

These files are used to store persistent project instructions that Claude follows throughout development.

Source:
https://docs.claude.com/en/docs/claude-code/memory

---

## GitHub Copilot

GitHub Copilot supports:

* `.github/copilot-instructions.md`
* `.github/instructions/*.instructions.md`

These files allow developers to provide repository-specific instructions that Copilot uses when generating code.

Source:
https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot

---

## AGENTS.md

AGENTS.md is a tool-agnostic instruction format designed for AI coding agents.

Its primary advantage is that it can be reused across multiple AI tools rather than being tied to a specific vendor.

Source:
https://agentsmd.io

---

# 2. How Should an AI Analyze a Project Before Making Changes?

An AI assistant should never begin by immediately generating code.

Before making any modifications, it should:

1. Inspect the repository structure.
2. Identify the technologies and frameworks being used.
3. Read relevant existing code.
4. Understand the project architecture.
5. Search for similar existing implementations.
6. Review the current test suite.

Typical files that should be examined include:

* package.json
* requirements.txt
* pyproject.toml
* go.mod
* Cargo.toml
* docker-compose.yml
* CI configuration files

This process reduces the risk of introducing inconsistent or incorrect solutions.

---

# 3. How Can Broken Code Be Prevented from Reaching the Main Branch?

Modern software development uses multiple layers of protection.

## Feature Branches

All development work should occur in a dedicated branch.

Example:

```text
feature/add-login
```

This keeps incomplete or experimental work isolated from the main branch.

---

## Pull Requests

Changes should be submitted through Pull Requests before being merged.

Pull Requests allow:

* code review;
* discussion of implementation details;
* validation of the proposed solution.

---

## Branch Protection

Branch protection rules help prevent unsafe changes from reaching production.

Typical protections include:

* blocking direct commits to main;
* requiring code reviews;
* requiring successful CI checks before merge.

Source:
https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches

---

## Required Status Checks

A Pull Request should only be mergeable when all required checks pass.

Examples include:

* automated tests;
* linting;
* build validation;
* type checking.

---

## CI Pipeline

Continuous Integration automatically validates changes whenever code is pushed or a Pull Request is opened.

Common CI tasks include:

* running tests;
* running linting tools;
* validating builds;
* performing security checks.

Source:
https://docs.github.com/en/actions

---

## Automated Tests

Automated tests verify that new changes do not break existing functionality.

---

## Linting

Linting tools help detect:

* syntax errors;
* style violations;
* potentially dangerous code patterns.

Examples:

* ESLint
* Ruff
* Pylint

---

## Type Checking

Type checking helps identify programming errors before runtime.

Example:

```text
tsc --noEmit
```

---

## Code Review

Automated tools cannot detect every issue.

Human reviewers help identify:

* business logic mistakes;
* security concerns;
* architectural problems.

Code review remains a critical quality assurance step.

---

# 4. How Can Regressions Be Prevented?

A regression occurs when a previously fixed bug reappears.

The most effective protection against regressions is a regression test.

## Regression Testing Process

When fixing a bug:

1. Create a test that reproduces the issue.
2. Verify that the test fails before the fix.
3. Implement the fix.
4. Verify that the test passes after the fix.

This ensures that future changes cannot accidentally reintroduce the same problem without detection.

Many development teams consider a bug fix incomplete if a regression test is not added.

---

# 5. Which Commands Should an AI Run Before Completing a Task?

Before marking work as complete, an AI assistant should execute all applicable quality checks.

## Tests

Examples:

```text
npm test
```

or

```text
pytest
```

---

## Linting

Examples:

```text
npm run lint
```

or

```text
ruff check .
```

---

## Type Checking

Example:

```text
tsc --noEmit
```

---

## Build Validation

Example:

```text
npm run build
```

---

## Formatting Validation

Example:

```text
prettier --check .
```

---

## Security and Dependency Checks

Examples:

```text
npm audit
```

```text
pip-audit
```

Other common tools include:

* Dependabot
* OWASP Dependency Check

These checks help identify known vulnerabilities in project dependencies.

---

# 6. How Should the Scope of AI Changes Be Limited?

One of the major risks of AI-assisted development is making unnecessarily large modifications.

The following principles help control scope.

## Modify Only Relevant Files

If the issue concerns authentication, the AI should not modify unrelated payment or notification modules.

---

## Prefer Small Changes

Smaller changes are:

* easier to review;
* easier to test;
* easier to revert.

---

## Avoid Unnecessary Refactoring

If the task is to fix a bug, the AI should not simultaneously redesign the architecture or refactor unrelated systems.

---

## Follow Existing Architecture

The AI should extend existing patterns whenever possible rather than introducing entirely new approaches.

---

# 7. When Should an AI Request User Approval?

An AI assistant should request approval before making high-impact changes.

## Database Schema Changes

Examples include:

* modifying tables;
* deleting columns;
* creating migrations.

These changes can affect existing data and application behavior.

---

## Adding Dependencies

Every new dependency introduces:

* maintenance overhead;
* security risks;
* additional project complexity.

---

## Deleting Files

Important files should never be removed without explicit approval.

---

## Public API Changes

Changes to public APIs may break existing clients and integrations.

---

## Security-Related Changes

Approval should be requested before modifying:

* authentication;
* authorization;
* tokens;
* sessions;
* access control mechanisms.

---

## Large Refactoring Efforts

Changes affecting many files, modules, or architectural components should always be approved before implementation.

---

# Conclusion

This research leads to three key conclusions:

1. AI should thoroughly analyze the existing project and architecture before generating code.
2. Broken code is best prevented from reaching the main branch through multiple quality gates, including feature branches, pull requests, branch protection, CI pipelines, automated testing, and code review.
3. AI-generated changes should remain small, focused, and thoroughly validated, while bug fixes should always include regression tests whenever possible.

---

# References

1. Anthropic Claude Code Documentation
   https://docs.claude.com/en/docs/claude-code/memory

2. GitHub Copilot Documentation
   https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot

3. GitHub Branch Protection Documentation
   https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches

4. GitHub Actions Documentation
   https://docs.github.com/en/actions

5. AGENTS.md Project
   https://agentsmd.io
