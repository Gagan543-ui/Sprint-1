# Standard Operating Procedure (SOP)
## Python Project Management Using Poetry
## SOP Overview Table

| Section No. | SOP Section Title | Description / Objective |
|------------|------------------|-------------------------|
| 1 | Purpose | Defines why this SOP exists and what problem it solves |
| 2 | Scope | Specifies where and when this SOP is applicable |
| 3 | Audience / Responsibility | Identifies roles and their responsibilities |
| 4 | Prerequisites | Lists required tools, access, and system requirements |
| 5 | Tool Overview – What is Poetry? | Explains Poetry and its importance |
| 6 | SOP – Creating a New Poetry Project | Step-by-step process to create a project |
| 7 | Project Structure Explanation | Explains folders and files created by Poetry |
| 8 | SOP – Virtual Environment Management | How Poetry manages virtual environments |
| 9 | SOP – Writing Application Code | Where and how to write Python code |
| 10 | SOP – Running the Application | Correct methods to run the application |
| 11 | Verification & Validation | How to confirm the setup is successful |
| 12 | Troubleshooting Guide | Common issues and their resolutions |
| 13 | Demo Commands | Commands used for demo and validation |
| 14 | SOP Completion Criteria | Conditions to mark the SOP as complete |


---

## 1. Purpose  
### Why this SOP exists

The purpose of this SOP is to define a standard and repeatable procedure for:

- Creating Python projects using Poetry
- Managing dependencies safely
- Managing virtual environments automatically
- Running Python applications in an isolated and consistent manner

This SOP helps prevent:

- Dependency conflicts
- Environment mismatch issues
- “Works on my machine” problems

---

## 2. Scope

This SOP applies to:

- All Python projects using Poetry
- Development, QA, UAT, and Production environments
- Local machines, build servers, and CI/CD pipelines

---

## 3. Audience / Responsibility

| Role | Responsibility |
|-----|----------------|
| L0 / L1 Engineer | Follow SOP to create & run projects |
| L2 Engineer | Troubleshoot Poetry issues |
| DevOps Engineer | Enforce SOP in CI/CD |
| Reviewer | Validate SOP compliance |

---

## 4. Prerequisites

Before starting, ensure:

- Python 3.8 or higher is installed
- Poetry is installed and accessible in PATH
- Basic Linux command knowledge
- Internet access (for dependency installation)

### Verification Commands
```bash
python3 --version
poetry --version

```
---
## Python Project Management Using Poetry
## 1. Purpose  
### Why this SOP exists

The purpose of this SOP is to define a standard and repeatable procedure for:

- Creating Python projects using Poetry
- Managing dependencies safely
- Managing virtual environments automatically
- Running Python applications in an isolated and consistent manner

This SOP helps prevent:

- Dependency conflicts
- Environment mismatch issues
- “Works on my machine” problems

---

## 2. Scope

This SOP applies to:

- All Python projects using Poetry
- Development, QA, UAT, and Production environments
- Local machines, build servers, and CI/CD pipelines

---

## 3. Audience / Responsibility

| Role | Responsibility |
|-----|----------------|
| L0 / L1 Engineer | Follow SOP to create & run projects |
| L2 Engineer | Troubleshoot Poetry issues |
| DevOps Engineer | Enforce SOP in CI/CD |
| Reviewer | Validate SOP compliance |

---

## 4. Prerequisites

Before starting, ensure:

- Python 3.8 or higher is installed
- Poetry is installed and accessible in PATH
- Basic Linux command knowledge
- Internet access (for dependency installation)

### Verification Commands

```bash
python3 --version

```

## 5. Tool Overview – What is Poetry?

- Poetry is a Python dependency and project management tool that:

- Creates isolated virtual environments automatically

- Manages dependencies via pyproject.toml

- Locks exact dependency versions using poetry.lock

- Ensures reproducible builds

### Why Poetry over pip & venv?

| pip + venv            | Poetry              |
|-----------------------|---------------------|
| Manual steps          | Automated           |
| Multiple config files | Single file         |
| No strict lock        | Locked dependencies |

## 6. SOP – Creating a New Poetry Project
Step 1: Create project
```bash
poetry new my-poetry-project
```

What this does:

- Creates project directory

- Generates pyproject.toml

- Sets up standard folder structure

- Uses src layout by default

## 7. Project Structure Explanation (Very Important)

```text
my-poetry-project/
├── pyproject.toml      # Project metadata & dependencies
├── poetry.lock         # Locked dependency versions
├── README.md
├── src/
│   └── my_poetry_project/
│       └── __init__.py
└── tests/

```

Explanation:

- src/ → All application code lives here

- pyproject.toml → Central configuration file

- poetry.lock → Ensures same dependencies everywhere

## 8. SOP – Virtual Environment Management
Step 1: Create virtual environment
```bash
poetry install
```
What happens internally:

- Poetry creates a dedicated virtual environment

- Installs dependencies

- Activates environment for project usage

## 9. SOP – Writing Application Code
Correct location for code:
```bash
src/my_poetry_project/
```
Example file creation:
```bash
nano src/my_poetry_project/main.py
```
#### Sample code:
import requests

def main():
    print("Poetry SOP demo running")
    print("Requests version:", requests.__version__)

if __name__ == "__main__":
    main()


## 10. SOP – Running the Application
```bash
poetry run python src/my_poetry_project/main.py
```

## 11. Verification & Validation

- After running the application, confirm:

- Application executes without errors

- Correct dependency versions are used

- Output matches expected behavior


## 12.Troubleshooting Guide

| Issue                       | Cause              | Resolution               |
|-----------------------------|--------------------|--------------------------|
| `poetry: command not found` | Poetry not in PATH | Reload shell / reinstall |
| Module not found            | Dependency missing | `poetry add <module>`    |
| Wrong folder                | Code outside src   | Move code to `src/`      |
| Env issues                  | Corrupt venv       | `poetry env remove`      |


## Demo Commands:
```bash
poetry new sop-demo
```
```bash
cd sop-demo
```
```bash
poetry run python src/sop_demo/main.py
```

## 13. SOP Completion Criteria

The SOP is considered complete when:

- Project runs successfully

- Dependencies are locked

- Environment is isolated

- Reviewer can reproduce steps

