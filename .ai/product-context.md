# EduSync Product Context

> Version: 1.0
>
> Product: EduSync School Management SaaS
>
> Status: Active
>
> Last Updated: July 2026

---

# 1. Purpose

This document is the single source of truth for the EduSync project.

Every AI agent must read this document before generating documentation, designs, architecture, APIs, or code.

If another instruction file conflicts with this document, this document takes precedence unless explicitly updated.

---

# 2. Product Overview

Product Name

EduSync

Category

Cloud-Based Multi-Tenant School Management SaaS

Target Market

India

Future Market

Global

Product Goal

Provide a modern, secure, scalable platform that digitizes school administration and improves collaboration between schools, teachers, students, and parents.

---

# 3. Vision

Build India's most trusted and modern School Management Platform that helps educational institutions manage academics, administration, finance, and communication from one unified platform.

---

# 4. Mission

Simplify school operations through secure, cloud-native software that is easy to use, scalable, and affordable.

---

# 5. Product Principles

EduSync should always be

- Secure
- Simple
- Fast
- Reliable
- Scalable
- Mobile First
- API First
- Cloud Native
- User Friendly

Every design and engineering decision should support these principles.

---

# 6. Target Users

Primary Users

- School Owner
- Principal
- School Administrator
- Accountant
- Teacher
- Parent
- Student

Future Users

- Librarian
- Transport Manager
- Hostel Warden
- HR Manager

---

# 7. School Types

Supported Institutions

- CBSE Schools
- ICSE Schools
- State Board Schools
- Private Schools
- International Schools (Future)
- Coaching Institutes (Future)

---

# 8. Multi-Tenant Model

EduSync is a Multi-Tenant SaaS.

Architecture

- Shared Application
- Shared PostgreSQL Database

Every tenant is identified by

school_id

Rules

- One school's data must never be visible to another school.
- Every tenant-owned table contains school_id.
- All queries must respect tenant isolation.

---

# 9. User Roles

System Roles

- SUPER_ADMIN
- SCHOOL_ADMIN
- ACCOUNTANT
- TEACHER
- PARENT
- STUDENT

Every feature must define which roles have access.

---

# 10. Core Modules (MVP)

Authentication

School Management

User Management

Role & Permission Management

Student Management

Guardian Management

Teacher Management

Academic Year

Classes

Sections

Subjects

Attendance

Fee Structure

Invoices

Payments

Receipts

Dashboard

Reports

Notifications

Audit Logs

---

# 11. Future Modules

Homework

Assignments

Examinations

Transport

Library

Hostel

Payroll

Inventory

Learning Management System (LMS)

AI Assistant

AI Analytics

AI Report Cards

Public API

Marketplace Integrations

---

# 12. Technology Stack

Frontend

- React
- TypeScript
- Vite
- Tailwind CSS

Mobile

- React Native
- Expo

Backend

- Java 21
- Spring Boot
- Spring Security
- Spring Data JPA

Database

- PostgreSQL

Cache

- Redis

Messaging

- RabbitMQ

Storage

- AWS S3

Infrastructure

- Docker
- Docker Compose
- Nginx
- AWS
- GitHub Actions

Documentation

- Markdown
- Mermaid
- MkDocs Material

---

# 13. Non-Functional Goals

Availability

99.9%

Security

OWASP Top 10 compliant

Performance

Average API response under 300 ms

Scalability

Support thousands of schools

Maintainability

Modular architecture

Reliability

Automatic backups and monitoring

---

# 14. Product Workflow

Admission

↓

Student Created

↓

Guardian Linked

↓

Class Assigned

↓

Attendance

↓

Fees

↓

Payments

↓

Reports

This represents the high-level lifecycle of a student within EduSync.

---

# 15. Business Rules

Examples

- Admission Number must be unique within a school.
- A student belongs to one active class at a time.
- A guardian can be linked to multiple students.
- Fee receipts cannot be edited after payment is confirmed.
- Deleted records should be soft deleted where appropriate.

Business rules belong in documentation first, then implementation.

---

# 16. Architecture Principles

Follow

- Clean Architecture
- SOLID Principles
- Domain Driven Design (where appropriate)
- REST API
- Modular Monolith (initially)
- Microservice Ready

Never sacrifice maintainability for short-term speed.

---

# 17. Documentation Standards

All project documentation

- Written in Markdown
- GitHub compatible
- MkDocs compatible
- Version controlled
- Reviewed before implementation

---

# 18. Design Principles

The UI should be

- Simple
- Consistent
- Responsive
- Accessible
- Mobile Friendly

Use a consistent design system across Web and Mobile.

---

# 19. Engineering Principles

Every implementation must be

- Secure
- Tested
- Documented
- Modular
- Observable
- Performant

Never write tutorial-style code.

---

# 20. Team Workflow

Feature Lifecycle

Business Requirement

↓

Product Requirement

↓

UI Design

↓

Database Design

↓

API Design

↓

Backend Development

↓

Frontend Development

↓

Mobile Development

↓

Testing

↓

Code Review

↓

Release

No implementation should begin without approved requirements.

---

# 21. AI Usage Rules

Every AI task must

1. Read this Product Context first.
2. Read the relevant instruction file.
3. Produce output that aligns with the product vision.
4. Avoid introducing conflicting terminology or architecture.
5. Prefer consistency over creativity.

---

# 22. Naming Standards

Use consistent terminology.

Examples

Student

Teacher

Guardian

Attendance

Fee Structure

Invoice

Payment

Academic Year

School

Avoid synonyms that create confusion.

---

# 23. Definition of Success

EduSync succeeds when

- Schools can manage operations digitally.
- Parents stay informed in real time.
- Teachers spend less time on administration.
- Administrators reduce manual work.
- The platform is secure, reliable, and easy to maintain.

---

# 24. Long-Term Vision

EduSync should evolve into a complete education platform with

- AI-powered insights
- Advanced analytics
- Integrated LMS
- Marketplace integrations
- White-label support
- Public APIs
- Enterprise scalability

---

# 25. Final Directive

All documentation, design, architecture, APIs, and code must align with this Product Context.

If new requirements arise, update this document first before updating implementation or documentation.

This document is the authoritative reference for the EduSync project.