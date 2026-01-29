
# Ansible Playbook

## Author & Version Information

### Document Details

---

| Author          | Created    | Version | Last updated by | Last Edited On | L0 Reviewer  | L1 Reviewer | L2 Reviewer |
| --------------- | ---------- | ------- | --------------- | -------------- | ------------ | ----------- | ----------- |
| Shreyas Awasthi | 2026-01-20 | 1.0     | Shreyas Awasthi | 2026-01-23     | Divya Mishra |             |             |
| Shreyas Awasthi | 2026-01-20 | 1.1     | Shreyas Awasthi | 2026-01-28     | Mohit Kumar | Pritam            |             |

---

## Table of Contents

- [1. Introduction](#1-introduction)
- [2. Scope](#2-scope)
- [3. What is an Ansible Playbook](#3-what-is-an-ansible-playbook)
- [4. Why Ansible Playbooks are Used](#4-why-ansible-playbooks-are-used)
- [5. Key Features of Ansible Playbooks](#5-key-features-of-ansible-playbooks)
- [6. Workflow of Anisble Playbook](#6-workflow-of-anisble-playbook)
- [7. Required Inputs](#7-required-inputs)
- [8. Execution Steps](#8-execution-steps)
- [9. Validation Checks](#9-validation-checks)
- [10. Conclusion](#10-conclusion)
- [11. Contact Information](#11-contact-information)
- [12. References](#12-references)

---

## 1. Introduction

This document defines of using Ansible playbooks to perform automated configuration and deployment tasks in a controlled and repeatable manner. The objective is to ensure consistency, reliability, and compliance across environments.

---
## 2. Scope

This SOP applies to:

- **All Ansible playbooks used for automation**  
  Ensures every automation follows a standardized and approved operational approach.
- **Development, QA, and Production environments**  
  Maintains uniform behavior and reduces environment-specific discrepancies.
- **Manual and CI/CD-driven playbook executions**  
  Covers both ad-hoc operations and automated pipeline executions.

---
## 3. What is an Ansible Playbook

An Ansible playbook is a YAML-based automation file that defines target hosts, tasks, variables, and execution logic to ensure structured, flexible, and reliable automation 

---
## 4. Why Ansible Playbooks are Used

Ansible playbooks are used to:

- **Automate repetitive operational tasks**  
  Reduces manual effort and operational overhead.
- **Maintain configuration consistency**  
  Ensures systems remain aligned with defined standards.
- **Reduce manual errors**  
  Minimizes risk caused by human intervention.
- **Enable predictable deployments**  
  Provides repeatable and reliable execution outcomes.
---
## 5. Key Features of Ansible Playbooks

- **Human-readable YAML syntax**  
  Makes playbooks easy to understand, review, and maintain.
- **Agentless execution model**  
  Simplifies infrastructure by avoiding agent installation on nodes.
- **Idempotent task execution**  
  Ensures repeated runs do not cause unintended changes.
- **Modular roles and reusable tasks**  
  Promotes standardization and reuse across projects.
---

## 6. Workflow of Anisble Playbook
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/bd21f7ff-195e-4f65-a69e-99adf34c9c2b" />

---
## 7. Required Inputs

The following inputs are required before executing the Ansible playbook:

- **Inventory file**  
  Defines the target hosts and host groups.
- **Variable files or extra variables**  
  Provide environment-specific configuration values.
- **SSH connectivity to target nodes**  
  Ensures Ansible can connect to managed systems.
- **Required credentials or access permissions**  
  Allows tasks to execute successfully on target hosts.

### inventory.ini
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/7dde839e-6827-4f51-91b0-b9a791db4ff9" />

### Playbook.yml
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/e908cdcb-29e5-47ac-8b28-f68199f7878a" />

---

## 8. Execution Steps

The following steps must be followed to execute the Ansible playbook in a controlled manner:

- **Validate inventory and target hosts**  
  Ensures the correct systems are selected before execution.
- **Review required variables and inputs**  
  Confirms all mandatory parameters are defined.
- **Execute the playbook**  
  Run the playbook using the `ansible-playbook` command.
- **Monitor task execution and logs**  
  Tracks progress and identifies failures during execution.
  ### Testing And Running
```bash
 ansible-playbook -i inventory first-playbook.yml
```

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/12124601-ab7c-4568-b727-ab77ac850d6e" />

---

## 9. Validation Checks

After playbook execution, the following checks must be performed to confirm successful automation:

- **Review Ansible play recap**  
  Confirms no tasks have failed.
- **Verify expected configurations or services**  
  Ensures the desired state has been applied on target systems.
- **Check logs and outputs if applicable**  
  Identifies any warnings or post-execution issues.
---
## 10. Conclusion

This SOP establishes a standardized and controlled approach for using Ansible playbooks to deliver reliable automation across environments. By clearly defining purpose, scope, execution steps, required inputs, and validation checks, it ensures consistency, reduces operational risk, and supports compliance requirements.

---
## 11. Contact Information

| Name            | Team    | Contact Type | Details |
| --------------- | ------- | ------------ | ------- |
| Shreyas Awasthi | Saarthi | Email        | shreyas.awasthi.snaatak@mygurukulam.CO |

---
## 12. References

| Descriptions | Links |
|-------------|------|
| Ansible Official Documentation | [Ansible Documentation](https://docs.ansible.com/) |
| Ansible Playbooks Guide | [Playbooks Introduction](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html) |
| Ansible Inventory Documentation | [Inventory Guide](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) |
| Ansible Best Practices | [Ansible Best Practices](https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html) |

---
