# Monitoring-System-Using-Prometheus-and-BlackBox
This project monitors the uptime and response time of a website using Prometheus and Blackbox Exporter. It visualizes the data in Grafana and sends real-time alerts to Slack via Alertmanager when the website is down.
**This project monitors the uptime and response time of a website using Prometheus and Blackbox Exporter. It visualizes the data in Grafana and sends real-time alerts to Slack via Alertmanager when the website is down.**

## **Architecture Diagram**

Website → Blackbox Exporter → Prometheus → Alertmanager → Slack & Grafana Dashboard

## **Components Used**

| Component | Purpose |
| --- | --- |
| Prometheus | Collects metrics from Blackbox Exporter |
| Blackbox Exporter | Probes the website endpoint for uptime & latency |
| Grafana | Visualizes metrics with dashboards |
| Alertmanager | Sends alerts based on Prometheus alert rules |
| Slack Webhook | Receives notifications for alerts |

## Setup and Installation

### Prerequisites

- Docker and Docker Compose installed
- Slack Workspace & Incoming Webhook URL

### Steps

1. Clone the repository or copy files: `docker-compose.yml`, `prometheus.yml`, `alerts.yml`, `alertmanager.yml`.
2. Configure Slack webhook URL in `alertmanager.yml`.
3. Run `docker-compose up` to start all services.
4. Access:
    - Prometheus: `http://localhost:9090`
    - Grafana: `http://localhost:3000` (default login: admin/admin)
    - Alertmanager: `http://localhost:9093`
5. probe_success   (This will show `1` if the website is up, `0` if it's down.
6. probe_duration_seconds   This shows how long (in seconds) it takes to get a response from the website.

## Configuration Details

### prometheus.yml

- Defines scrape configs to collect metrics from Blackbox Exporter.
- Loads alert rules from `alerts.yml`.
- Sets alertmanager endpoint.

### alerts.yml

- Contains alerting rules, e.g., if `probe_success` equals 0 for 30 seconds, fire alert `WebsiteDown`.

### alertmanager.yml

- Configures Alertmanager to send alerts to the Slack via the webhook URL.

### docker-compose.yml

- Defines all the containers and mounts required configuration files.

## Usage

- Monitor website uptime and response time on Grafana dashboards.
- Receive Slack notifications instantly when the site is down.

## 

[http://host.docker.internal:9090](http://host.docker.internal:9090/)
