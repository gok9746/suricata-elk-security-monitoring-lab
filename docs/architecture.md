# Architecture

Network traffic → Suricata IDS → eve.json logs

Filebeat → forwards logs

Logstash → processes logs

Elasticsearch → stores logs

Kibana → visualizes logs

Security automation script → blocks malicious IPs
