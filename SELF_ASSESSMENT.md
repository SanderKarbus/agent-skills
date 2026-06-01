# Self-Assessment

## What was the most useful rule?

The most useful rule is **"Regression Prevention"** (Testing Rules). This rule requires that every bug fix includes a regression test that first fails before the fix and then passes after it. This ensures that old bugs do not resurface and fixes are genuinely effective. This rule is extremely powerful in practice because it automates validation for future developers.

## Which risk remains unmitigated?

The greatest remaining risk is **incorrect interpretation of business logic**. Even if AI follows AGENTS.md rules perfectly, it can misunderstand what the user actually wants to accomplish. Rules can control code quality, but not requirement correctness. To reduce this risk, human code review and clear specifications are necessary.

## What would you improve in the next version?

In the next version, I would add:

1. **Project-specific examples** - Create specialized versions of AGENTS.md for common stacks (e.g., Node.js/React, Python/FastAPI, Go/gRPC) with concrete patterns and anti-patterns from real projects.

2. **Automated quality enforcement in CI** - Enhance the CI pipeline with actual linting, type checking, and code formatting validation rules beyond just file existence checks.

3. **Pre-commit hooks guidance** - Add documentation for setting up local git hooks to prevent direct commits to main, with examples for different environments.

4. **Tighter PR template integration** - Link PR checklist items directly to AGENTS.md sections with automated validation, so every PR is audited against the ruleset.

5. **AI tool-specific variants** - Create specialized instruction files for different AI tools (CLAUDE.md, .github/copilot-instructions.md, GEMINI.md) with tool-specific syntax and capabilities.
