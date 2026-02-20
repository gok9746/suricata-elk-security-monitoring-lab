# Suricata + ELK Security Monitoring Lab (SIEM Pipeline)

A hands-on SOC-style lab that builds an end-to-end security monitoring pipeline using:

- **Suricata** (IDS/IPS) for network threat detection  
- **Filebeat** for log shipping  
- **Logstash** for parsing/forwarding  
- **Elasticsearch** for indexing/storage  
- **Kibana** for dashboards and investigation

## Architecture

**Traffic / Attacks → Suricata (eve.json) → Filebeat → Logstash → Elasticsearch → Kibana**

See: `docs/architecture.md`

## What this project demonstrates (Recruiter-focused)

- IDS deployment + alert generation (**Suricata**)
- SIEM-style log pipeline design (**Beats → Logstash → Elasticsearch**)
- Security event investigation with dashboards (**Kibana**)
- Practical attack simulations (port scans / web attacks) and detection validation

## Repository Contents

- `config/suricata.yaml` — Suricata configuration  
- `config/rules/local.rules` — custom/local detection rules  
- `config/filebeat.yml` — Filebeat input + output configuration  
- `config/logstash.conf` — Logstash pipeline config  
- `docs/architecture.md` — architecture notes  
- `screenshots/` — evidence (services running, alerts, dashboards)

> Note: Large upstream Suricata rulesets are intentionally **not committed** to avoid GitHub secret-scanner false positives.
> This repo focuses on configuration, pipeline setup, and custom rules.

## Lab Evidence (Screenshots)

### Docker / Containers
**Container(s) running**
![Containers Running](screenshots/container_running.png)

**Docker status**
![Docker Status](screenshots/docker_status.png)

### ELK + Logstash Pipeline
**Logstash pipeline config**
![Logstash 1](screenshots/logstash_1.png)
![Logstash 2](screenshots/logstash_2.png)
![Logstash 3](screenshots/logstash_3.png)

### Suricata + Filebeat Services
**Suricata service status**
![Suricata Status](screenshots/suricata_status.png)

**Filebeat service status**
![Filebeat Status](screenshots/filebeat.png)
![Filebeat Status 2](screenshots/filebeat%202.png)

### Kibana Visualization
**Kibana showing visualized logs**
![Kibana Visualization](screenshots/kibana_visualized.png)

### Attack Simulation Proof
**Nmap activity**
![Nmap](screenshots/nmap.png)

**SQL Injection activity**
![SQL Injection](screenshots/sql_injection.png)

**XSS activity**
![XSS](screenshots/xss.png)

### Target Application
**OWASP Juice Shop running**
![Juice Shop](screenshots/juiceshop.png)

## How to run (high level)

## Setup (high level)

### 1) Start ELK (Docker)
```bash
docker compose up -d
docker ps
##start suricata

sudo systemctl start suricata
sudo systemctl status suricata --no-pager

##start filebeat
sudo systemctl start filebeat
sudo systemctl status filebeat --no-pager
