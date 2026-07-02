# draw.io Design Specification — Product Architecture Context

- File name: product-architecture-context.drawio
- Source context: docs/03-Product-Requirements/product-requirements.md

## Purpose
Provide a professional architecture overview of the EduSync product context, showing how users, client applications, the API layer, domain modules, and platform services interact.

## Components
- Client layer
  - Users
  - React web app
  - React Native mobile app
- Application layer
  - Spring Boot REST API
  - Authentication and authorization
  - Domain modules
    - School
    - Student
    - Teacher
    - Guardian
    - Attendance
    - Homework
    - Examination
    - Fees
    - Payments
    - Reports
    - Dashboard
    - Notification
    - Subscription
- Platform services
  - PostgreSQL
  - Redis
  - RabbitMQ
  - AWS S3
  - SMS, WhatsApp, Email, payment providers

## Layout
- Use a three-column canvas:
  1. Client layer on the left
  2. API and domain services in the center
  3. Data, messaging, storage, and external providers on the right
- Group domain modules inside a single container labeled Domain Modules.
- Keep the API at the center of the diagram with clear directional lines to each platform capability.

## Connections
- Users -> web app and mobile app.
- Web app and mobile app -> REST API.
- REST API -> authentication and authorization.
- REST API -> domain modules.
- Domain modules -> PostgreSQL, Redis, RabbitMQ, AWS S3.
- RabbitMQ -> external communication and payment providers.
- Keep relationships explicit and avoid overly dense cross-links.

## Color Recommendations
- Users and clients: light blue (#BFDBFE)
- API and application services: blue (#2563EB)
- Domain modules: orange (#F59E0B)
- Data layer: purple (#7C3AED)
- External integrations: amber (#D97706)
- Background: white or very light gray (#F8FAFC)

## Swimlanes
- Recommended swimlanes: Client Layer, Application Layer, Platform & Integration Layer
- Use container backgrounds to visually separate each lane.
