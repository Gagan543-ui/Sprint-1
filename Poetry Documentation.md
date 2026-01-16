# Poetry Documentation

## Author Information

| Author | Created on | Version | Last Updated |
|------|-----------|---------|--------------|
| Shreyas Awasthi | 10-08-2023 | v1.0 | 16/01/2026 |

---

## Introduction

Poetry is a modern dependency management and packaging tool for Python projects.  
It provides a single, standardized way to manage dependencies, virtual environments, and project metadata using one configuration file. Poetry streamlines the Python development lifecycle by replacing multiple traditional tools with one integrated solution.

---

## Purpose

Poetry is used to:
- Manage Python dependencies in a reliable and reproducible manner
- Automatically create and manage virtual environments
- Simplify Python packaging and distribution
- Maintain consistency across development, testing, and production environments

---

## Key Features

- Centralized configuration using `pyproject.toml`
- Automatic virtual environment creation
- Deterministic dependency resolution with `poetry.lock`
- Separation of production and development dependencies
- Built-in support for packaging and publishing
- Cleaner and more maintainable workflow than traditional tools

---

## Getting Started

### Pre-requisites

| License Type | Description | Commercial Use | Open Source |
|-------------|------------|---------------|------------|
| MIT License | Free and open-source | Yes | Yes |

---

## Software Overview

| Software | Version |
|--------|---------|
| Poetry | Latest Stable |

---

## System Requirements

| Requirement | Minimum Recommendation |
|------------|-----------------------|
| Processor | Dual-Core |
| RAM | 4 GB or higher |
| Disk Space | 10 GB or higher |
| OS | Linux / macOS / Windows |
| Python | 3.8 or above |

---

## Important Ports

Poetry does not require any network ports.

---

## Dependencies

### Run-time Dependency

| Dependency | Version | Description |
|-----------|--------|-------------|
| Python | 3.8+ | Required to run Poetry |

### Other Dependencies

| Dependency | Version | Description |
|-----------|--------|-------------|
| curl | Latest | Used for installation |

---

## Why Poetry?

Traditional Python workflows require multiple tools such as `pip`, `virtualenv`, and `setup.py`.  
Poetry consolidates these tools into a single solution, improving reliability, reducing configuration errors, and ensuring reproducible builds.

---

## What Poetry Does

- Manages and locks dependencies
- Creates isolated virtual environments automatically
- Handles project metadata
- Builds and publishes Python packages
- Simplifies dependency upgrades and conflict resolution

---

## Comparison

### Poetry vs pip

| Feature | pip | Poetry |
|------|-----|--------|
| Dependency Resolution | Basic | Advanced |
| Lock File | Optional | Mandatory |
| Conflict Handling | Manual | Automatic |
| Project Metadata | Separate | Unified |

---

### Poetry vs venv

| Feature | venv | Poetry |
|------|------|--------|
| Virtual Environment | Manual | Automatic |
| Dependency Management | Not Included | Built-in |
| Central Config | No | Yes (`pyproject.toml`) |

---

## Installation

### Linux / macOS

```bash
curl -sSL https://install.python-poetry.org | python3 -

```
Verify installation:

```bash
poetry --version

```

## Poetry Configuration

The project uses **Poetry** for dependency and environment management.  
All configuration is defined in the `pyproject.toml` file.

### What `pyproject.toml` Defines
- Project metadata
- Python version compatibility
- Application dependencies
- Development and testing dependencies

By centralizing all configuration in a single file, Poetry helps ensure consistency, simplifies dependency management, and reduces operational risk.

## Maintenance

### Update Poetry
Keep Poetry up to date using:
```bash
poetry self update

```

### Monitoring

``` 
poetry check

```
## Disaster Recovery

Backup the following files:

pyproject.toml

poetry.lock

Restore dependencies using:

```
poetry install

```

## References

| Links | Descriptions |
|------|--------------|
| https://python-poetry.org | Official Poetry website for documentation, installation guides, and best practices |
| https://github.com/python-poetry/poetry | Official GitHub repository for source code, issues, and community contributions |
