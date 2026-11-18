# Day 1 — Technical Study Notes

**Project:** Retail Data Engineering & Analytics Platform  
**Phase:** 1 — Development Foundations  
**Status:** Local environment, Git initialization, and first GitHub push verified by terminal outputs reported during the session. Dataset ingestion, PostgreSQL, ETL, and Azure deployment are not yet completed.

## 1. Learning objectives

- Distinguish the Python interpreter, pip, and a virtual environment.
- Create a Python 3.12 project environment on Windows.
- Understand Git repositories, branches, staging, commits, and remotes.
- Exclude local/generated files from version control using `.gitignore`.
- Publish an existing local repository to GitHub without creating conflicting initial commits.
- Explain the purpose of a professional data engineering repository structure.

## 2. Verified environment

| Component | Verified result |
|---|---|
| Operating system | Windows; PowerShell in VS Code |
| Python interpreter in virtual environment | Python 3.12.7 |
| pip in virtual environment | pip 24.2 |
| Additional installed Python | Python 3.15.2 (system launcher default) |
| Git | 2.45.2.windows.1 (reported earlier) |
| Project directory | `C:\Users\Prokshy\Documents\retail-data-engineering-platform` |
| Git branch | `main` |
| Initial commit | `aaf59eb` |
| Remote | `https://github.com/PolemoniProkshitha/retail-data-engineering-platform.git` |
| GitHub push | `main -> main`; upstream tracking `origin/main` established |

## 3. Concepts and explanations

### Python interpreter and pip

The interpreter runs Python code. `pip` installs Python packages. `python -m pip` invokes pip using the currently selected interpreter, reducing the risk of installing packages into a different Python installation.

### Virtual environment (`venv`)

A virtual environment isolates Python packages and interpreter references for a project. It makes dependency conflicts less likely, but it does not guarantee full reproducibility on its own. Dependency versions and external system requirements must also be documented.

### Git and GitHub

Git is a distributed version control system. GitHub is a remote hosting and collaboration platform for Git repositories. A commit saves a snapshot locally; pushing sends commits to the configured remote.

### Working directory, staging area, and repository

- **Working directory:** Files being edited.
- **Staging area (index):** Changes selected for the next commit.
- **Repository history:** Commits and related Git objects saved locally.

### `.gitignore`

Git uses `.gitignore` patterns to ignore matching *untracked* files. Common examples include `.venv/`, `__pycache__/`, `.env`, logs, and large generated data. `.gitignore` does not remove files already tracked or purge secrets from Git history. Never treat it as a complete secrets-management solution.

### Git branch and remote

`main` is the current local branch. `origin` is a conventional name for the remote repository. `origin/main` is a remote-tracking reference. `git push -u origin main` pushes the branch and establishes upstream tracking for convenient future push/pull operations.

## 4. Command reference

| Command | Purpose | Expected result / check |
|---|---|---|
| `py --list` | List installed Python versions | Shows Python 3.12 and 3.15 |
| `py -3.12 -m venv .venv` | Create isolated Python 3.12 environment | `.venv` directory appears |
| `.\.venv\Scripts\Activate.ps1` | Activate environment in PowerShell | Prompt begins with `(.venv)` |
| `python --version` | Check active interpreter | `Python 3.12.7` |
| `python -m pip --version` | Check pip tied to active Python | `pip 24.2` under `.venv\Lib\site-packages` |
| `pwd` | Show current PowerShell directory | Project root path |
| `git init` | Initialize local Git repository | `.git` directory created |
| `git branch -M main` | Name current branch `main` | `git branch --show-current` prints `main` |
| `git status` | Inspect tracked/untracked/staged changes | Clean after commit |
| `git add .gitignore README.md requirements.txt .env.example` | Stage selected setup files | Four staged files in status |
| `git commit -m "chore: initialize retail data engineering project"` | Save first snapshot | Commit `aaf59eb` |
| `git log --oneline -1` | Show latest commit | `aaf59eb ...` |
| `git remote add origin https://github.com/PolemoniProkshitha/retail-data-engineering-platform.git` | Register GitHub remote | Usually no output |
| `git remote -v` | Check remote fetch/push URLs | Both point to the same GitHub repository |
| `git show --pretty="" --name-only HEAD` | Inspect files in latest commit | Only intended setup files |
| `git push -u origin main` | Push and set upstream | `main -> main`, tracking `origin/main` |

## 5. Project organization and engineering rationale

| Directory | Planned purpose |
|---|---|
| `src/ingestion/` | Extract data from sources |
| `src/transformation/` | Clean and transform records |
| `src/validation/` | Validate schema and data quality |
| `src/pipelines/` | Orchestrate pipeline steps |
| `sql/staging/`, `sql/analytics/` | Database and analytics SQL |
| `spark/bronze/`, `spark/silver/`, `spark/gold/` | Future lakehouse layers |
| `tests/` | Automated testing |
| `azure/` | Future Azure configuration |
| `docs/` | Architecture, learning, interviews, troubleshooting |
| `.github/workflows/` | Future GitHub Actions automation |

Empty folders are not tracked by Git until they contain tracked files. The folder structure expresses a plan, not implemented functionality.

## 6. Troubleshooting guide

| Symptom | Likely cause | Safe response |
|---|---|---|
| `python --version` shows 3.15 | Wrong interpreter active | Activate `.venv`; check again |
| PowerShell blocks `Activate.ps1` | Execution policy restrictions | Use `.\.venv\Scripts\python.exe` directly; review policy before changing it |
| `git status` shows `.venv/` | Missing/incorrect `.gitignore` | Confirm `.gitignore` at repo root includes `.venv/`; if tracked, ignoring alone is insufficient |
| `remote origin already exists` | Remote previously configured | Run `git remote -v` before modifying |
| `Author identity unknown` | Git user name/email missing | Configure local `git config --local user.name` and `user.email` |
| Push requests sign-in | GitHub authentication needed | Use supported browser/Git Credential Manager sign-in; never paste tokens into chat |
| Push rejected | Remote history or permissions issue | Inspect exact error; do not force-push blindly |
| Secret accidentally committed | Sensitive value in history | Rotate/revoke secret immediately; use an appropriate history-removal procedure |

**Observed errors during Day 1:** None reported. Troubleshooting entries above are preventative examples, not incidents that occurred.

## 7. Interview preparation — questions and model answers

**Q1. What is a Python virtual environment?**  
An isolated project-specific Python environment used to manage dependencies independently from other projects.

**Q2. Why use `python -m pip`?**  
It runs pip using the currently selected Python interpreter, avoiding ambiguity when multiple Python versions are installed.

**Q3. Why shouldn't `.venv` be committed?**  
It contains installed packages and machine-specific files, increases repository size, and can cause portability problems. Instead, document dependencies and recreate the environment.

**Q4. What is the difference between Git and GitHub?**  
Git manages version history; GitHub hosts Git repositories and enables collaboration.

**Q5. What does `.gitignore` do, and what is its limitation?**  
It excludes matching untracked files from ordinary Git tracking. It does not remove tracked files or secrets already committed.

**Q6. What is the difference between `git add` and `git commit`?**  
`git add` stages changes; `git commit` records staged changes as a local snapshot.

**Q7. What is a local versus remote repository?**  
A local repository exists on your machine. A remote repository is hosted elsewhere, such as GitHub; push/pull synchronize changes.

**Q8. What does `git push -u origin main` do?**  
Pushes local `main` to the remote named `origin` and sets the upstream tracking branch.

**Q9. Why use meaningful commit messages?**  
They explain the intent of changes and improve review, troubleshooting, and project history.

**Q10. Why separate ingestion, transformation, validation, and tests?**  
Separation of concerns makes a pipeline easier to understand, test, maintain, and extend.

### Practice exercise

Without looking at the answers, explain in 60 seconds how code travels from an edited file in VS Code to GitHub. Include `git add`, `git commit`, and `git push`. Then explain what happens if a secret is accidentally committed.

## 8. End-of-day review

**Completed:** Python 3.12 environment, Git initialization, repository structure, `.gitignore`, first commit, GitHub remote configuration, successful push.  
**Not yet completed:** Dataset download, PostgreSQL installation, SQL practice, ingestion, ETL, tests, cloud deployment.  
**Next learning activity:** Verify and publish Day 1 notes, then begin dataset acquisition and exploration.

## 9. Personal reflection prompts

1. What is the difference between installing a Python package globally and inside `.venv`?
2. Why do we stage files before committing?
3. How would you check whether a remote is configured correctly?
4. What could go wrong if a real database password appears in Git history?
5. Which Day 1 command could you explain confidently without looking it up?
