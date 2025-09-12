# LibreNMS + Grafana Integration and Centralized Logging

A concise plan to integrate Grafana with LibreNMS for visualization and to determine a centralized logging approach.

## Table of Contents
- Objectives
- Compose Files
- Grafana + LibreNMS: Integration Options
- Centralized Logging Options
- Decision Criteria
- Status
- Next Steps
- Glossary

## Objectives
- Visualize LibreNMS device and network metrics in Grafana
- Establish a scalable, centralized logging solution

## Compose Files
- [libre-lgtm.yaml](./libre-lgtm.yaml) — Docker Compose for LibreNMS with the full LGTM stack (Loki, Grafana, Tempo, Mimir).
- [libre-prom.yaml](./libre-prom.yaml) — Docker Compose for a LibreNMS -> Prometheus -> Grafana stack.
- [rrdrest-compose.yaml](./rrdrest-compose.yaml) — Docker Compose for a LibreNMS -> RRDReST -> Grafana stack.

## Grafana + LibreNMS: Integration Options
1) RRDReST API
- Grafana queries LibreNMS via RRDReST to retrieve time-series data

2) Prometheus
- Grafana queries Prometheus, which collects metrics exposed by LibreNMS

## Centralized Logging Options
1) LGTM Stack with LibreNMS
- Run LGTM alongside LibreNMS and export LibreNMS metrics to Mimir

2) LGTM Stack Only
- Replace LibreNMS and rely solely on the LGTM stack

## Decision Criteria
- Effort and complexity to implement and maintain
- Performance and scalability (horizontal scaling where possible)
- Operational simplicity and ecosystem alignment
- Cost (infrastructure and operational overhead)
- Time to value and community support

## Status
- Current decision: TBD

## Next Steps
- [ ] Choose Grafana data source approach (RRDReST vs Prometheus)
- [ ] Choose centralized logging approach (LGTM with LibreNMS vs LGTM-only)
- [ ] Prototype selected path(s) in a sandbox
- [ ] Document deployment/runbooks
- [ ] Build initial Grafana dashboards

## Glossary
- LGTM = Loki, Grafana, Tempo, Mimir
- Loki = Log aggregation system
- Grafana = Data visualization tool
- Tempo = Distributed tracing system
- Mimir = Metrics aggregation system (Prometheus format/compatible, but horizontally scalable)