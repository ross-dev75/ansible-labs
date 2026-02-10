# 01 – Getting Started

This document explains how to set up a local Ansible + Containerlab lab using WSL, Docker, and Ubuntu containers.

Goal:
Build a repeatable environment for learning network automation and security workflows.

---

# Environment Overview

This lab runs on:

- Windows 11 host
- WSL2 (Ubuntu Linux)
- Docker (container runtime)
- Containerlab (network topology orchestration)
- Ansible (automation engine)

All automation is executed from inside WSL.

---

# Step 1 – Install WSL

Install:

wsl --install

Reboot after installation.

Verify:

wsl -l -v

---

# Step 2 – Install Ansible

sudo apt update  
sudo apt install -y ansible git python3-pip

Verify:

ansible --version

---

# Step 3 – Install Docker

sudo apt install -y docker.io  
sudo usermod -aG docker $USER  
newgrp docker  
sudo service docker start

Test:

docker run --rm hello-world

---

# Step 4 – Install Containerlab

bash -c "$(curl -sL https://get.containerlab.dev)"

Verify:

containerlab version

---

# Step 5 – Deploy Lab

sudo containerlab deploy -t topologies/basic.clab.yml

Verify:

docker ps --format "table {{.Names}}\t{{.Status}}"

---

# Step 6 – Test Ansible

ansible all -m ping -i inventories/hosts.yml

Success returns "pong".

---

# Key Lessons

- Docker provides disposable lab targets
- Ansible requires Python on targets
- Containerlab creates realistic network layouts
- Inventory defines where Ansible runs tasks

---

# Tear Down Lab

sudo containerlab destroy -t topologies/basic.clab.yml

