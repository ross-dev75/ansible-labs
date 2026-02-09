# 02 – Lab Architecture

This document explains how the Ansible lab is structured and why each component exists.

The goal of this lab architecture is to simulate a small, realistic network environment that can be automated and rebuilt easily.

---

# Topology Overview

The lab consists of five main nodes:

- r1 (FRR router container)
- r2 (FRR router container)
- radius (Ubuntu container acting as AAA server)
- pc1 (Alpine (Linux) container acting as a workstation)
- -pc2 (Alpine (Linux) container acting as a workstation)

Logical connections:

r1 <> r2  
r1 <> radius  
r2 <> radius
r1 <> pc1
r2 <> pc2

This simulates:

- Router-to-router communication
- Router-to-AAA server communication
- Workstations connected to different routers
- Multi-node automation scenarios

---

# Why Containers Instead of Virtual Machines

Containers were chosen because they:

- Start in seconds
- Use minimal resources
- Are easy to destroy and rebuild
- Support automation workflows well

Virtual machines are heavier and slower for iterative labs.

Containers allow fast experimentation.

---

# Why FRR (Free Range Routing)

FRR provides:

- BGP
- OSPF
- Routing features similar to enterprise devices

It allows practice with routing and automation without requiring proprietary vendor images.

This makes it ideal for learning automation concepts.

---

# Why Ubuntu for the RADIUS Node

Ubuntu acts as a general-purpose Linux server.

It is used for:

- FreeRADIUS installation
- AAA simulations
- Security service experiments

This mirrors real environments where Linux servers often host authentication services.

---

# Ansible Control Node

The Ansible control node is the WSL Ubuntu environment.

It runs:

- Ansible
- Docker
- Containerlab

All automation commands originate here.

No agents are installed on targets.

---

# Network Simulation Approach

Containerlab connects nodes using virtual Ethernet links.

This creates realistic networking between containers.

From Ansible's perspective, each container behaves like a host.

---

# Design Philosophy

This lab is designed to be:

- Repeatable
- Disposable
- Script-driven
- Version-controlled in Git

This follows Infrastructure-as-Code principles.

The lab can be rebuilt at any time.

---

# How the Lab Scales

This architecture can be expanded by adding:

- More routers
- Logging servers
- SIEM containers
- Firewall containers
- NAC simulations

The same automation principles apply at larger scale.

---

# Key Takeaways

- Containers enable fast lab creation
- FRR provides routing functionality
- Ubuntu supports security services
- Ansible acts as the automation layer
- Containerlab provides topology orchestration

This combination provides a powerful learning environment for network automation and security.
