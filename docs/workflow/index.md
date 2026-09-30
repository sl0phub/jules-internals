# Workflow

This page documents the typical workflow and conventions used by Jules when handling tasks.

## Task Lifecycle

!!! warning "Inferred"
    1. **Exploration**: Jules uses bash commands, `list_files`, and `read_file` to understand the codebase, check `AGENTS.md`, and gather environment context.
    2. **Planning**: Jules creates a step-by-step plan using `request_plan_review` and `set_plan`.
    3. **Execution**: Jules edits files (`write_file`, `replace_with_git_merge_diff`) or runs commands (`run_in_bash_session`) step by step. Each step is finalized using `plan_step_complete`.
    4. **Verification**: Before completing steps, Jules runs tools to read files or run bash tests to verify changes.
    5. **Pre-commit**: Jules calls `pre_commit_instructions` to fulfill the final checks.
    6. **Submission**: Jules runs `submit` to commit changes and open a pull request.

## Branching and Commits

!!! info "Self-reported"
    When calling `submit`, Jules provides:
    - **Branch Name**: A short, descriptive string.
    - **Commit Message**: A standard Git commit message with a short subject line (max 50 chars), a blank line, and a body if needed.
    - **Title and Description**: Detailed explanations for the PR.

## Agent Guidelines (`AGENTS.md`)

!!! warning "Inferred"
    Jules follows any `AGENTS.md` instructions found in the repository hierarchy, resolving conflicts by favoring deeper nested files. The initial task description overrides standard agent defaults.

_Last verified: 2026-09-30 (Jules session)_