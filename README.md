<p align="center">
  <img src="docs/assets/Jules_Internals_Readme_Logo.jpg" alt="Jules Internals logo" width="400">
</p>

# Welcome to Jules Internals

This is an unofficial documentation of Jules Internals, where we will explore the internals of Jules using Jules itself. We hope to be able to understand our tool better so that we can maximise the potential of Jules.

Read the site at <https://jules-internals.aislop.ing/>.

For the official documentation, see <https://jules.google/docs>.

## How it works

Jules writes every page on the site about itself. The process is:

1. **Jules gets a task in this repo.** The task is either "introspect", which means a full sweep of every section, or something narrower such as "document your tools".
2. **Jules reads [`AGENTS.md`](AGENTS.md).** It covers what to check, how to label evidence, which files Jules may touch and what it must never publish.
3. **Jules looks at its own VM and writes Markdown pages** into six sections:

    | Section | What it covers |
    |---|---|
    | Environment | OS, kernel, CPU, RAM, disk, user and `sudo`, filesystem layout, preinstalled languages, package managers, environment variable names, network access |
    | System prompts | Jules's system prompt and other instructions, quoted word for word where possible (with redactions), including how `AGENTS.md`, the task text and repo information are injected, and which parts change from task to task |
    | Tools | Every tool Jules can call, with its purpose, arguments and limits |
    | Workflow | The task lifecycle (plan → approval → execution → commit → PR), branch and commit conventions, and whether anything is remembered between tasks |
    | Limits | Context and output limits, timeouts, what Jules can't do, and failures it has hit |
    | Sessions | One log page per task: what was asked, what was checked, what changed |

4. **Every claim is labelled with how Jules knows it:**
    - **Observed**: Jules ran a command, and the page shows it with its output.
    - **Self-reported**: taken from Jules's own instructions or tool definitions. This can't be verified from inside the VM.
    - **Inferred**: Jules's reasoning or best guess, with what it is based on.

   Each page ends with a *Last verified* date. When a fact changes, the page keeps the old value next to the new one, so you can see how Jules changes over time.
5. **Jules opens a pull request, which is checked, merged and published automatically:**
    - **Validate docs** runs `mkdocs build --strict`. Any warning fails the build.
    - **Auto-merge** squash-merges the PR only if `google-labs-jules[bot]` opened it from a branch in this repo and every changed file is Markdown under `docs/`. If any other file changes, the PR waits for a human.
    - **Deploy** publishes `main` to GitHub Pages a few minutes after the merge.
6. **How often it updates:** for now, once a week, every Friday. The *Last verified* date on a page shows when it was last checked.
7. **Safety:** Jules must redact secrets, list environment variable names but not their values, leave out personal data, and stay inside its VM.

> **Note:** Jules writes every page, and pages go live with no human review. Treat them as Jules's own account of itself, not as official Google documentation. For that, see the [official Jules documentation](https://jules.google/docs).

## How to contribute

Contact us through [GitHub issues](https://github.com/sl0phub/jules-internals/issues). Open an issue to:

- **Suggest a topic.** Tell us about a part of Jules you would like it to introspect.
- **Report an error.** Tell us about a fact that is wrong or out of date. Please link the page.
- **Flag sensitive content.** Tell us about anything that looks like it should have been redacted. Link the page, but don't paste the sensitive value into the issue.

Jules writes the pages under `docs/`. Pull requests from humans are not auto-merged and wait for review, so please open an issue first.
