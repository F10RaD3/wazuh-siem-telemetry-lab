# wazuh-siem-telemetry-lab
# Multi-Platform Endpoint Telemetry & Log Aggregation Pipeline (Wazuh SIEM & Tailscale)

## 📌 Project Overview
This project demonstrates the deployment of an enterprise-grade Open-Source Security Information and Event Management (SIEM) system using **Wazuh**. To simulate modern, decentralized, and hybrid workforce environments, I architected a secure cross-platform logging pipeline across isolated environments utilizing a virtual mesh network (**Tailscale VPN overlay**). 

The central security operations dashboard is hosted on a secure Linux container, actively ingesting and processing cryptographic and system events from a remote Windows 10 endpoint agent.

### 🎯 Core Objectives & Business Case
* **Centralized Telemetry:** Eliminate endpoint blind spots by pooling system and application events into a central correlation hub.
* **Network Isolation & Security:** Avoid exposing listening server ports directly to the public internet by wrapping infrastructure in a private wireguard-based tunnel (Tailscale).
* **Compliance Framework Alignment:** This architecture structurally satisfies the fundamental log collection, system logging, and audit trail requirements mandated by **Section 30 of the Jamaica Data Protection Act (JDPA)** for data security processing.

---

## 🛠️ The Architecture Stack
* **Central SIEM/XDR Dashboard:** Wazuh Server (Hosted inside a Debian-based Crostini Linux Container).
* **Monitored Endpoint:** Windows 10 Home/Pro workstation running the native Wazuh Agent service.
* **Network Overlay:** Tailscale VPN (Providing persistent 100.X.X.X virtual IP routing over any local network or router infrastructure changes).
* **Telemetry Focus:** Windows Event Logs & Sysmon (System Monitor) ingestion pipelines.

---

## 🗺️ Architectural Workflow
1. **The Target:** Windows Endpoint generates standard security event loops (Process creations, account logons, privilege modifications).
2. **The Pipeline:** The local Windows Wazuh Agent captures events and packages them securely.
3. **The Tunnel:** Data passes securely through the encrypted Tailscale mesh tunnel via designated network Port `1514`.
4. **The Collector:** The central Linux Wazuh dashboard parses the telemetry, checks hashes against known threat definitions, and visualizes alerts in real-time.

---

## 📊 Summary of Applied Security Principles (ISC2 CC Alignment)
* **Confidentiality:** Log transmission is encrypted inside an authenticated Tailscale overlay tunnel.
* **Integrity:** System telemetry utilizes File Integrity Monitoring (FIM) to detect unauthorized changes to key system registries or binary files.
* **Availability:** Centralized aggregation ensures logs are structurally retained even if an adversary clears the local Windows Event Viewer logs to hide their footprints.

---

## 📖 Detailed Step-by-Step Playbook
For granular execution scripts, network port configurations, specific router switching strategies, and full verification dashboards, please review the comprehensive playbook hosted on my documentation server:

👉 **[READ THE FULL LAB PLAYBOOK ON GITBOOK](https://cyber-lightcycle.gitbook.io/f10rad3-cyber-lightcyclebase/)**

---
*Developed by a an intuitive Aspriring Cybersecurity Professional*
