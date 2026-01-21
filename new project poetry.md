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
<img width="1346" height="202" alt="image" src="https://github.com/user-attachments/assets/30be9047-fb3a-4b49-a71d-c81c9fd250a3" />

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
<img width="1146" height="78" alt="image" src="https://github.com/user-attachments/assets/ab9d5e13-c332-45ad-9028-c19de09c86a6" />

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
<img width="1330" height="80" alt="image" src="https://github.com/user-attachments/assets/082a3e80-a704-4664-a66a-a374eae705a9" />

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
<img width="1186" height="444" alt="image" src="https://github.com/user-attachments/assets/c2818161-f45e-413f-821a-5518cc898635" />

Explanation:

- src/ → All application code lives here

- pyproject.toml → Central configuration file

- poetry.lock → Ensures same dependencies everywhere

## 8. SOP – Virtual Environment Management
Step 1: Create virtual environment
```bash
poetry install
```
<img width="1962" height="284" alt="image" src="https://github.com/user-attachments/assets/69538808-6994-4c73-a719-8dc5328c3f94" />

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
<img width="1290" height="44" alt="image" src="https://github.com/user-attachments/assets/34145ea6-cbdf-4002-9a5b-9eae7523011a" />

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
<img width="1788" height="136" alt="image" src="https://github.com/user-attachments/assets/5a32e78e-932a-46ba-b430-4c141fe9a440" />

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

 ## 14. References

| Ref No. | Reference Title                          | Description / Usage                                                    | Link                                                                                         |
| ------: | ---------------------------------------- | ---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
|       1 | Poetry – Official Documentation          | Primary reference for Poetry concepts, commands, and project structure | [https://python-poetry.org/docs/](https://python-poetry.org/docs/)                           |
|       2 | Poetry – Installation Guide              | Official steps to install Poetry on different operating systems        | [https://python-poetry.org/docs/#installation](https://python-poetry.org/docs/#installation) |
|       3 | Python Packaging User Guide              | Best practices for Python dependency and packaging standards           | [https://packaging.python.org/en/latest/](https://packaging.python.org/en/latest/)           |
|       4 | PEP 518 – pyproject.toml Specification   | Defines the build-system requirements using `pyproject.toml`           | [https://peps.python.org/pep-0518/](https://peps.python.org/pep-0518/)                       |

