# Honeypot Threat Intelligence & SIEM Pipeline

## Threat Intelligence Findings (24-Hour Capture)
*(Note: The honeypot is currently active and gathering telemetry. This section will be updated with final OpenSearch visualizations and data points upon completion of the 24-hour capture window).*

### 1. The Threat Landscape (Origins & Credential Stuffing)
* **Top Attacking ASNs:** [Placeholder for Pie Chart showing origin infrastructure - e.g., DigitalOcean, Tencent, etc.]
* **Credential Combinations:** [Placeholder for Data Table showing top 10 Username/Password combinations attempted, demonstrating reliance on default IoT credentials].

### 2. Post-Exploitation Tactics (MITRE ATT&CK)
* **Command & Scripting Interpreter (T1059):** [Placeholder for Word Cloud/Bar Chart of executed commands]. Observations on how automated scripts footprint the fake environment (e.g., `uname -a`, `nproc`, file system enumerations).
* **Indicator Removal on Host (T1070):** Observations of bots attempting to alter `/tmp/` directories to kill competing crypto-mining software.

### 3. Payload Delivery Analysis
Captured dropped payloads targeting the fake file system.
* **SHA-256 Hashes:** * [Placeholder Hash 1] -> [Link to VirusTotal Analysis]
  * [Placeholder Hash 2] -> [Link to VirusTotal Analysis]

---

## Repository Structure
*To maintain operational security, exact IP addresses, Tailnet keys, and SSH keys have been sanitized from these configuration files.*

* `/infrastructure`: Contains the `docker-compose.yml` used to deploy the Cowrie container and establish the volume mappings.
* `/siem-rules`: Contains the custom `local_rules.xml` engineered for the Wazuh Manager. These rules natively parse Cowrie JSON output, establish dynamic alerting levels, and map the activity to MITRE ATT&CK vectors.
* `/dashboards`: Contains the raw JSON exports of the OpenSearch custom threat intelligence dashboards for easy replication.

---

## Conclusion & Learnings
* **Security by obscurity is dead:** Automated scanners map and attack exposed IPv4 ports within minutes of deployment.
* **Infrastructure as Code (IaC):** Containerizing the sensor array allows for the rapid, disposable deployment of high-fidelity threat intelligence gathering nodes.
* **Actionable SIEM Engineering:** Collecting raw logs is insufficient without custom decoders to extract fields (`data.shasum`, `data.input`) and turn raw data into structured intelligence.
