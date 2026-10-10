<div align="center">

# Kumo — Cloud Infrastructure Canvas & Bidirectional Terraform HCL Compiler

**Visual Cloud Architecting Engine with Real-Time HCL Generation, Cost Modeling, and Capacity Simulation**

<p align="center">
  <a href="#roadmap"><img src="https://img.shields.io/badge/Status-Active%20Development-blueviolet?style=flat-square" alt="Status: Active Development"></a>
  <a href="https://www.terraform.io/"><img src="https://img.shields.io/badge/Terraform-HCL%20v1.9+-844FBA?style=flat-square&logo=terraform" alt="Terraform HCL"></a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API"><img src="https://img.shields.io/badge/Rendering-WebGL%20%2F%20WebGPU-informational?style=flat-square" alt="WebGL / WebGPU"></a>
  <a href="https://go.dev/"><img src="https://img.shields.io/badge/Engine-Go%201.23+-00ADD8?style=flat-square&logo=go" alt="Go 1.23+"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow?style=flat-square" alt="MIT License"></a>
</p>

<p align="center">
  Visual cloud topology designer with bidirectional Terraform HCL compilation, sub-second cost estimation, and fault-domain simulation.<br>
  WebGL canvas rendering · Bidirectional AST parser · AWS / GCP / Azure multi-cloud provider modeling.
</p>

<p align="center">
  <a href="#quick-flow">Quick Flow</a> •
  <a href="#system-architecture">Architecture</a> •
  <a href="#core-architectural-pillars">Core Pillars</a> •
  <a href="#compiler-pipeline">Compiler Pipeline</a> •
  <a href="#planned-specification">Specification</a> •
  <a href="#engineering-roadmap">Roadmap</a>
</p>

</div>

---

> [!NOTE]
> **Architecture & Engineering Blueprint**
> Kumo is under active architectural development. This repository establishes the core system specification, bidirectional HCL compilation intermediate representation (IR), and technical roadmap.

---

## Quick Flow

```
Visual Canvas Drag-and-Drop  →  Graph Topology IR  →  Bidirectional HCL CodeGen  →  Live Cost & Blast Radius Audit
```

---

## System Architecture

```mermaid
flowchart TD
    subgraph CanvasLayer ["Visual Interaction Tier (WebGL / WebGPU)"]
        Canvas["Infinite Spatial Canvas<br/>Hardware-Accelerated Node Graph Rendering"]
        Inspector["Resource Property Inspector<br/>Provider Schema Driven Validation"]
        MiniMap["Viewport Navigator & Dependency MiniMap"]
        Canvas --> Inspector
        Canvas --> MiniMap
    end

    subgraph CompilerLayer ["Bidirectional Compilation Core (Go / WASM Engine)"]
        Parser["HCL v2 Lexer & AST Parser<br/>Bidirectional HCL <--> Graph IR"]
        GraphIR["Directed Acyclic Graph IR<br/>Node: Resources / Edges: References"]
        CodeGen["Deterministic HCL Code Generator<br/>Formatted main.tf, variables.tf, outputs.tf"]
        Parser --> GraphIR
        GraphIR --> CodeGen
    end

    subgraph AnalyticalEngines ["Real-Time Intelligence Engines"]
        CostEngine["Infracost Real-Time Pricing Engine<br/>Sub-Second Monthly Cloud Bill Estimation"]
        SecurityEngine["Blast-Radius & Least-Privilege Sentinel<br/>IAM Graph Traversals & Security Group Overlap"]
        FaultSim["AZ / Region Failure Simulator<br/>High-Availability Boundary Analysis"]
    end

    subgraph OutputArtifacts ["Infrastructure Artifacts"]
        TFModule["Deployable Terraform Module<br/>100% Native HashiCorp HCL"]
        ArchDiagram["Exportable Vector Architecture SVG / PNG"]
    end

    Canvas <-->|"Bidirectional State Sync"| GraphIR
    GraphIR --> CostEngine
    GraphIR --> SecurityEngine
    GraphIR --> FaultSim
    CodeGen --> TFModule
    Canvas --> ArchDiagram
```

---

## Core Architectural Pillars

### 01. GPU-Accelerated Infinite Topology Canvas
* **High-Density Node Rendering**: Powered by WebGL/WebGPU to smoothly render hundreds of cloud resources, VPC subnets, security group linkages, and peering connections at continuous 60fps.
* **Spatial Semantic Zoom**: Transitions dynamically from high-level multi-region VPC topologies down to individual EC2, Lambda, and IAM policy attribute definitions.

### 02. Bidirectional HCL AST Parser & Compiler
* **True Two-Way Synchronization**: Edits made on the visual canvas automatically produce clean, idiomatic Terraform HCL. Conversely, pasting existing `.tf` files generates the visual topology layout instantaneously.
* **Lossless Round-Tripping**: Preserves custom comments, local variables, and variable interpolation syntax across round-trip edits without stripping developer formatting.

### 03. Sub-Second Real-Time Cost Estimation Engine
* **Instantaneous Financial Telemetry**: Queries pricing heuristics in real-time as resources and instances are provisioned on canvas (e.g. EC2 instance family switches, RDS multi-AZ deployments, NAT Gateway traffic estimates).
* **Budget Threshold Guardrails**: Highlights cost deltas dynamically before infrastructure changes are exported to Git or CI/CD pipelines.

### 04. Blast-Radius Analysis & Security Sentinel
* **IAM Least-Privilege Graph Traversals**: Automatically maps permissions, role assumptions, and public egress paths across cloud resources.
* **Fault-Domain Resilience Auditing**: Simulates single Availability Zone or Regional outages by severing nodes, demonstrating service continuity and failover readiness visually.

---

## Compiler Pipeline

```
┌─────────────────────────┐
│ Visual Topology Graph   │
│ (Nodes, Subnets, Edges) │
└────────────┬────────────┘
             │ State Dispatch
             ▼
┌─────────────────────────┐
│ Intermediate Rep (IR)   │ ◄──── Bidirectional Bridge ────► ┌─────────────────────────┐
│ (Dependency DAG)        │                                   │ Native Terraform HCL    │
└────────────┬────────────┘                                   │ (main.tf / provider.tf) │
             │ Compilation                                    └─────────────────────────┘
             ▼
┌─────────────────────────┐
│ Static Analysis Audit   │
│ • Cost Delta (Infracost)│
│ • IAM Blast Radius      │
│ • Trivy Policy Sentinel │
└────────────┬────────────┘
             │ Emit
             ▼
┌─────────────────────────┐
│ Production TF Artifacts │
└─────────────────────────┘
```

---

## Planned Specification

### Provider Support Target
* **Amazon Web Services (AWS)**: VPC, Subnet, Route Table, IGW, EC2, ECS, EKS, RDS, S3, IAM, CloudFront, Lambda.
* **Google Cloud Platform (GCP)**: VPC Network, Compute Engine, Cloud SQL, Cloud Storage, GKE, Cloud Run.
* **Microsoft Azure**: VNet, Subnets, Virtual Machines, Azure SQL, Blob Storage, AKS.

### Target Performance Benchmarks
* **AST Parse Latency**: `< 50ms` for typical configurations under 1,000 resources.
* **Canvas Frame Budget**: Fixed `16.6ms` (60fps) during active pan, zoom, and multi-node drag interactions.
* **Cost Query Cache**: Sub-10ms lookup against cached local provider pricing matrices.

---

## Engineering Roadmap

- [x] **Milestone 1**: Core system architecture, HCL bidirectional AST intermediate representation (IR) specification.
- [ ] **Milestone 2**: Standalone Go-based HCL lexer and AST round-trip serializer (`kumo-core`).
- [ ] **Milestone 3**: WebGL visual node graph canvas with reactive state synchronization.
- [ ] **Milestone 4**: AWS Provider schema generator and component palette.
- [ ] **Milestone 5**: Real-time Infracost pricing integration and visual blast-radius security overlay.
- [ ] **Milestone 6**: Local CLI compilation binary and browser-based WebAssembly (WASM) distribution.

---

## Contributing

1. Fork the repository.
2. Clone your fork:
   ```bash
   git clone https://github.com/tanmayythakare/kumo.git
   ```
3. Create your feature branch:
   ```bash
   git checkout -b feat/your-feature-name
   ```
4. Commit your changes:
   ```bash
   git commit -m "feat: add descriptive feature summary"
   ```
5. Push to your branch and submit a Pull Request.

---

## License

This project is open-source and distributed under the **[MIT License](LICENSE)**.

---

## Author

**Tanmay Thakare**
* GitHub: [@tanmayythakare](https://github.com/tanmayythakare)
* Email: [tanmayrthakare@gmail.com](mailto:tanmayrthakare@gmail.com)
* LinkedIn: [Tanmay Thakare](https://www.linkedin.com/in/tanmaythakare)

---

<div align="center">
  <a href="https://github.com/tanmayythakare">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=16&pause=2000&color=38BDF8&center=true&vCenter=true&width=360&lines=Built+by+Tanmay+Thakare+%F0%9F%90%B1" alt="Built by Tanmay Thakare 🐱" />
  </a>
</div>
