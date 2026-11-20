# Day 30 - 2026-11-20

## Rooms completed
1. Cloud Computing Fundamentals (TryHackMe): 100%
2. Linux CLI Basics (TryHackMe): 100%

---

## Room 1: Cloud Computing Fundamentals

### Cloud computing overview
- **Cloud computing** means using computing resources (servers, storage, networking) over the internet instead of running everything on one computer I own.
- It solves the problems of a single machine: users far away get lag, many users at once overload it, and if it is switched off the app is gone.
- The cloud is built on technologies I already know: **virtualisation** and **containers**, which let many applications share infrastructure efficiently.

### Benefits and characteristics
| Characteristic | Meaning |
|----------------|---------|
| **Scalability** | Scale up or down as demand changes |
| **On-demand self-service** | Create or remove servers and storage instantly |
| **Pay for what you use** | Charged for usage, not big upfront costs |
| **Security** | The provider protects the infrastructure (but see below) |
| **High availability** | The application keeps running if part of the system fails |
| **Global access** | Users anywhere can reach it |

### Deployment types
| Type | Description | Typical use |
|------|-------------|-------------|
| **Public cloud** | Shared services over the internet | Startups, websites, global apps |
| **Private cloud** | Built for one organisation, more control | Banks, healthcare, government |
| **Hybrid cloud** | A mix of both that work together | Keep sensitive data private, scale publicly in busy periods |

### Service models (renting a place to live)
| Model | Full form | What I manage | Analogy |
|-------|-----------|---------------|---------|
| **IaaS** | Infrastructure as a Service | The operating system and my application | Renting an empty apartment |
| **PaaS** | Platform as a Service | Only my application | Renting a furnished apartment |
| **SaaS** | Software as a Service | Nothing, I just use the software | Staying in a hotel (Gmail, Zoom) |

### Major cloud vendors
- **AWS** (Amazon Web Services) is the market leader.
- Others: **Microsoft Azure** (strong in enterprise and hybrid), **Google Cloud Platform**, Alibaba Cloud, IBM Cloud, Oracle Cloud.
- Large companies use the cloud to scale quickly, stay online during peaks, and avoid managing hardware.

### Practical: deploying a cloud environment
- Worked in a cloud console similar to AWS.
- **Region:** a geographical location where resources live. Choosing one affects speed and legal location of data.
- **EC2** (Elastic Compute Cloud): a virtual computer in the cloud, with CPU and RAM.
- **Instance type:** how powerful the virtual computer is. Bigger means more power and a higher cost.
- Created several instances, then **stopped** the ones not in use and checked **billing**. Stopped machines cost much less, so managing running resources is how cloud costs are controlled.
- IaaS suits security practice, because I get full control of the operating system to install tools and simulate attacks safely.

### Cloud security basics (added from my own reading)
- **Shared responsibility model:** the provider secures the underlying infrastructure, and I secure my own data, accounts, configuration and access. In IaaS I carry more of the responsibility than in SaaS.
- Common cloud problems come from **misconfiguration** (for example storage left open to the internet) and **weak access control**, not from the provider's hardware.
- Use **least privilege**, strong authentication, logging and monitoring.
- Azure equivalents of AWS ideas: a Virtual Machine is like EC2. This matters because the job I am aiming for mentions Microsoft Azure.

---

## Room 2: Linux CLI Basics

### The scenario
A guided first day as a new intern on a cyber operations team: find a file, read it, and collect a small system report, all from the terminal.

### Why the terminal matters
- It is faster than clicking, gives more control, and many security tools only run in the terminal.
- **CLI** = Command Line Interface.

### Commands I used
| Command | What it does |
|---------|--------------|
| `pwd` | Prints the folder I am in (print working directory) |
| `ls` | Lists files and folders |
| `ls -l` | Detailed list: permissions, owner, size, date |
| `ls -al` | Also shows **hidden files** (names starting with a dot) |
| `cd folder` / `cd ..` | Moves into a folder / up one level |
| `find ~ -name file` | Searches my home directory for a file by name |
| `cat file` | Prints a file's contents |
| `whoami` | Shows the current user |
| `uname -a` | Shows kernel version, hostname and architecture |
| `uname` | Shows only the operating system name |
| `df -h` | Shows disk space in human-readable sizes |
| `cat /etc/os-release` | Shows the Linux distribution name and version |

### Things I learned
- **Hidden files are not secret.** Linux hides names starting with a dot by default. `ls -al` shows them, and important data is often kept in hidden folders.
- `~` means my home directory, so `find ~` searches only there.
- `-h` means human readable (G and M instead of long byte counts).
- `tmpfs` entries are temporary file systems in RAM, not on the disk.
- `/etc` holds configuration and information files. `os-release` is often clearer than `uname` for the distribution name.
- The kernel version in `uname -a` matters because known vulnerabilities depend on it.
- A real task needs combining commands: find a file, go to its folder, read it.

## Connection to what I already know
- Cloud virtual machines are the same idea as a hypervisor and VMs, run by a provider.
- A cloud instance is a client-server machine reachable over the network, so firewall rules and open ports still matter.
- `find`, `cat`, `ls` and `cd` are the same investigation commands, now used in a guided mission.
- Checking the kernel version, disk space and distribution is the first step when examining a system during an incident.
- Hidden files and `/etc` are exactly where an investigator looks for backdoors and configuration changes.

## Why this matters for security
- **Cloud security** is a large part of modern security work, and the job ads I am targeting name cloud platforms.
- A **misconfigured** cloud resource can expose data to the whole internet, so defenders check configuration and access regularly.
- Stopping unused machines reduces both **cost** and **attack surface**.
- Collecting system information (user, kernel, disk, distribution) is the first step of any investigation.
- Only use cloud accounts and machines I own or am authorised to use, and watch the billing on any real account.

## Full forms
- **IaaS / PaaS / SaaS:** Infrastructure / Platform / Software as a Service
- **AWS:** Amazon Web Services
- **EC2:** Elastic Compute Cloud
- **GCP:** Google Cloud Platform
- **CLI:** Command Line Interface
- **VM:** Virtual Machine
- **RAM:** Random Access Memory

## Time and completion
- Time spent today: 90 minutes
- Both rooms: 100%
