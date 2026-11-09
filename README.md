# Awesome-Systems-Administration-Management

# Awesome Systems Administration & Management

> A curated list of top Systems Administration and Management platforms — both SaaS/Hosted commercial solutions and open-source alternatives for endpoint management, remote monitoring, and infrastructure administration.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Microsoft Intune](#microsoft-intune)
  - [ManageEngine Endpoint Central](#manageengine-endpoint-central)
  - [NinjaOne](#ninjaone)
  - [Atera](#atera)
  - [Kaseya VSA](#kaseya-vsa)
  - [Jamf Pro](#jamf-pro)
  - [JumpCloud](#jumpcloud)
  - [SolarWinds Server & Application Monitor](#solarwinds-server--application-monitor)
- [Open-Source Software](#-open-source-software)
  - [Tactical RMM](#tactical-rmm)
  - [OpenRMM](#openrmm)
  - [Fleet](#fleet)
  - [NetLock RMM](#netlock-rmm)
  - [Zabbix](#zabbix)
  - [Ansible](#ansible)
  - [Snipe-IT](#snipe-it)
  - [Checkmate](#checkmate)
  - [Glouton](#glouton)
  - [Cairn-MDM](#cairn-mdm)
  - [MDMesh](#mdmesh)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Systems Administration and Management platforms. These are not open-source but are included as reference points for feature comparison.

### Microsoft Intune
**Type:** Cloud-based endpoint and mobile device management  
Microsoft Intune provides unified endpoint management for Windows, macOS, iOS, Android, and Linux, integrated with Microsoft Entra ID and the broader Microsoft 365 ecosystem. It handles device enrollment, configuration profiles, compliance policies, app deployment, and conditional access. Pricing is per-user and typically bundled with Microsoft 365 E3/E5 plans.

### ManageEngine Endpoint Central
**Type:** Unified endpoint management and security  
Endpoint Central (formerly Desktop Central) provides patch management, software deployment, asset inventory, remote control, and configuration management across Windows, macOS, and Linux. It is available as both cloud and on-premises, with pricing per endpoint. Suited for mid-market organizations wanting comprehensive UEM without Microsoft 365 lock-in.

### NinjaOne
**Type:** Unified IT operations and RMM platform  
NinjaOne combines remote monitoring and management (RMM), endpoint management, patch management, remote access, backup, and mobile device management for enterprise IT teams and MSPs [citation:12]. It is known for a modern interface and fast agent deployment. Pricing is per-device with tiered plans.

### Atera
**Type:** RMM and PSA for MSPs and IT teams  
Atera combines RMM, PSA, and remote access in a single platform with per-technician pricing rather than per-device. It includes automation, patch management, and helpdesk ticketing. Suited for MSPs and internal IT teams wanting predictable per-staff costs.

### Kaseya VSA
**Type:** Enterprise RMM and endpoint management  
Kaseya VSA provides remote monitoring and management, patch management, automation, and endpoint security for MSPs and enterprise IT. It is a long-standing platform with a broad feature set, though pricing and complexity typically target larger MSPs.

### Jamf Pro
**Type:** Apple-focused MDM and endpoint management  
Jamf Pro is the enterprise standard for Apple device management, covering macOS, iOS, iPadOS, and tvOS. It provides zero-touch deployment, configuration profiles, app management, and compliance enforcement. Suited for organizations with significant Apple fleets requiring deep Apple-specific management.

### JumpCloud
**Type:** Cloud directory with device management  
JumpCloud combines cloud directory, SSO, MFA, LDAP/RADIUS, and cross-OS device management (Windows, macOS, Linux) in a single console. It is a common replacement for on-premises Active Directory in small and mid-sized companies.

### SolarWinds Server & Application Monitor
**Type:** Infrastructure monitoring and application performance  
SolarWinds SAM provides server and application monitoring with agentless and agent-based collection, dependency mapping, and alerting. It is part of the broader SolarWinds IT management portfolio, suited for organizations wanting deep infrastructure visibility with a commercial support model.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Systems Administration and Management tools. The open-source ecosystem spans **RMM platforms**, **endpoint management**, **configuration management**, **infrastructure monitoring**, and **asset tracking**.

### Tactical RMM
**Stack:** Python / Django / Go / MeshCentral | **License:** Open Source (per project)  
Tactical RMM is an open-source remote monitoring and management platform built on Django and MeshCentral, designed for MSPs and IT teams managing Windows, Linux, and macOS endpoints [citation:1]. Features include agent-based endpoint onboarding, remote command execution, scripting, patch management, and alerting. The deployment lab documentation covers practical setup on Debian 12, Windows endpoint onboarding, and troubleshooting findings, including a known limitation where Linux/macOS agent generation requires a code-signing token that may block deployment even after configuring the Global Key Store [citation:1]. **Trade-off:** The Linux/macOS agent signing workflow can be a deployment blocker; Windows endpoints are the primary tested path.  
**Best for:** IT teams and MSPs wanting a self-hosted RMM with Windows-first endpoint management, accepting that Linux/macOS agent deployment may require additional signing configuration.

### OpenRMM
**Stack:** Go / React / PostgreSQL | **License:** Open Source (per project)  
OpenRMM is a self-hosted RMM with a native AI assistant, a Go agent, pluggable remote access, and an MCP server with human approval for every action [citation:2]. Security features include built-in admin/tech/readonly roles, TOTP 2FA, SSO via OpenID Connect, per-user access scoping (Company/Site/Department/device) enforced across read, write, remote access, and the AI/MCP surface. The MCP server connects external AI (Claude, ChatGPT) to manage the fleet with the same permission-filtered tools and human-approval guardrails. Deploys via Docker Compose with published images from `ghcr.io/openrmm-project` [citation:2]. **Trade-off:** Newer project; evaluate maturity and community size before production deployment.  
**Best for:** Teams wanting a modern, AI-integrated RMM with strong access control and MCP-based AI agent management.

### Fleet
**Stack:** Go / osquery / nanoMDM | **License:** MIT (free version)  
Fleet is an open-source device management platform built on osquery, nanoMDM, Nudge, and swiftDialog, designed for IT and security teams managing thousands of computers [citation:3]. It provides MDM, patch management, software deployment, and compliance verification across Linux, macOS, Windows, Chromebooks, iOS, and Android. Fleet emphasizes API-first design with GitOps, webhooks, YAML, and `fleetctl` CLI, plus CIS benchmarks for macOS and Windows. The free version is MIT-licensed and used in production by organizations managing 400,000+ hosts [citation:3].  
**Best for:** IT and security teams wanting a lightweight, API-driven device management platform with strong Linux support and osquery-based visibility.

### NetLock RMM
**Stack:** C# / ASP.NET Core / Blazor / MySQL | **License:** Open Core (Community up to 25 devices)  
NetLock RMM is an open-core RMM from Germany with a Community Edition (self-hosted, up to 25 devices) and paid Self-Hosted editions with unlimited devices and SLA support [citation:8]. Features include 53 pre-built report templates, a visual query builder, per-user custom dashboards, an append-only audit log, event notifications via Email/Teams/ntfy/Telegram/webhooks, an integrated file server for scripts, a device world map with offline GeoIP, white-label branding, and **code-signed Windows agents and installers in every edition including Community** [citation:8]. Security includes agent handshake, supply-chain hash verification, RAM-based encrypted package delivery, and outbound-only agents.  
**Best for:** Small teams and homelabs wanting a feature-rich, code-signed RMM with a free tier up to 25 devices, or MSPs wanting a white-labelable open-core platform.

### Zabbix
**Stack:** C / PHP / MySQL/PostgreSQL | **License:** GPL-2.0  
Zabbix is an all-in-one, enterprise-grade open-source monitoring solution providing data collection, storage, a web UI, and flexible alerting [citation:9]. Its architecture is a traditional server-agent model, with strong native support for agentless monitoring via SNMP, JMX, and IPMI, making it a favorite for network and hardware monitoring. Zabbix proxies distribute load in large environments. It stores data in a relational database, separating raw History from hourly Trends for long-term storage [citation:9].  
**Best for:** Organizations needing broad, multi-protocol infrastructure monitoring (network, hardware, servers) with a proven, centralized platform.

### Ansible
**Stack:** Python / YAML | **License:** GPL-3.0 (core)  
Ansible is an agentless automation platform using YAML-based playbooks to configure systems, deploy software, and orchestrate workflows [citation:5]. It is the most widely adopted configuration management tool, with no agent required on managed nodes (SSH-based). Ansible supports cloud provisioning, network automation, and application deployment. Red Hat offers a commercially supported Ansible Automation Platform for enterprises requiring lifecycle support [citation:5].  
**Best for:** Teams wanting agentless configuration management and automation with the largest community and ecosystem in the space.

### Snipe-IT
**Stack:** PHP / MySQL | **License:** AGPL-3.0  
Snipe-IT is an open-source IT asset management solution for tracking hardware, software licenses, and accessories [citation:7]. It provides asset checkout/checkin, license seat management, depreciation tracking, and reporting. Deployable on standard LAMP hosting. Suited for organizations needing a lightweight, self-hosted alternative to commercial asset management platforms.  
**Best for:** IT teams wanting a free, self-hosted asset management system for tracking hardware and software inventory.

### Checkmate
**Stack:** Node.js / MongoDB | **License:** Open Source  
Checkmate is an open-source self-hosted monitoring tool that tracks server and infrastructure uptime, response times, and hardware status [citation:14]. It supports monitoring Docker containers, including remote Docker daemons with TLS authentication, and provides a dashboard for visualizing infrastructure health. Deployable via Docker Compose.  
**Best for:** Teams wanting a lightweight, self-hosted uptime and infrastructure monitoring dashboard, particularly for Docker-centric environments.

### Glouton
**Stack:** Go | **License:** Open Source (per Go package)  
Glouton is a lightweight infrastructure monitoring agent (~100 MB RAM, 3-5% of a single core) that auto-discovers running services and collects metrics from containers, applications, logs, and hardware [citation:4]. It includes an embedded Prometheus-compatible TSDB with 15-day default retention, a local panel at `localhost:8015`, and can forward to Bleemeo Cloud or MQTT brokers. It supports Docker, Kubernetes, SNMP, SMART, IPMI, and NVIDIA monitoring. **Important:** Glouton is an agent, not a full monitoring platform; it serves a Prometheus endpoint and provides a local UI for single-host visibility [citation:4].  
**Best for:** Homelabs and small deployments wanting a single-binary monitoring agent with a local dashboard and Prometheus compatibility, without deploying a full monitoring stack.

### Cairn-MDM
**Stack:** Go / SQLite | **License:** MIT  
Cairn-MDM is a single-binary open-source Apple MDM server for homelabbers, small businesses, and non-profits, managing macOS and iOS/iPadOS devices with over-the-air enrollment, an embedded SCEP certificate authority, and a web console [citation:6]. It embeds the MDM protocol server (NanoMDM), an optional SCEP CA, and the admin UI into one process with one config file and SQLite by default. **The non-ABM path is first-class: no Apple Business Manager account required** [citation:6]. **Status:** Public beta (v0.x); Declarative Device Management and ABM/ADE are on the roadmap but not yet implemented.  
**Best for:** Small Apple fleets and homelabs wanting a single-binary, MIT-licensed MDM without the complexity of a multi-service stack or Apple Business Manager requirement.

### MDMesh
**Stack:** Java / React / Kotlin / PostgreSQL | **License:** Open Source  
MDMesh is a modern, self-hosted Android MDM forked from Headwind MDM, rebuilt as a distinct product with a Java control plane, React admin console, Kotlin device agent, and signed auto-updates [citation:11]. Features include QR-code Device-Owner enrollment, kiosk/COSU mode with exit PIN, app delivery (APK upload, F-Droid, silent install/upgrade), location tracking with Leaflet map, remote actions (lock, wipe, reboot), and signed auto-updates with rollback. **No paywalled enterprise edition** — kiosk, app delivery, and signed updates are in the open-source core [citation:11].  
**Best for:** Organizations managing Android device fleets (kiosks, field devices, BYOD) wanting a modern, fully open-source MDM without feature gating.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Endpoint Mgmt | Monitoring | Self-Hosted | Best For |
|----------|---------|-------|---------------|------------|-------------|----------|
| **Microsoft Intune** | Proprietary | Cloud | ✅ | (Limited) | ❌ | Microsoft 365 endpoint management |
| **NinjaOne** | Proprietary | Cloud | ✅ | ✅ | ❌ | Unified IT operations + RMM |
| **Kaseya VSA** | Proprietary | Cloud/on-prem | ✅ | ✅ | (on-prem) | Enterprise MSP RMM |
| **Jamf Pro** | Proprietary | Cloud/on-prem | ✅ (Apple) | (Limited) | (on-prem) | Apple device management |
| **Tactical RMM** | Open Source | Python/Django/Go | ✅ (Windows-first) | ✅ | ✅ | Self-hosted Windows RMM |
| **OpenRMM** | Open Source | Go/React/Postgres | ✅ | ✅ | ✅ | AI-integrated RMM + MCP |
| **Fleet** | MIT | Go/osquery | ✅ (MDM) | ✅ | ✅ | API-driven device management |
| **NetLock RMM** | Open Core | C#/ASP.NET/MySQL | ✅ | ✅ | ✅ | Code-signed RMM (25 free) |
| **Zabbix** | GPL-2.0 | C/PHP/DB | ❌ | ✅ Deep | ✅ | Multi-protocol monitoring |
| **Ansible** | GPL-3.0 | Python/YAML | ❌ (Config) | ❌ | ✅ | Agentless automation |
| **Snipe-IT** | AGPL-3.0 | PHP/MySQL | (Assets) | ❌ | ✅ | IT asset tracking |
| **Cairn-MDM** | MIT | Go/SQLite | ✅ (Apple) | ❌ | ✅ | Single-binary Apple MDM |
| **MDMesh** | Open Source | Java/React/Kotlin | ✅ (Android) | (Location) | ✅ | Fully open Android MDM |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Systems Administration or Management tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source (or clearly note if it is open-core). Note that the open-source ecosystem **splits** between RMM platforms (Tactical RMM, OpenRMM, NetLock RMM), device management/MDM (Fleet, Cairn-MDM, MDMesh), infrastructure monitoring (Zabbix, Glouton, Checkmate), configuration automation (Ansible), and asset tracking (Snipe-IT). No single open-source tool replicates the full breadth of Microsoft Intune or NinjaOne, but combinations of Fleet (MDM), Zabbix (monitoring), and Ansible (configuration) can cover most systems administration needs.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
