# Zabbix Monitoring Stack in Docker

Network monitoring lab: Zabbix 7.0 + PostgreSQL running in Docker Compose.

## What it monitors
- Linux host (CPU, memory, disk, network) via Zabbix agent 2
- External devices via ICMP ping (Google DNS, Cloudflare DNS, unreachable test device)

## Alarms (triggers)
- Custom trigger: CPU > 50% for 1 minute (tested with `yes > /dev/null`)
- Real alarm detected: VM disk over 90% → fixed by expanding the disk

## How to run
1. Create a `.env` file: `DB_PASSWORD=your_password`
2. `docker compose up -d`
3. Open `http://<VM-IP>:8081` (user: Admin)

## What I learned
- Docker Compose: multi-container apps, volumes, ports, container DNS
- Zabbix: hosts, agents, templates, items, triggers, problems
- Agent-based vs agentless (ICMP) monitoring