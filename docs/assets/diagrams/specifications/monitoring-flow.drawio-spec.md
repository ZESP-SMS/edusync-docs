# draw.io Design Specification — Monitoring Flow

- File name: monitoring-flow.drawio
- Source context: docs/04-Software-Requirements/software-requirements.md

## Purpose
Detail the telemetry architecture and data flow of the EduSync platform. This diagram shows how log, metric, and trace telemetry is emitted from applications, databases, caches, queues, and external integrations, aggregated by an observability platform, and translated into dashboards and alerting triggers.

## Components
- **Telemetry Sources**
  - Application (Spring Boot SaaS service)
  - PostgreSQL (Database)
  - Redis (Cache)
  - RabbitMQ (Queue)
  - External Providers (SMS, payment gateways, etc.)
- **Telemetry Buffers / Types**
  - Logs (Standard output/error streams)
  - Metrics (Time-series performance metrics)
  - Traces (Distributed transaction traces)
- **Ingestion & Processing**
  - Observability Platform (Elasticsearch/Logstash/Kibana, Prometheus/Grafana, or OpenTelemetry collector)
- **Output & Consumption**
  - Operational Dashboards
  - Alerts & Escalations

## Layout
- Use a left-to-right flow with 4 distinct horizontal layers:
  1. **Sources (Far Left)**: Staged vertically. Place `Application` at the top center, and database/infrastructure blocks stacked below it.
  2. **Data Types (Middle-Left)**: Three circular or cylindrical shapes labeled `Logs`, `Metrics`, and `Traces` to show the pipeline divisions.
  3. **Processor (Middle-Right)**: A large central container labeled `Observability Platform` with inner components for ingestion, aggregation, and querying.
  4. **Consumers (Far Right)**: Two outputs (`Operational Dashboards` and `Alerts & Escalations`) stacked vertically.
- Keep the connections straight and horizontal where possible to show data flow.

## Connections
- Connect `Application` directly to `Logs`, `Metrics`, and `Traces`.
- Connect `PostgreSQL`, `Redis`, `RabbitMQ`, and `External Providers` directly to `Metrics` (or to custom metric collectors).
- Connect `Logs`, `Metrics`, and `Traces` into the `Observability Platform` container.
- Connect `Observability Platform` to both `Operational Dashboards` and `Alerts & Escalations` on the right.
- Use arrowheads representing the direction of data push/pull (e.g. Prometheus pulling metrics vs. application pushing logs/traces).

## Color Recommendations
- **Telemetry Sources**: Light Blue (#EFF6FF) with Indigo border (#3B82F6)
- **Logs**: Pale Yellow (#FEF3C7) with Gold border (#D97706)
- **Metrics**: Pale Purple (#F3E8FF) with Violet border (#8B5CF6)
- **Traces**: Pale Rose (#FCE7F3) with Pink border (#DB2777)
- **Observability Platform**: Light Teal (#E0F2FE) with Dark Teal border (#0D9488)
- **Outputs / Consumers**: Pale Green (#ECFDF5) with Emerald border (#10B981)
- **Background**: Soft Gray (#F8FAFC)

## Swimlanes
- **Lane 1: Source Layer** (Platform components generating telemetry)
- **Lane 2: Telemetry Pipeline** (Data formatting: logs, metrics, traces)
- **Lane 3: Analytics Engine** (Observability central processor)
- **Lane 4: Action & Visualization Layer** (Dashboards, paging alerts)
