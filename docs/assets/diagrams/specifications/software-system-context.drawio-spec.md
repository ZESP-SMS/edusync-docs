# draw.io Design Specification — Software System Context

- File name: software-system-context.drawio
- Source context: docs/04-Software-Requirements/software-requirements.md

## Purpose
Capture the full software system context for EduSync, including clients, edge services, application APIs, core platform services, messaging, storage, external integrations, and observability.

## Components
- Client entry points
  - Web browser
  - Mobile device
- Edge and experience layer
  - React web application
  - React Native Expo application
  - Nginx
- Core application layer
  - Spring Boot REST API
  - Spring Security
  - Domain modules
- Data and platform services
  - PostgreSQL
  - Redis
  - RabbitMQ
  - AWS S3
- Integration and operations
  - Notification workers
  - SMS provider
  - WhatsApp provider
  - Email provider
  - Payment gateway
  - Centralized logs
  - Metrics
  - Distributed traces
  - Alerts

## Layout
- Use a left-to-right, layered layout.
- Place users and clients on the far left.
- Place edge and web/mobile application nodes in the middle-left.
- Place the API and domain modules in the center.
- Place databases, queues, storage, and external integrations on the right.
- Place observability and alerting at the far right as a support layer.

## Connections
- Browser and mobile -> web/mobile apps -> Nginx -> REST API.
- REST API -> Spring Security and domain modules.
- REST API -> PostgreSQL, Redis, RabbitMQ, AWS S3.
- RabbitMQ -> notification workers -> SMS, WhatsApp, Email providers.
- REST API -> payment gateway.
- REST API -> logs, metrics, traces.
- Metrics -> alerts.

## Color Recommendations
- Client layer: light blue (#DBEAFE)
- Edge and app layer: blue (#2563EB)
- Core platform layer: teal (#0F766E)
- Data and messaging: purple (#7C3AED)
- External providers: orange (#F59E0B)
- Observability: green (#16A34A)
- Background: white or pale gray (#F9FAFB)

## Swimlanes
- Recommended swimlanes: Client, Edge & Experience, Core Platform, Data & Integrations, Operations
- The operations swimlane should be visually separated from the business transaction flow.
