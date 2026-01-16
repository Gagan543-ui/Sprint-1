# Maven Documentation

## Author & Version Information

| Author | Created on | Version | Last updated by | Last edited on |
|--------|------------|---------|-----------------|----------------|
| Shreyas Awasthi  | 16-01-2026 | Version 1 | Shreyas Awasthi | 17-01-2026 |

---

## Introduction

Apache Maven is a **build automation and project management tool** primarily used for Java-based applications.  
It simplifies the build process by providing a standard project structure, dependency management, and lifecycle management using a declarative configuration file called `pom.xml`.

Maven ensures consistency, repeatability, and ease of maintenance across development and deployment environments.

---

## Purpose

Maven is used to:

- Standardize project structure
- Manage dependencies efficiently
- Automate build, test, and packaging
- Handle project versioning and releases
- Integrate with CI/CD pipelines

---

## Key Features

- **Convention over Configuration**
- **Centralized Dependency Management**
- **Build Lifecycle Management**
- **Plugin-based Architecture**
- **Support for Multi-module Projects**
- **Integration with CI/CD tools**

---

## Getting Started

### Pre-requisites

| Requirement | Description |
|------------|-------------|
| Java | JDK 8 or higher |
| Maven | Apache Maven 3.x |
| OS | Linux / Windows / macOS |

---

## Software Overview

| Software | Version |
|--------|---------|
| Apache Maven | 3.9.x |
| Java JDK | 8+ |

---

## System Requirements

| Requirement | Minimum Recommendation |
|------------|------------------------|
| Processor | Dual-Core |
| RAM | 4 GB or higher |
| Disk Space | 2 GB or higher |
| OS | Linux / Windows / macOS |

---

## Important Ports

| Port | Description |
|------|------------|
| 443 | Secure communication with remote Maven repositories |
| 80 | HTTP-based repository access |

---

## Dependencies

### Build-time Dependencies
Defined in the `pom.xml` file and required during the build process.

### Run-time Dependencies
Required during application execution.

### Other Dependencies
- Maven plugins
- Reporting tools
- Testing frameworks (JUnit, TestNG)

---

## Local Repository

The local repository is a directory on the developer’s machine where Maven stores downloaded dependencies.

**Default Location:**
```bash
~/.m2/repository

```
## Benefits:

- Prevents repeated downloads of dependencies by caching artifacts locally  
- Enhances overall build speed and efficiency  
- Supports offline builds once dependencies are cached  
- Minimizes reliance on external networks and remote repositories  

## Remote Repository

Remote repositories are centralized storage locations used to host and manage project artifacts and third-party dependencies.

Commonly Used Repositories:

- Maven Central – Public default repository

- Nexus Repository Manager – Internal enterprise repository



### Enterprise Benefits:

- Controlled and approved dependency usage

- Improved security and compliance

- Faster builds via caching and mirroring

## Installation & Setup
  #### Step-by-step Installation

Download Apache Maven from the official Apache website

Extract the downloaded archive

Configure the environment variable:

    export MAVEN_HOME=/opt/maven

Add Maven to the system PATH:

    export PATH=$MAVEN_HOME/bin:$PATH
Verify the installation:

       mvn -version

## Configuration

  Project Configuration

- Main configuration file: pom.xml

- Must be committed to version control

- Should follow company-approved dependency versions

### User-level Configuration

- Location: ~/.m2/settings.xml

Used for:

   - Repository credentials

-    Proxy configuration

-    Mirror and profile settings

## Maintenance

- Upgrade Maven versions as per approved release cycles

- Remove unused or deprecated dependencies

- Validate plugin compatibility after upgrades

- Ensure consistency across environments

## Monitoring & Compliance

- Monitor CI/CD pipeline build status

- Track dependency vulnerabilities using approved tools

- Review and analyze build logs for failures

- Enforce usage of internal repositories only

##  Troubleshooting

| Issue                | Resolution                                              |
|----------------------|----------------------------------------------------------|
| Dependency not found | Verify repository configuration and access               |
| Build failure        | Run Maven with debug logging: `mvn -X`                   |
| Slow builds          | Validate local repository cache and configured mirrors   |

## FAQs

#### Q: What is pom.xml?

A: Project Object Model file that defines project dependencies, plugins, build lifecycle, and configurations.

#### Q: What is Maven Central?
A: The default public repository hosting thousands of open-source Java dependencies.
