# K3s-Development-Homelab

> A production-grade Kubernetes development environment built from scratch on Arch Linux, demonstrating modern DevOps practices with isolated dev containers, GitOps workflows, and Infrastructure as Code.

## Table of Contents

- Overview
- Architecture
- Features
- Prerequisites
- Getting Started
- Usage Guide
- Project Structure
- Learning Outcomes
- Roadmap
- Contributing
- Acknowledgments
- License

### Overview

This repository documents my journey building a professional-grade Kubernetes homelab environment. The goal is to demonstrate real-world DevOps skills through hands-on infrastructure management, containerization, and GitOps practices.

Why this matters:

- Production-aligned workflows: Uses the same tools and patterns employed in enterprise environments

- Reproducible environments: Dev containers ensure consistency across machines

- Infrastructure as Code: All configurations are version-controlled and declarative

- Skill validation: Demonstrates practical Kubernetes knowledge for potential employers

### Architecture

```bash
┌─────────────────────────────────────────────────────────┐
│                    Arch Linux (Host)                    │
│            Encrypted with LUKS on LVM                   │
│                                                         │
│  ┌────────────────────────────────────────────────┐   │
│  │         Hyprland (Wayland Compositor)          │   │
│  │                                                │   │
│  │  ┌──────────────────────────────────────┐    │   │
│  │  │    VSCode + Dev Containers           │    │   │
│  │  │                                      │    │   │
│  │  │  ┌────────────────────────────┐     │    │   │
│  │  │  │  Debian Dev Container      │     │    │   │
│  │  │  │                            │     │    │   │
│  │  │  │  ┌──────────────────────┐ │     │    │   │
│  │  │  │  │   k3d K3s Cluster    │ │     │    │   │
│  │  │  │  │                      │ │     │    │   │
│  │  │  │  │  • Server Node       │ │     │    │   │
│  │  │  │  │  • Agent Node 1      │ │     │    │   │
│  │  │  │  │  • Agent Node 2      │ │     │    │   │
│  │  │  │  │                      │ │     │    │   │
│  │  │  │  │  Workloads:          │ │     │    │   │
│  │  │  │  │  - Helm Charts       │ │     │    │   │
│  │  │  │  │  - Custom Apps       │ │     │    │   │
│  │  │  │  │  - GitOps Pipelines  │ │     │    │   │
│  │  │  │  └──────────────────────┘ │     │    │   │
│  │  │  │                            │     │    │   │
│  │  │  │  Tools: kubectl, helm,    │     │    │   │
│  │  │  │         k3d, git, docker  │     │    │   │
│  │  │  └────────────────────────────┘     │    │   │
│  │  └──────────────────────────────────────┘    │   │
│  └────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

### Key Components

- Host OS: Arch Linux with full-disk encryption (LUKS on LVM)
- Desktop Environment: Hyprland (modern Wayland compositor)
- Containerization: Docker + containerd runtime
- Development: VSCode with Dev Containers extension
- Kubernetes: k3d (K3s in Docker) for lightweight clusters
- Package Management: Helm 3 for application deployment
- Version Control: Git + GitHub integration

### Features

Infrastructure

Encrypted storage - LUKS on LVM for data security
Isolated environments - Dev containers prevent host pollution
Multi-node clusters - 3-node K3s setup (1 server, 2 agents)
Disposable infrastructure - Clusters can be created/destroyed instantly

Development Workflow

Declarative configuration - Infrastructure as Code with YAML manifests
Package management - Helm charts for application deployment
Version control - All configs stored in Git
Reproducible builds - Dev container ensures consistent environment

Learning Focus

Kubernetes fundamentals - Pods, Deployments, Services, ReplicaSets
Helm best practices - Chart creation, values customization, releases
GitOps methodology - Declarative, version-controlled infrastructure
Container orchestration - Scaling, networking, storage

### Prerequisites

Hardware Requirements

- CPU: 4+ cores recommended
- RAM: 16GB minimum, 32GB recommended
- Storage: 128GB minimum, 256GB recommended (SSD preferred)

Software Requirements

- Arch Linux (or Arch-based distribution)
- Docker or containerd runtime
- VSCode with Dev Containers extension
- Git for version control

Knowledge Prerequisites

- Basic Linux command-line proficiency
- Understanding of containers (Docker basics)
- Familiarity with text editors (vim/nano)
- Git fundamentals (clone, commit, push/pull)

### Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/k3s-homelab.git
cd k3s-homelab
```

### 2. Open in Dev Container

```bash
# Open in VSCode
code .

# When prompted, click "Reopen in Container"
# Or use Command Palette: Ctrl+Shift+P → "Dev Containers: Reopen in Container"
```

VSCode will automatically:

- Build the dev container from .devcontainer/devcontainer.json
- Install kubectl, Helm, k3d, and dependencies
- Configure the development environment

### 3. Verify Installation

Inside the dev container terminal:

```bash
# Check tool versions
k3d version
kubectl version --client
helm version
docker ps
```

### Usage Guide

### Project Structure

```bash
k3s-homelab/
├── .devcontainer/
│   └── devcontainer.json          # Dev container configuration
├── k8s-manifests/
│   ├── deployment.yaml            # Example deployment manifest
│   └── service.yaml               # Example service manifest
├── helm-charts/
│   └── my-chart/
│       ├── Chart.yaml             # Chart metadata
│       ├── values.yaml            # Default values
│       └── templates/             # Kubernetes templates
│           ├── deployment.yaml
│           ├── service.yaml
│           └── ...
├── docs/
│   ├── architecture.md            # Architecture details
│   ├── troubleshooting.md         # Common issues & solutions
│   └── best-practices.md          # Kubernetes best practices
├── scripts/
│   ├── setup-cluster.sh           # Automated cluster setup
│   └── cleanup.sh                 # Resource cleanup script
├── .gitignore
├── LICENSE
└── README.md
```

### Learning Outcomes

Through this project, I've gained hands-on experience with:

### Kubernetes Core Concepts

- Pod lifecycle management and debugging
- Deployments for application scaling
- Services for networking and load balancing
- ReplicaSets for maintaining desired state
- ConfigMaps and Secrets for configuration management

### Helm Package Management

- Chart structure and templating
- Values files for environment-specific configs
- Release management (install, upgrade, rollback)
- Repository management
- Custom chart development

### DevOps Practices

- Infrastructure as Code (IaC)
- Declarative configuration
- Version control for infrastructure
- Isolated development environments
- GitOps workflows

### Systems Administration

- Linux system configuration
- Storage encryption (LUKS/LVM)
- Container runtime management
- Network troubleshooting
- Security best practices

### Roadmap

### Current Phase: Foundation

- [X] Encrypted Arch Linux LUKS on LVM installation
- [X] Hyprland desktop environment
- [X] Dev containers setup
- [X] K3s cluster deployment
- [X] Helm chart creation

### Next Phase: GitOps

- [] ArgoCD installation and configuration
- [] Automated deployments from Git
- [] Multi-environment setup (dev/staging/prod)
- [] Secrets management with Sealed Secrets
- [] Prometheus + Grafana monitoring

### Future Enhancements

- [] CI/CD pipeline with GitHub Actions
- [] Custom application development
- [] Service mesh (Istio/Linkerd)
- [] Persistent storage with Longhorn
- [] Ingress controllers (Traefik/NGINX)
- [] Certificate management (cert-manager)
- [] Backup and disaster recovery

### Contributing

This is a personal learning project, but suggestions and feedback are welcome!

### How to contribute

1. Fork the repository
2. Create a feature branch (git checkout -b feature/improvement)
3. Commit your changes (git commit -m 'Add some improvement')
4. Push to the branch (git push origin feature/improvement)
5. Open a Pull Request

### Areas where contributions are welcome:

- Documentation improvements
- Best practices suggestions
- Security enhancements
- Automation scripts
- Troubleshooting guides

### Acknowledgments

**Inspiration:**

- Mischa van den Burg - DevOps workflows and homelab philosophy
- The Arch Linux community for excellent documentation
- System76 for COSMIC desktop development

### Resources

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Helm Documentation](https://helm.sh/docs/)
- [k3d Documentation](https://k3d.io/)
- [Arch Wiki](https://wiki.archlinux.org/)
- [Dev Containers Specification](https://containers.dev/)

Technologies:

- Arch Linux
- Kubernetes (via k3d)
- Helm
- Docker/containerd
- VSCode Dev Containers
- Hyprland

### 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

### 📬 Contact

Lavell Burton

[LinkedIn](linkedin.com/in/benjaminlburton)
[GitHub](https://github.com/BenjaminBurton)
[Email](benjaminlburton@outlook.com)

### Project Status: Active Development 🚧
