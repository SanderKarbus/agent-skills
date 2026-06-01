# AI QUALITY PLAN

## 1. Selected AI rules file

The project uses **AGENTS.md** as the primary AI instruction file.

This choice is based on the following reasons:

- It is tool-agnostic (works with Claude, Cursor, Copilot, GPT, etc.)
- It supports reusable cross-project AI behavior rules
- It is suitable for both small and large-scale projects
- It aligns with modern AI-assisted development workflows
- It can be combined with CI/CD and branch protection systems

The goal is to define a reusable AI engineering contract rather than a tool-specific configuration.

---

## 2. Sources used

The rules and structure are based on established software engineering and AI development practices:

- GitHub Copilot instructions and AGENTS.md concepts
- Claude Code persistent instruction patterns (CLAUDE.md)
- Karpathy-style agent workflow principles (context-first reasoning)
- CI/CD best practices (linting, testing, build validation)
- Git branch protection and pull request workflows
- General software engineering principles:
  - Clean architecture
  - Test-driven development (TDD)
  - Secure coding practices (least privilege principle)

---

## 3. Main risks when using AI in development

### 3.1 Incorrect context interpretation
AI may:
- modify unrelated files
- misunderstand business logic
- assume incorrect requirements

---

### 3.2 Large and uncontrolled changes
AI may:
- perform unnecessary refactoring
- modify multiple systems at once
- introduce regressions

---

### 3.3 Ignoring quality gates
AI may:
- skip running tests
- ignore linting errors
- produce failing builds

---

### 3.4 Hallucinated implementations
AI may:
- use non-existent APIs
- assume missing infrastructure (queues, caches, services)
- invent incorrect system behavior

---

## 4. How AGENTS.md mitigates these risks

### 4.1 Structured workflow enforcement
The agent must:
- analyze repository context before changes
- follow existing architecture
- avoid assumptions without confirmation

---

### 4.2 Scope limitation
Rules enforce:
- minimal diffs
- isolated changes
- prohibition of unrelated refactoring

---

### 4.3 Testing and validation enforcement
The rules require:
- running tests before completion
- linting and build validation
- adding regression tests for bug fixes

---

### 4.4 Security and stability constraints
The agent is prevented from:
- committing secrets
- removing authentication logic
- introducing unchecked dependencies

---

## 5. Required commands before completion

Before marking any task as complete, the following must pass:

- Unit tests (e.g. `npm test`)
- Lint checks (e.g. `npm run lint`)
- Build process (e.g. `npm run build`)
- Type checking (if applicable, e.g. `tsc --noEmit`)

If any step fails, the task is not complete.

---

## 6. Regression prevention strategy

To prevent regressions:

- Every bug fix must include a regression test
- Tests must fail before the fix and pass after it
- Existing tests must not be removed without justification
- CI must execute the full test suite automatically

---

## 7. Quality gates (CI / PR / branch protection)

### 7.1 CI pipeline
Must run automatically on every pull request:
- tests
- linting
- build validation

---

### 7.2 Branch protection
- Direct commits to `main` are blocked
- Merging requires successful CI checks

---

### 7.3 Code review requirement
- At least one approval is required before merging
- Review must validate correctness and scope

---

## 8. Additional required safeguards

AI rules alone are not sufficient. The system also requires:

- CI enforcement of tests and linting
- Branch protection rules
- Pull request templates with checklists
- Required status checks (CI gates)
- Conventional commit discipline

---

## 9. Ensuring stability of existing functionality

System stability is maintained through:

- Regression tests
- Minimal and isolated changes
- CI enforcement
- Code review process
- Strict “no unrelated refactoring” rule

---

## 10. Summary

The AGENTS.md file reduces risks in AI-assisted development but does not guarantee correctness.

Real code quality is achieved through the combination of:

> AI rules + testing + CI pipelines + branch protection + human review

---

## 11. Self-assessment

This ruleset improves AI-assisted development by enforcing structured workflows and reducing unpredictable behavior.

The main remaining risk is incorrect interpretation of business requirements, which cannot be fully eliminated through rules alone.

Future improvements would include:
- project-specific CI integration examples
- tighter coupling between rules and automated checks
- PR templates enforcing AI compliance checks

Overall, the system significantly improves reliability, maintainability, and safety of AI-generated code.
