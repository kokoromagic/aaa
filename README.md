# WebPulse Benchmark Engine

WebPulse is an automated infrastructure testing tool designed to measure web page responsiveness and latency under various network configurations. By leveraging headless browser automation and secure tunnel routing, WebPulse provides high-fidelity performance metrics for external domains.

## Overview
WebPulse automates the process of spinning up isolated testing environments in the cloud. It is primarily used to evaluate how specific web domains behave when accessed through different proxy infrastructures or restrictive network conditions.

## Key Features
- **Headless Browser Execution:** Utilizes optimized Playwright instances for fast, consistent rendering.
- **Dynamic Proxy Routing:** Configurable proxy support to simulate global traffic patterns.
- **Tunnel Security:** Integrates `cloudflared` to ensure testing traffic is routed through encrypted, secure tunnels.
- **Infrastructure-as-Code:** Fully compatible with GitHub Actions for automated, scheduled benchmarking.

## Setup Requirements
To use WebPulse in your CI/CD pipeline, ensure the following secrets are configured in your repository:

| Secret Name | Description |
| :--- | :--- |
| `REPO` | The target repository containing the core logic scripts. |
| `ACCESS_TOKEN` | GitHub PAT with read/write access to the target repository. |
| `WEB_PASSWORD` | Secure authentication key for the internal benchmarking engine. |

## Quick Start (GitHub Actions)
You can trigger a benchmark test manually through the GitHub Actions tab by selecting the `Run test on playwright` workflow.

### Input Parameters
- `test_domain`: The target URL you wish to benchmark (e.g., `example.com`).
- `proxy_server`: Optional IP:PORT of the proxy server to route traffic through.
- `time_runner`: Maximum execution timeout (in seconds) to prevent infinite loops.

## Deployment Note
This repository acts as the **Orchestration Layer**. The actual execution logic is pulled dynamically from the secure private repository specified in your secrets. Ensure that your environment has sufficient resource allocation for Chromium-based rendering tasks.

---
*Disclaimer: This tool is intended for performance testing and infrastructure benchmarking only. Please ensure you have permission to perform load/latency tests on the target domain.*
