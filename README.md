# The IT Industry — Interactive CS Domains Mind Map

An interactive, zero-dependency mind map that visualizes the modern Information Technology and Computer Science ecosystem. Rather than grouping by fleeting tech stacks or tools, it organizes domains by **the fundamental problems they solve** and offers both an academic/engineering taxonomy and a career-focused work lens.

![IT Industry Mind Map Preview](https://img.shields.io/badge/Architecture-Vanilla%20JS%20%2B%20SVG-blue)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero-brightgreen)
![License](https://img.shields.io/badge/License-MIT-orange)

---

## 🌟 Highlights & Features

- **Problem-First Organization**: Explains *why* each discipline exists and *what* engineering challenge it addresses.
- **Dual Perspectives**:
  - **Domain View**: 11 major IT industry branches hierarchically broken down into subfields, core specializations, and foundational technologies.
  - **Work Lens**: A career-oriented perspective grouping roles into 5 functional verbs (**BUILD**, **INTELLIGENCE**, **OPERATE**, **PROTECT**, **INNOVATE**) to help developers identify career tracks based on what work they enjoy.
- **Custom Horizontal Tidy-Tree Engine**: Built from scratch with pure JavaScript and SVG (no external libraries like D3, Cytoscape, or React). Employs an overlap-free dynamic vertical packing algorithm with smooth cubic Bézier connections.
- **Interactive Exploration**:
  - **Click to Expand / Collapse**: Smoothly toggles branches with pan compensation so the clicked node stays in place.
  - **Detail Inspector**: Click any node to open a glassmorphism drawer containing breadcrumbs, the core problem description, and external reference links (MDN, Wikipedia, official specs).
  - **Live Search & Auto-Expansion**: Instantly search fields by typing (press `/`). Ancestor paths expand automatically, matching nodes highlight in amber, and non-matching elements dim.
  - **Fluid Navigation**: Pan via click-and-drag, zoom with mouse wheel or on-screen controls, and auto-fit to screen.
- **Zero Build Step**: Pure HTML5, modern CSS variables, and Vanilla JavaScript. Runs directly in any modern browser without npm, bundlers, or servers.

---

## 🗺️ The 11 Core Domains

| # | Domain | Core Focus / What It Solves | Key Subfields |
|---|---|---|---|
| **1** | **Software Engineering** | Building user-facing and backend software products | Frontend, Web Dev, Backend, Full Stack, Mobile, Desktop, Game Dev, Systems Programming, Distributed Systems, Blockchain / Web3 |
| **2** | **AI & Machine Learning** | Systems that learn, predict, reason, generate, and act | Classical ML, Deep Learning, Foundation Models & LLMs, Generative AI, Agentic AI, NLP, Computer Vision, Speech & Audio, Recommenders, MLOps, AI Safety |
| **3** | **Data & Analytics** | Collecting, processing, transforming, and extracting value from data | Data Analytics, BI, Data Science, Data Engineering, Analytics Engineering (dbt), Big Data, Data Architecture, Database Engineering, Data Governance |
| **4** | **Cloud & Infrastructure** | Providing and scaling the computing platforms modern software runs on | Cloud Engineering (AWS/Azure/GCP), DevOps, CI/CD, Observability, SRE, Platform Engineering, Kubernetes, Infrastructure, FinOps |
| **5** | **Cybersecurity** | Protecting applications, infrastructure, networks, and identities | AppSec (OWASP), Network Security, Cloud Security, Pen Testing, Ethical Hacking, SOC & Incident Response, Digital Forensics, Cryptography, IAM |
| **6** | **Hardware & Embedded** | Computing systems that interface directly with physical devices | Embedded Systems, RTOS, Firmware, PCB & Circuit Design, VLSI / Chip Design, FPGA, IoT, Robotics, Edge Computing, XR / Spatial Computing |
| **7** | **Networking & Telecom** | Communication infrastructure between devices, clouds, and consumers | Network Engineering (OSI, TCP/IP), Data Center Architecture, Wireless (Wi-Fi, Bluetooth), 4G / 5G / 6G RAN & Core, Network Automation, SDN / NFV |
| **8** | **Quality Engineering** | Ensuring software behaves reliably, correctly, securely, and performantly | Automation Testing, Unit & Integration Testing, End-to-End, Performance & Load Testing, Security Testing & Fuzzing, API Testing, Test CI Harnesses |
| **9** | **Enterprise IT** | Technology stacks running operations for large organizations | ERP Systems (SAP, Oracle), CRM Systems (Salesforce), Custom Enterprise Dev (ABAP, Apex), SysAdmin, ITSM (ITIL), Integration Platforms (iPaaS) |
| **10** | **Research & Academia** | Theoretical limits, new algorithms, and frontier computational physics | Algorithms & Complexity (P vs NP), Theory of Computation, Distributed Consensus, AI Alignment, Post-Quantum Cryptography, Computer Architecture, Quantum Computing |
| **11** | **UX / Product** | Defining what to build, for whom, and how people interact with it | UX Research, UI Design, Design Systems, Interaction Design, Product Strategy & Management, Agile / Scrum / Kanban Project Management |

---

## 🎯 The Career "Work Lens"

Instead of categorizing purely by technologies (e.g. Python vs. Rust), the **Work Lens** toggle groups technical disciplines into five fundamental archetypes:

```
Tech Work Archetypes
 ├── BUILD         → Application & Product Engineering (Frontend, Backend, Mobile, Games)
 ├── INTELLIGENCE  → Data & AI Specializations (Data Scientists, ML Engineers, AI Engineers)
 ├── OPERATE       → Reliability, Scale & Networks (Cloud, DevOps, SRE, Platform, Network)
 ├── PROTECT       → Security & Defensibility (Security Engineers, Pen Testers, Architects, QA)
 └── INNOVATE      → Frontier Tech & Hardware (Research Scientists, Embedded, VLSI, Robotics)
```

Click the **"Work lens"** button in the header bar at any time to switch views.

---

## 🚀 Quick Start

Because this project requires no compilation or package installation, getting started takes seconds:

### Option 1: Open Directly
Double-click `index.html` or open it with any web browser:
```bash
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

### Option 2: Run with a Local Static Server
If you prefer running through a local HTTP server:

```bash
# Using Python 3
python -m http.server 8080

# Using Node.js (npx)
npx serve .

# Using PHP
php -S localhost:8080
```
Then navigate to `http://localhost:8080` in your browser.

---

## ⌨️ Controls & Shortcuts

| Action | Control / Shortcut |
|---|---|
| **Pan Canvas** | Click and drag on empty canvas |
| **Zoom In / Out** | Mouse scroll wheel or `+` / `−` buttons |
| **Fit to Screen** | `⤢` button in bottom-right corner |
| **Expand / Collapse Node** | Click on any node pill or its `+` / `–` badge |
| **Inspect Node Details** | Click on any node to reveal the detail panel |
| **Focus Search** | Press `/` |
| **Clear Search / Close Panel** | Press `Esc` or click the `×` button |
| **Toggle Work Lens** | Click **"Work lens"** / **"Domain view"** button |
| **Reset View** | Click **"Reset view"** button |

---

## 🛠️ Architecture & Implementation

The entire application is self-contained within `index.html`:

- **Layout Engine**: A custom left-to-right tidy-tree algorithm (`layout(root)` and `assignY(node, depth)`). Subtrees are dynamically assigned non-overlapping vertical slots (`ROW_STEP = 46px`) based on visible leaf counts, and parent nodes are centered on the midpoint of their visible children.
- **Rendering Layer**: Directly renders `<svg>` paths using horizontal cubic Bézier curves:
  $$\text{Curve}(x_1, y_1, x_2, y_2) = M(x_1, y_1) \to C\left(\frac{x_1 + x_2}{2}, y_1,\; \frac{x_1 + x_2}{2}, y_2,\; x_2, y_2\right)$$
- **View Transforms**: Uses hardware-accelerated SVG matrix transforms (`translate(x, y) scale(k)`) with pointer event management and threshold-based drag detection to distinguish panning from clicks.
- **Glassmorphism UI**: CSS backdrop-filter blur, CSS color-mix, CSS custom properties, and dark mode palette.

---

## 🤝 Contributing

Contributions to expand domains, add modern specializations, or refine descriptions are welcome!

1. Fork the repository.
2. Edit `index.html` to update the `DATA` or `LENS` object.
3. Test your changes locally by opening `index.html` in your browser.
4. Submit a Pull Request describing your additions or improvements.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
