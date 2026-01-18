# GNU Make – Standard Operating Procedure (SOP)

## 1. Purpose
The purpose of this document is to define a standardized and repeatable procedure for installing, verifying, and using **GNU Make** to automate build and compilation tasks across Linux-based systems.

---

## 2. Scope
This SOP applies to:
- Ubuntu / Debian-based Linux systems
- Development and CI/CD environments
- Build automation and compilation workflows

---

## 3. Audience / Responsibility

| Role | Responsibility |
|----|----|
| L0 / L1 Engineer | Install and verify GNU Make |
| L2 Engineer | Troubleshoot build and Makefile issues |
| DevOps Engineer | Integrate Make into CI/CD pipelines |

---

## 4. Prerequisites
- Linux system access
- sudo or root privileges
- Basic understanding of Linux commands
- Source code containing a `Makefile`

---

## 5. What is GNU Make
**GNU Make** is a build automation tool that executes tasks defined in a `Makefile`.

### Key Features
- Automates build processes
- Manages dependencies efficiently
- Prevents unnecessary recompilation
- Improves build performance

---

## 6. Installation Guide (Ubuntu)

### Step 1: Update the package index
```bash
sudo apt update
```
<img width="1448" height="936" alt="image" src="https://github.com/user-attachments/assets/cc375646-d685-4581-9b25-7ee7edb45c71" />

### Step 2: Install GNU Make
```bash
sudo apt install make -y
```
<img width="1056" height="184" alt="install_make" src="https://github.com/user-attachments/assets/ad557803-fe63-41ad-ae33-2b057c12885b" />

### Step 3: Verify installation
```bash
make --version
```
<img width="1432" height="220" alt="check_version" src="https://github.com/user-attachments/assets/d4b7bfd5-2e6f-4737-8bf8-b10a5f260b7f" />

## 7. Basic Usage

### Step 1: Navigate to the project directory
```bash
cd /path/to/project
```

### Step 2: Execute Make
```bash
make
```
This command reads instructions from the Makefile and executes the default target.
<img width="1374" height="364" alt="image" src="https://github.com/user-attachments/assets/e2d2adf2-b7d5-45dd-b4b7-4b45a55fe655" />


## Makefile Commands

The following table outlines the commonly used `make` commands and their purpose within this project:

| Command          | Description                                                   |
|------------------|---------------------------------------------------------------|
| `make`           | Builds the project using the default target                   |
| `make clean`     | Cleans up all generated build artifacts                        |
| `make install`   | Installs the compiled binaries to the system environment       |
| `make help`      | Lists all available Makefile targets with descriptions         |


## 9. Validation / Verification

Confirm build artifacts are generated

Check command exit status:
```bash
echo $?
```

## 10. Troubleshooting

The table below lists common issues encountered while using `make`, along with their possible causes and recommended resolutions:

| Issue                       | Possible Cause                  | Resolution                                  |
|-----------------------------|---------------------------------|---------------------------------------------|
| `make: command not found`   | GNU Make is not installed       | Install `make` using your system package manager |
| `No rule to make target`    | Missing or incorrectly named Makefile | Verify the Makefile name and target definition |
| Build failure               | Dependency or configuration issues | Review build logs and validate dependencies |

## 11. Best Practices

- Use tabs, not spaces, for command indentation

- Define .PHONY targets for non-file actions

- Keep Makefiles modular and readable

- Add comments to explain targets and variables

## 12. References

- GNU Make Official Documentation

- Linux Manual Page:
```bash
man make
```
