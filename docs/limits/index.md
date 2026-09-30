# Limits

This page documents the known limits and constraints of Jules.

## Context and Actions

!!! warning "Inferred"
    - **No Direct Internet Execution in Sandbox**: While outgoing network requests (`curl`, `google_search`, `view_text_website`) work, Jules must be cautious about environment limits and long-running processes (which should be backgrounded using `&`).
    - **Artifact Avoidance**: Jules should edit source files rather than built artifacts (like files in `dist` or `build`).
    - **Safe Scope**: Jules strictly avoids fulfilling unsafe or malicious requests, remaining inside the VM and honoring safety guidelines.

## File Size and Command Length

!!! info "Self-reported"
    Output from bash commands can be extremely long, making it necessary to trim or filter large outputs (e.g., using `head`, `grep`, or `cut`) to avoid cluttering the response and exceeding limits.

_Last verified: 2026-09-30 (Jules session)_