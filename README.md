# Raspberry Pi Monitoring with Grafana Cloud & Alloy

An observability project designed to explore the various visuals in Grafana and see what they can offer for home lab monitoring. This dashboard was built as a personal experiment to explore modern observability patterns using **Grafana Alloy** and **Grafana Cloud**.

<p align="center">
  <img width="810" height="1046" alt="Raspberry Pi-1766836571386" src="https://github.com/user-attachments/assets/71b48461-840a-4b1e-b91d-462d32319e12" />
</p>
*A look at the various visualization options used to monitor system health.*

## 🚀 Key Visualizations
This dashboard utilizes several different Grafana panel types to represent system data:

* **Hardware Health (Stat & Bar Gauge)**: Real-time tracking of CPU temperature with orange/red warning thresholds at 60°C and 80°C.
* **Docker Observability (Time Series)**: Stacked views of CPU and Memory utilization per container, along with active container counts.
* **System Uptime (Bar Gauge)**: A visual representation of how long specific containers have been running without restarts (still needs more work).
* **Storage & Network (Bar Gauge & Time Series)**: Visualizing disk space usage on the root partition and live network traffic throughput for `eth0`.
* **Live Error Stream (Logs)**: A dedicated logs panel that streams critical errors and alerts directly from the system.

## 🛠️ Prerequisites
To replicate this setup, you will need:
1. **Grafana Cloud Account**: Used to host the dashboard and store metrics.
2. **Grafana Alloy**: Installed on your Raspberry Pi to collect and "Remote Write" metrics.
3. **Prometheus & Loki**: Configured as data sources in your Grafana instance.

## 📥 Installation
1. **Download** the `dashboard.json` file from this repository.
2. In your Grafana instance, go to **Dashboards** > **New** > **Import**.
3. **Upload** the JSON file.
4. When prompted, select your **Prometheus** and **Loki** data sources to map the required template variables.

## 📊 Technical Details
* **Collection**: Designed to work with `node_exporter` and `cadvisor` modules within Grafana Alloy.
* **Language**: Built using **PromQL** for hardware metrics and **LogQL** for the error stream.
* **Alerting**: Includes logic for thermal monitoring using `max(node_hwmon_temp_celsius)`.

## 🤝 Community & Background
This project was shared on LinkedIn as a "learning in public" update, where it reached over **9,000 impressions** and sparked engagement from the **Grafana Labs** team. 

<img width="555" height="310" alt="Grafana_comment" src="https://github.com/user-attachments/assets/cbc6d5a3-c049-408a-a43b-90eb8ceee82f" />

It serves as a proof-of-concept for how visualizing local hardware can bridge the gap between abstract metrics and physical reality.
