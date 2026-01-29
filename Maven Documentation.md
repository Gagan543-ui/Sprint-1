
# Maven Documentation
## Author & Version Information

###  Document Details

| Author           | Created    | Version | Last updated by  | Last Edited On | L0 Reviewer | L1 Reviewer | L2 Reviewer |
| ---------------- | ---------- | ------- | ---------------- | -------------- |----------- | ----------- | ----------- |
| Shreyas Awasthi | 2026-01-20 | 1.0     | Shreyas Awasthi| 2026-01-23     | Divya Mishra         |   |       |
| Shreyas Awasthi | 2026-01-20 | 1.1     | Shreyas Awasthi | 2026-01-24    | Divya Mishra         |  Pritam |        |
## Table of Contents

- [1. Introduction](#1-introduction)
- [2. What is Maven](#2-what-is-maven)
- [3. Why Maven is Required](#3-why-maven-is-required)
- [4. Key Features of Maven](#4-key-features-of-maven)
  - [Dependency Management](#1-dependency-management)
  - [Standard Project Structure](#2-standard-project-structure)
  - [Build Automation](#3-build-automation)
  - [Version and Release Management](#4-version-and-release-management)

- [5. What is pom.xml](#5-what-is-pomxml)
- [6. Maven Repositories](#6-maven-repositories)
- [7. Dependency Resolution Flow](#7-dependency-resolution-flow)
- [8. Common Maven Commands](#8-common-maven-commands)
- [9. Conclusion](#9-conclusion)
- [10. Contact Information](#10-contact-information)
- [11. References](#11-references)


## 1. Introduction

This document provides a clear and structured overview of **Apache Maven**, a widely adopted build and dependency management tool for Java-based projects.  
It is intended to support onboarding, project understanding, and standardized development practices.

---
## 2. What is Maven

Apache Maven is a **build automation and project management tool** primarily used for Java applications.  
It manages project builds, dependencies, plugins, and versions using a centralized configuration file.
 
> Maven defines *how a project is built and what it depends on*.

---
## 3. Why Maven is Required

Before Maven:

- **Developers manually managed `.jar` files**  
  This increased manual effort and introduced inconsistencies across environments.
- **Dependency version conflicts were common**  
  Multiple versions of the same library caused runtime and compatibility issues.
- **Build process varied across environments**  
  Builds behaved differently on developer machines, QA, and production servers.

With Maven:

- **Dependencies are downloaded automatically**  
  Maven fetches required libraries from repositories based on configuration.
- **Builds are consistent on all systems**  
  The same lifecycle executes uniformly across environments.
- **Project structure follows a standard format**  
  This improves maintainability and team collaboration.

---
## 4. Key Features of Maven

### 1. Dependency Management

- **Automatically downloads required libraries**  
  Maven resolves dependencies declared in `pom.xml`.
- **Manages transitive dependencies**  
  Required sub-dependencies are handled automatically.
- **Removes the need for manual `.jar` handling**  
  Projects remain clean and lightweight.
### 2. Standard Project Structure

Maven enforces a predefined directory structure that is common across Java projects.

- **Improves readability**  
  Developers can easily navigate the project.
- **Reduces onboarding time**  
  New team members understand the layout quickly.
### 3. Build Automation

Maven automates the complete build lifecycle.

- **Compile source code**  
  Converts Java source files into bytecode.
- **Package applications (JAR/WAR)**  
  Produces deployable artifacts.
### 4. Version and Release Management

- **Manages project and dependency versions**  
  Ensures controlled and predictable releases.
- **Helps avoid version conflicts**  
  Explicit version definitions prevent failures.
---

## 5. What is `pom.xml`

The `pom.xml` (Project Object Model) file is the **core configuration file** of a Maven project.  
It defines project metadata, dependencies, plugins, and build behavior.

It contains:

- **Project information**  
  Identifies the project using `groupId`, `artifactId`, and `version`.
- **Dependency definitions**  
  Lists all external libraries required.
- **Build and plugin configurations**  
  Controls compilation, testing, and packaging.

### Example

```xml
<project>
  <groupId>com.example</groupId>
  <artifactId>demo-app</artifactId>
  <version>1.0.0</version>
</project>
```
## 6. Maven Repositories

A Maven repository is a storage location for dependencies and build artifacts.

### Local Repository

- **Stored on the developer’s machine**  
  It resides locally and is specific to each user environment.
- **Acts as a local cache for dependencies**  
  Downloaded libraries are reused to improve build performance.
  
- **Default location**
 
      ~/.m2/repository

- **Reused across multiple projects**  
  Multiple Maven projects can use the same cached dependencies.
- **Avoids repeated downloads**  
  Reduces network usage and speeds up builds.
---
### Remote Repository

- **Hosted on centralized servers**  
  Dependencies are maintained in shared, remote locations.
- **Provides shared access to dependencies**  
  Teams use a common source of approved libraries.
- **Used when dependencies are not found locally**  
  Maven automatically contacts remote repositories.
- **Maven downloads them automatically**  
  No manual intervention is required during builds.

**Common examples:**

- **Maven Central** – Default public repository  
- **Artifactory** – Advanced artifact management tool  
---

## 7. Dependency Resolution Flow

1. **Maven command is executed**  
   This triggers the build or dependency resolution process.
2. **Maven checks the local repository**  
   It searches for required dependencies in the local cache.
3. **If dependency is missing**  
   Maven downloads it from a remote repository.
4. **Dependency is stored locally**  
   This improves performance for future builds.
---
## 8. Common Maven Commands

The following Maven commands are commonly used during local development and CI/CD pipelines.  
Each command corresponds to a specific Maven lifecycle phase and produces predictable outputs.

| Command | Purpose | What It Does | Key File Paths |
|-------|---------|--------------|----------------|
| `mvn clean` | Clean build environment | Removes previously generated build files to ensure a fresh build | Deletes: `target/` |
| `mvn compile` | Compile source code | Compiles Java source files into bytecode | Input: `src/main/java/`<br>Output: `target/classes/` |
| `mvn test` | Execute tests | Runs unit tests to validate application behavior | Tests: `src/test/java/`<br>Reports: `target/surefire-reports/` |
| `mvn package` | Create build artifact | Packages compiled code into a deployable format | Artifact: `target/*.jar` or `target/*.war` |
| `mvn install` | Install artifact locally | Installs the packaged artifact into the local Maven repository | Local repo: `~/.m2/repository/` |

---

### Notes
- All Maven commands are executed from the project root where `pom.xml` is located.
- The `target/` directory is generated automatically.
- These commands are widely used in automated CI pipelines for consistent builds.

### Example

```bash
mvn clean install

```
---
## 9. Conclusion

Apache Maven provides a standardized, automated, and reliable approach to Java project builds.  
By managing dependencies, versions, and builds centrally, it ensures consistency, reduces errors, and supports scalable enterprise development.

---
## 10. Contact Information

| Name             | Team                 | Contact Type | Details                                                             |
| ---------------- | -------------------- |------------ | ------------------------------------------------------------------- |
| Shreyas Awasthi | Saarthi              |Email        | [shreyas.awasthi.snaatak@mygurukulam.CO](mailto:shreyas.awasthi.snaatak@mygurukulam.CO) |


---
## 11. References

| Descriptions | Links |
|-------------|-------|
| Apache Maven – Introduction | [What is Maven](https://maven.apache.org/what-is-maven.html) |
| Maven POM Reference (`pom.xml`) | [POM Reference](https://maven.apache.org/pom.html) |
| Maven Build Lifecycle | [Build Lifecycle Guide](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html) |

---
