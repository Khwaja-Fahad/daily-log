## Room 2: Virtualisation Basics

### Introduction and Virtualisation Overview
- **Old rule:** one server = one application. Problems:
  - High cost (hardware, electricity, cooling, space)
  - Low use (many servers sat at only 5 to 20 percent)
  - Slow to set up and hard to scale
- **Virtualisation** lets one physical computer act like several separate computers, so applications can share hardware safely.
- Analogy: a ten-floor building with one tenant is wasteful. Splitting it into apartments lets many tenants share the electricity and water.

| In the analogy | In the real world |
|----------------|-------------------|
| The building | The physical server |
| The apartments | Virtual machines (VMs, called lab machines in the room) |
| The tenants | Applications or operating systems |
| The building manager | The hypervisor |
| Rooms inside an apartment | Containers |

### Virtualisation Components
**Hypervisor:** software that divides a physical computer into virtual ones. It gives each VM its own share of CPU, memory and storage, keeps them isolated, and manages their life cycle (start, stop, pause, clone, delete).
- **Type 1:** runs directly on the hardware. Fast and efficient, used for servers and data centres.
- **Type 2:** runs inside an existing operating system. Easy to install, used for learning, testing and small setups. Examples: VirtualBox, VMware Workstation.

**Virtual machine (VM):** a virtual computer with its own virtual CPU, RAM, storage, network and operating system.
- Isolated from other VMs, so if one breaks, the others keep working.

**Container:** a lightweight, isolated environment for one application, packaged with its libraries and dependencies.
- Shares the host's **kernel**, so it starts almost instantly and uses fewer resources than a VM.
- Because of the shared kernel, it must match the host type (a Linux container needs a Linux kernel).
- **Docker** is a popular platform for building and running containers. A **container image** is the template a container is made from.

| | Virtual machine | Container |
|---|---|---|
| Includes | Its own full operating system | Only the app and its dependencies |
| Start time | Slower | Very fast |
| Resource use | Heavier | Lighter |
| Isolation | Stronger | Lighter (shares the host kernel) |

### Managing Virtual Machines
In a simulated company, I used a virtualisation manager to:
- Read the **summary** of the environment, the list of VMs, and the physical hosts
- Spot a VM in an **error state** and restart it to restore a service (email)
- **Create a VM** by choosing its name, CPU cores, memory and disk size
- Check **host usage**: which servers have spare capacity, which are close to full, and which are disconnected
- Reporting a nearly full host is part of the job, because it can cause outages later.

### Key benefits
Cost savings, better resource use, safe testing, fast deployment, flexibility, portability, scalability, and central management.

## Connection to what I already know
- A hypervisor is a layer between the hardware and the operating systems, similar to how an operating system sits between apps and hardware.
- A VM has the same parts as a real computer: CPU, RAM, storage and network.
- Setting up a Kali Linux or other practice machine on my own laptop (a Type 2 hypervisor) is the usual way to build a safe home lab.
- Servers in the client-server model are often VMs or containers today.
- A container's shared kernel connects to the kernel and user space idea.

## Why this matters for security
- **Safe testing:** I can test suspicious files or practise attacks in an isolated VM, not on my main computer. For malware, use a separate OS or no connection to the host, and take a **snapshot** to restore a clean state.
- **Network isolation:** set lab VMs to host-only or isolated networks, so practice tools cannot reach real systems.
- **Isolation is strong but not perfect.** A **VM escape** (breaking out of a guest to reach the host) is rare but serious, so keep the hypervisor patched.
- **Containers share the kernel,** so a kernel flaw or a badly configured container can affect the host and other containers. Use trusted images and keep them updated.
- **One host, many VMs:** if the host or hypervisor is compromised, everything on it is at risk, so defenders protect these carefully.
- **Cloud computing** is built on virtualisation and containers, which is where much of modern security work happens.
- Only use lab tools inside my own VMs or approved lab environments.

## Full forms
- **VM:** Virtual Machine
- **CPU:** Central Processing Unit
- **RAM:** Random Access Memory
- **OS:** Operating System

## Time and completion
- Time spent : 30 minutes
- room completed: 100%
