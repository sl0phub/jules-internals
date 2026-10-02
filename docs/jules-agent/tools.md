# Tools

This page documents the tools Jules can call to explore, modify, and manage tasks.

## Tool Verification

| Tool | Self-reported (definition) | Observed (call made and result) | Status |
|---|---|---|---|
| `list_files` | Lists all files and directories under the given directory. | Called on `/tmp` and returned listing (`tool_test.txt`, etc). | works |
| `read_file` | Reads the content of a specified file. | Called on `docs/jules-agent/tools.md` and returned contents successfully. | works |
| `write_file` | Creates a new file or overwrites an existing file. | Called to create `docs/jules-vm/environment.md` update. | works |
| `replace_with_git_merge_diff` | Performs a targeted search-and-replace using Git merge diff format. | Called to update `docs/index.md` links. | works |
| `delete_file` | Deletes a specified file. | - | not tested (changes state) |
| `rename_file` | Renames or moves files and directories. | - | not tested (changes state) |
| `reset_all` | Resets the entire codebase to its original state. | - | not tested (changes state) |
| `restore_file` | Restores a given file to its original state. | - | not tested (changes state) |
| `run_in_bash_session` | Runs a bash command in the sandbox. | Called `ls` and `echo` successfully, also complex commands. | works |
| `start_live_preview_instructions` | Returns instructions on how to start a live preview server. | - | not tested (reads help string) |
| `google_search` | Online search to retrieve information. | - | not tested (external web action) |
| `view_text_website` | Fetches the content of a website as plain text. | Called on `https://jules.google/docs/environment/` and returned HTML text. | works |
| `view_image` | Loads an image from a URL to view its contents. | - | not tested (no image handy) |
| `read_image_file` | Reads an image file at the filepath into context. | - | not tested (no image handy) |
| `read_media_file` | Reads a media file from the machine into context. | - | not tested (no media handy) |
| `set_plan` | Sets or updates the execution plan in Markdown format. | Called to set the plan for this task. | works |
| `plan_step_complete` | Marks a plan step as complete with an explanation message. | Called to finish steps for this task. | works |
| `request_plan_review` | Requests a review for the proposed plan. | Called multiple times to get the plan approved. | works |
| `pre_commit_instructions` | Get instructions on pre-commit steps required before submission. | - | not tested (will run at end of task) |
| `submit` | Commits the code with title/description and requests user approval to push. | - | not tested (ends the task) |
| `message_user` | Sends a message to the user. | - | not tested (messages user) |
| `request_user_input` | Asks the user a question and waits for a response. | - | not tested (blocks task) |
| `request_code_review` | Requests code review for the current change. | - | not tested (messages user) |
| `read_pr_comments` | Reads pending pull request comments. | - | not tested (requires PR context) |
| `reply_to_pr_comments` | Replies to pull request comments. | - | not tested (requires PR context) |
| `initiate_memory_recording` | Starts recording information useful for future tasks. | - | not tested (state mutation) |
| `record_user_approval_for_plan` | Records user's approval for the plan. | - | not tested (mutates memory) |

## Tool Definitions

### Code and File Management

!!! info "Self-reported"
    - **`list_files`**: Lists all files and directories under the given directory (defaults to repo root).
    - **`read_file`**: Reads the content of a specified file.
    - **`write_file`**: Creates a new file or overwrites an existing file.
    - **`replace_with_git_merge_diff`**: Performs a targeted search-and-replace to modify an existing file using Git merge diff format.
    - **`delete_file`**: Deletes a specified file.
    - **`rename_file`**: Renames or moves files and directories.
    - **`reset_all`**: Resets the entire codebase to its original state.
    - **`restore_file`**: Restores a given file to its original state.

### Execution and Environment

!!! info "Self-reported"
    - **`run_in_bash_session`**: Runs a bash command in the sandbox. Used for installing dependencies, compiling code, running tests, etc.
    - **`start_live_preview_instructions`**: Returns instructions on how to start a live preview server.

### Web and Media

!!! info "Self-reported"
    - **`google_search`**: Online search to retrieve information.
    - **`view_text_website`**: Fetches the content of a website as plain text.
    - **`view_image`**: Loads an image from a URL to view its contents.
    - **`read_image_file`**: Reads an image file at the filepath into context.
    - **`read_media_file`**: Reads a media file (image or video) from the machine into context.

### Workflow and Planning

!!! info "Self-reported"
    - **`set_plan`**: Sets or updates the execution plan in Markdown format.
    - **`plan_step_complete`**: Marks a plan step as complete with an explanation message.
    - **`request_plan_review`**: Requests a review for the proposed plan before using `set_plan`.
    - **`pre_commit_instructions`**: Get instructions on pre-commit steps required before submission.
    - **`submit`**: Commits the code with title/description and requests user approval to push.

### User Interaction and Review

!!! info "Self-reported"
    - **`message_user`**: Sends a message to the user.
    - **`request_user_input`**: Asks the user a question and waits for a response.
    - **`request_code_review`**: Requests code review for the current change.
    - **`read_pr_comments`**: Reads pending pull request comments.
    - **`reply_to_pr_comments`**: Replies to pull request comments.

### Memory and State

!!! info "Self-reported"
    - **`initiate_memory_recording`**: Starts recording information useful for future tasks.
    - **`record_user_approval_for_plan`**: Records user's approval for the plan.

_Last verified: 2026-10-02 (Jules session)_
