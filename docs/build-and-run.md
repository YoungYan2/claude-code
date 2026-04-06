# Build and Run Guide

This guide helps new contributors understand what is needed to compile and run this project.

## Important Context

This repository is a source snapshot for research. In its current form, it does **not** include standard build manifests such as `package.json` or `tsconfig.json`.

That means:

- You can browse and study the source code immediately.
- You cannot do a normal dependency install or full compile from this snapshot alone.

## Prerequisites

Install these tools first:

- Git (for cloning and branch workflows)
- Bun (runtime/package manager used by this codebase)
- Node.js (some tooling in related ecosystems may still expect it)
- A terminal and editor (for example: macOS Terminal + VS Code)

Optional but useful:

- ripgrep (`rg`) for fast code search

## Quick Start (Current Snapshot)

From the repository root:

```bash
# show top-level files
ls -la

# inspect source layout
find src -maxdepth 2 -type d | sort
```

This is the safe and expected workflow for this snapshot: read and analyze source.

## Build and Run (Full Source Checkout)

If you have a complete source checkout that includes build manifests, use this baseline flow:

```bash
# 1) install dependencies
bun install

# 2) compile/type-check (command name may vary by repo scripts)
bun run build

# 3) run CLI help or app entrypoint
bun run src/main.tsx --help
```

If your checkout defines different script names, run:

```bash
bun run
```

Then pick the available script targets (for example `dev`, `build`, or `start`).

## Troubleshooting

- `bun: command not found`
  - Install Bun and restart your terminal session.
- `No package.json` or `Script not found`
  - You are likely in the research snapshot, not a full buildable checkout.
- Missing modules during execution
  - Dependencies were not installed, or the checkout is incomplete.

## Recommended Next Step

If your goal is to run the CLI end-to-end, obtain a complete checkout that includes package manifests and lockfiles, then follow the full-source steps above.
