
# Jinja Template (Ansible)

### Document Details

| Author          | Created    | Version | Last updated by | Last Edited On | L0 Reviewer | L1 Reviewer | L2 Reviewer |
| --------------- | ---------- | ------- | --------------- | -------------- | ----------- | ----------- | ----------- |
| Shreyas Awasthi | 2026-01-20 | 1.0     | Shreyas Awasthi | 2026-01-27     | Mohit Kumar |             |             |
| Shreyas Awasthi | 2026-01-20 | 1.1    | Shreyas Awasthi | 2026-01-27     | Divya Mishra| Pritam      |
| Shreyas Awasthi | 2026-01-20 | 1.2    | Shreyas Awasthi | 2026-01-28     | Mohit Kumar| Pritam      |

---

## Table of Contents

* [1. Introduction](#1-introduction)
* [2. What is Jinja Template?](#2-what-is-jinja-template)
* [3. Why Jinja Template is Used?](#3-why-jinja-template-is-used)
* [4. Features of Jinja Template](#4-features-of-jinja-template)
* [5.Template Structure (.j2)](#5-template-structure-(.j2))
* [6. Usage with Ansible](#6-usage-with-ansible)
* [7. Best Practices](#7-best-practices)
* [8. Security Considerations](#8-security-considerations)
* [9. Conclusions](#9-conclusion)
* [10. Contact-Information](#10-contact-information)
* [11. References](#11-references)

---

## 1. Introduction

This document provides a clear, practical overview of how Jinja templates are structured, maintained, and applied in real-world automation workflows.

---

## 2. What is Jinja Template?

Jinja is a simple template engine, also known as Jinja templating (.j2), used to create dynamic files by replacing placeholders with actual values. It allows one template to be reused for multiple configurations, making file management easier, consistent, and efficient across different environments.

---

## 3. Why Jinja Template is Used?

- **Configuration Flexibility**  
  Jinja makes configuration files adaptable without rewriting them.
- **Reduced Duplication**  
  Common patterns can be reused across multiple files.
- **Easy Updates**  
  Changes can be made in one place and reflected everywhere.
- **Time Saving**  
  Templates reduce the effort needed to manage multiple files.
- **Consistent Output**  
  All generated files follow the same format and structure.

---

## 4. Features of Jinja Template

* **Variables**
  Insert dynamic values using placeholders.
* **Conditional Statements**
  Control content inclusion using conditions.
* **Loops**
  Generate repeated blocks automatically.
* **Filters**
  Transform variable output (e.g., uppercase, default values).
* **Comments**
  Add inline documentation without affecting output.

---


## 5. Template Structure (.j2)
### Template File (nginx.conf.j2)

```bash
server {
    listen {{ http_port }};
    server_name {{ server_name }};

    location / {
        proxy_pass http://{{ backend_host }}:{{ backend_port }};
    }
}
```

### Playbook Using the Template

```bash
- hosts: web
  vars:
    http_port: 80
    server_name: example.com
    backend_host: 127.0.0.1
    backend_port: 5000

  tasks:
    - name: Deploy nginx config from template
      template:
        src: nginx.conf.j2
        dest: /etc/nginx/sites-available/nginx.conf
```
- Variables (http_port, server_name, etc.) are defined in the playbook.
- Template module copies the .j2 file to the target system, replacing Jinja2 placeholders ({{ variable }}) with actual values.
Result → Each server gets its own customized nginx.conf.
### Dynamic Templates
- Dynamic Content: This is the content of a template generated or modified during run-time, depending on input variables and logic defined in the template.

---
## 6. Usage with Ansible

* Jinja templates are commonly used with the Ansible `template` module.
* Variables are passed from inventory files, playbooks, or roles.
* Templates are rendered on the managed nodes with correct values.

**Typical File Path**

```
roles/<role_name>/templates/config.j2
```

---
## 7. Best Practices

* Keep templates simple and readable.
* Use meaningful variable names.
* Avoid hardcoding environment-specific values.
* Store templates under version control.
* Add comments for complex logic.

---

## 8. Security Considerations

* Do not hardcode secrets in templates.
* Use vaults or encrypted variables for sensitive data.
* Restrict access to template repositories.
* Review templates as part of standard code reviews.

---

## 9. Conclusion

Jinja templates provide a structured and scalable way to manage dynamic configurations. By following established practices and maintaining clean templates, teams can achieve consistency, reduce operational overhead, and support long-term maintainability.

---

## 10. Contact Information

| Name            | Team    | Contact Type | Details                                                                                 |
| --------------- | ------- | ------------ | --------------------------------------------------------------------------------------- |
| Shreyas Awasthi | Saarthi | Email        | [shreyas.awasthi.snaatak@mygurukulam.CO](mailto:shreyas.awasthi.snaatak@mygurukulam.CO) |

---

## 11. References

| Descriptions | Links |
|-------------|------|
| Jinja Official Documentation | [Jinja Documentation](https://jinja.palletsprojects.com/en/latest/) |
| Jinja Template Designer Guide | [Template Designer Guide](https://jinja.palletsprojects.com/en/latest/templates/) |
| Ansible Jinja Templating Guide | [Ansible Jinja Templates](https://docs.ansible.com/ansible/latest/user_guide/playbooks_templating.html) |

---
