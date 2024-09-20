# Building a SOC and Honeynet in Microsoft Azure with Live Traffic Monitoring

![Cloud Honeynet / SOC](https://i.imgur.com/MN97uFU.png)

## Executive Summary

This repository documents the process of establishing a miniature honeynet within the Azure platform. The initiative aims to aggregate and analyze log data to construct attack narratives and monitor network vulnerabilities. Utilizing Microsoft Sentinel, the project highlights the effectiveness of deploying and later enhancing security measures within cloud environments.

## Initial Architecture & Security Landscape

The initial setup of our Azure honeynet infrastructure is outlined below. This configuration details the absence of significant security barriers and publicly exposed endpoints, rendering the environment susceptible to potential compromise.

![Initial Architecture Diagram](https://i.imgur.com/aBDwnKb.jpg)

### Components

- **Virtual Network (VNet)**
- **Network Security Group (NSG)**
- **Virtual Machine Instances**: Includes 2 Windows and 1 Linux VM.
- **Log Analytics Workspace**
- **Azure Key Vault**
- **Azure Storage Account**
- **Microsoft Sentinel**

### Initial Findings

Before the implementation of security controls, data was collected from the environment for a 24-hour benchmarking interval, facilitating a clearer understanding of the unsecured network state.

## Enhanced Security Architecture

Following the application of meticulous hardening practices, the architecture was significantly reinforced, as depicted below. Enhancements included network traffic filtering, deployment of private endpoints, and stringent access control.

![Enhanced Architecture Diagram](https://i.imgur.com/YQNa9Pp.jpg)

## Preliminary Attack Narratives & Metrics

Prior to security control implementation, the generated attack maps and metrics provide empirical evidence of the network's vulnerability.

![NSG Allowed Inbound Malicious Flows](https://i.imgur.com/1qvswSX.png)
![Linux Syslog Auth Failures](https://i.imgur.com/G1YgZt6.png)
![Windows RDP/SMB Auth Failures](https://i.imgur.com/ESr9Dlv.png)

### Benchmark Metrics (Pre-Hardening)

| Metric                   | Count  |
|--------------------------|--------|
| SecurityEvent            | 19,470 |
| Syslog                   | 3,028  |
| SecurityAlert            | 10     |
| SecurityIncident         | 348    |
| AzureNetworkAnalytics_CL | 843    |

*Data Collection Interval: 2024-03-15 17:04:29 to 2024-03-16 17:04:29*

## Post-Hardening Observations

Following the security enhancement process, no malicious activity was detected through the same attack map diagnostics leveraged initially.

### Reinforced Metrics (Post-Hardening)

| Metric                   | Count |
|--------------------------|-------|
| SecurityEvent            | 8,778 |
| Syslog                   | 25    |
| SecurityAlert            | 0     |
| SecurityIncident         | 0     |
| AzureNetworkAnalytics_CL | 0     |

*Data Collection Interval: 2024-03-18 15:37 to 2024-03-19 15:37*

## Conclusive Insight

The post-analysis of the environment, enhanced with robust security controls, yielded a marked reduction in the recorded events and incidents. The stringent application of the security measures underscores their significance in mitigating network vulnerabilities and solidifying the defense posture of cloud-based infrastructures.

---

*This project is subject to further iterations and refinements. Viewer discretion is advised as the findings are based on a controlled environment and may not perfectly emulate real-world operational conditions.*
