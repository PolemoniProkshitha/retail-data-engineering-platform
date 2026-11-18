# Phase 1 — Day 1: Development Environment and Version Control

## Objective

Establish a local Python development environment and publish the initial repository for the **Retail Data Engineering & Analytics Platform**.

## Completed work

- Selected Python 3.12 for project compatibility and created an isolated `.venv` environment.
- Verified Python 3.12.7 and pip 24.2 inside the environment.
- Initialized a Git repository and standardized the primary branch as `main`.
- Created a modular directory structure for future ingestion, transformation, validation, SQL, Spark, Azure, testing, and documentation components.
- Configured `.gitignore` to exclude local environments, caches, secrets files, logs, and generated datasets.
- Added initial `README.md`, `requirements.txt`, and `.env.example` files.
- Created initial commit `aaf59eb` (`chore: initialize retail data engineering project`).
- Connected the local repository to GitHub and successfully pushed `main`, establishing upstream tracking with `origin/main`.

## Repository

[retail-data-engineering-platform](https://github.com/PolemoniProkshitha/retail-data-engineering-platform)

## Tools

| Tool | Verified version / configuration |
|---|---|
| Python | 3.12.7 in `.venv` |
| pip | 24.2 in `.venv` |
| Git | 2.45.2.windows.1 |
| Editor | VS Code on Windows |
| Primary branch | `main` |

## Engineering decisions

**Isolated dependencies.** Use a project-specific Python environment rather than relying on the system default interpreter.

**Selective version control.** Exclude local environments, generated artifacts, and secrets from normal tracking. `.gitignore` is not a substitute for credential management.

**Modular structure.** Organize code by responsibility to support incremental implementation, testing, and future cloud integration.

**Traceable history.** Use descriptive commit messages and a remote GitHub repository to support future collaboration and CI/CD.

## Verification evidence

The following results were reported and checked during setup:

```text
Python 3.12.7
pip 24.2 ...\.venv\Lib\site-packages\pip (python 3.12)

origin  https://github.com/PolemoniProkshitha/retail-data-engineering-platform.git (fetch)
origin  https://github.com/PolemoniProkshitha/retail-data-engineering-platform.git (push)

main
aaf59eb (HEAD -> main) chore: initialize retail data engineering project

* [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

The user also confirmed that the expected files are visible on GitHub.

## Current scope and next steps

This milestone covers **development setup and repository publication only**. Data ingestion, database loading, transformations, automated testing, analytics, and Azure deployment are planned but have **not yet been implemented**.

Next: acquire and inspect the Store Sales dataset, define a first ingestion workflow, and introduce foundational SQL/PostgreSQL exercises.

## Reproduce the local Python setup

From the repository root on Windows PowerShell:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python --version
python -m pip --version
```

The initial `requirements.txt` is intentionally empty until project dependencies are selected and tested.
