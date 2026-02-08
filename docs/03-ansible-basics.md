# 03 – Ansible Basics

This document summarizes the core Ansible concepts learned while building this lab.

Understanding these basics is important before moving into advanced automation.

---

# What Ansible Is

Ansible is an automation tool used for:

- Configuration management
- System provisioning
- Orchestration
- Infrastructure as Code

It is agentless and typically communicates using SSH or APIs.

---

# Control Node vs Managed Nodes

Control Node:
The system running Ansible.
In this lab, this is the WSL Ubuntu machine.

Managed Nodes:
Systems Ansible controls.
In this lab, these are the containers (r1, r2, radius).

Ansible sends commands from the control node to managed nodes.

---

# Inventory

The inventory defines:

- Hosts
- Groups
- Connection methods

Example structure:

routers:
  hosts:
    r1:

Meaning:
A group named "routers" contains host r1.

Inventory answers the question:
WHERE Ansible runs tasks.

---

# Playbooks

Playbooks are YAML files that define tasks.

Example structure:

- hosts: all
  tasks:
    - ping:

Meaning:
Run the ping module on all hosts.

Playbooks answer the question:
WHAT to do.

---

# Modules

Modules are the actions Ansible performs.

Examples:

- ping
- apt
- copy
- service
- raw

Modules answer the question:
HOW tasks are executed.

---

# Ad-Hoc Commands

Ad-hoc commands are one-line automation tasks.

Example:

ansible all -m ping

Useful for:
- Connectivity tests
- Quick checks
- Simple automation

---

# The Ping Module

Important:
This is NOT ICMP ping.

It tests:
- Ansible connectivity
- Python availability on the target
- Command execution ability

Success returns:
pong

---

# Python Requirement

Most Ansible modules require Python on the target system.

If Python is missing, modules fail.

This is why the Ubuntu container initially failed.

---

# Raw Module

The raw module runs commands directly on the system.

Example:

ansible aaa -m raw -a "apt-get install -y python3"

Used for:
- Bootstrapping Python
- Fixing broken hosts
- Low-level commands

The raw module does NOT require Python.

---

# Idempotency

A core Ansible principle.

Idempotent means repeatable without causing changes if the system is already in the desired state.

Example:
Installing a package twice should not reinstall it if already present.

Good automation is idempotent.

---

# Why Idempotency Matters

Ensures:
- Consistency
- Predictable outcomes
- Safe re-runs
- Reliable automation

This is critical in production environments.

---

# Key Mental Model

Inventory = WHERE  
Playbook = WHAT  
Modules = HOW  

Remembering this simplifies Ansible usage.

---

# Key Takeaways

- Ansible is agentless
- Inventory structure matters
- Python is required on targets
- Raw module is for bootstrapping
- Idempotency is a core goal
- Ad-hoc commands are useful for quick tasks

Mastering these basics enables more advanced automation.
