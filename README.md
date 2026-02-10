# Ansible Network Automation Lab

This repository contains a personal lab environment for learning and practicing Ansible and network automation concepts.

The lab is designed to be repeatable and easy to rebuild, allowing consistent experimentation with automation workflows and network services.

---

## Lab Environment

Current components:

- WSL Ubuntu control node  
- Docker-based lab hosts  
- Containerlab for topology orchestration  
- FRR containers acting as routers  
- Ubuntu container for AAA/RADIUS testing
- Linux containers to act as workstations
- Ansible as the automation tool  

All components run locally.

---

## Documentation

- [Getting Started](docs/01-getting-started.md)
- [Lab Architecture](docs/02-lab-architecture.md)
- [Ansible Basics](docs/03-ansible-basics.md)

---

## Quick Start

1) Deploy the lab:

sudo containerlab deploy -t lab/topologies/basic.clab.yml

2) Bootstrap python to the 'aaa' and 'workstations' group:

ansible-playbook -i inventories/lab/hosts.yml playbooks/bootstrap.yml

3) Verify Ansible connectivity:

ansible all -m ping -i inventories/lab/hosts.yml

---

## Tear Down

sudo containerlab destroy -t lab/topologies/basic.clab.yml

---

## Objectives

This lab is used to practice:

- Ansible playbooks and inventory management  
- Automation of multi-node environments  
- AAA/RADIUS concepts  
- Infrastructure-as-code approaches  
- Troubleshooting automation tasks  

---

## Status

This is an active learning environment that will expand over time as additional scenarios and tools are tested.



