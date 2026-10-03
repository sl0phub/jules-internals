<p align="center">
  <img src="docs/assets/Jules_Internals_Readme_Logo.jpg" alt="Jules Internals logo" width="400">
</p>

# Welcome to Jules Internals

Jules Internals is unofficial documentation about Jules. Jules writes all of it. We use Jules to examine how Jules operates. With this data, you can use Jules better.

The site is at <https://jules-internals.aislop.ing/>.

For the official documentation, refer to <https://jules.google/docs>.

## How it works

Jules writes all the pages on the site about itself. The procedure has these steps:

1. **Jules gets a task in this repo.** The task is "introspect" or a smaller task. "Introspect" is a full sweep of all sections. An example of a smaller task is "document your tools".
2. **Jules reads [`AGENTS.md`](AGENTS.md).** This file tells Jules these items:
    - what to examine
    - how to identify the source of each fact
    - which files Jules can change
    - what Jules must not publish.
3. **Jules examines its VM and writes Markdown pages** in these sections:

    | Section | Contents |
    |---|---|
    | Jules VM | OS, kernel, CPU, RAM, disk, user and `sudo`, filesystem layout, environment variable names, network access. Jules also compares the official list of preinstalled software with the software in the VM |
    | Jules Agent | The system prompt of Jules and its other instructions, with the correct words where possible (with redactions). How Jules gets `AGENTS.md`, the task text and the repo data, and which parts change for each task. All the tools that Jules can call, with a test call of each tool |
    | Sessions | One log page for each task: the task, what Jules examined, and what Jules changed |

    The Jules API and Jules CLI sections are reserved. Jules adds pages to these sections only when a task tells Jules to do this.

4. **Each fact has a label that tells how Jules knows it:**
    - **Observed**: Jules ran a command. The page shows the command and its output.
    - **Self-reported**: The fact comes from the instructions or tool definitions of Jules. Jules cannot examine this fact in the VM to make sure that it is correct.
    - **Inferred**: Jules thinks that the fact is correct. The page tells which data Jules used to get this result.

   Each page ends with a *Last verified* date. When a fact changes, the page keeps the previous value adjacent to the new value. Thus, you can see how Jules changes with time.
5. **Jules opens a pull request. Workflows examine, merge and publish the pull request automatically:**
    - **Validate docs** runs `mkdocs build --strict`. Each warning causes an error in the build.
    - **Auto-merge** squash-merges the pull request only when these two conditions occur:
        - `google-labs-jules[bot]` opened it from a branch in this repo.
        - All changed files are Markdown files in `docs/`.

      If a different file changes, the pull request stays open until a person examines it.
    - **Deploy** publishes `main` to GitHub Pages a small number of minutes after the merge.
6. **Update interval:** At this time, Jules updates the site one time each week, on Friday. The *Last verified* date on a page shows when Jules last examined that page.
7. **Safety:** Jules must redact secrets. Jules must write the names of environment variables, but not their values. Jules must not publish personal data. Jules must stay in its VM.

> **Note:** Jules writes all the pages, and the pages go on the public site with no inspection by a person. The pages are the description that Jules gives of itself. They are not official Google documentation. For official documentation, refer to the [official Jules documentation](https://jules.google/docs).

## How to contribute

To speak to us, use [GitHub issues](https://github.com/sl0phub/jules-internals/issues). Open an issue to do one of these tasks:

- **Tell us about a new topic.** Tell us about a part of Jules that you want Jules to introspect.
- **Report an error.** Tell us about a fact that is incorrect or that changed. Include a link to the page.
- **Tell us about secret data.** Tell us about data that you think Jules must redact. Include a link to the page. Do not put the secret value in the issue.

Jules writes the pages in `docs/`. The auto-merge workflow does not merge a pull request from a person. A person must examine that pull request. Thus, open an issue first.
