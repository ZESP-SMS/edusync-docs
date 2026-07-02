# draw.io Design Specification — Module Dependency Map

- File name: module-dependency-map.drawio
- Source context: docs/03-Product-Requirements/product-requirements.md

## Purpose
Document the module-level dependencies within the EduSync modular platform. This architecture map defines the compilation and execution dependencies between different modules (such as Authentication, School Core, Academics, Finance, and Reporting) to ensure modular isolation and clean boundaries.

## Components
- **System Core & Identity**
  - Subscription
  - Authentication
  - School
- **Core Entities**
  - Student
  - Teacher
  - Guardian
- **Academic Operations**
  - Attendance
  - Homework
  - Examination
- **Financial Workflows**
  - Fees
  - Payments
- **Reporting & Dashboards**
  - Reports
  - Dashboard
- **Cross-Cutting Utilities**
  - Notification

## Layout
- Use a top-to-bottom layered architecture:
  - **Layer 1: Entry & Access Controls** (Subscription, Authentication)
  - **Layer 2: Core Institution Context** (School, Student, Teacher, Guardian)
  - **Layer 3: Functional Domain Modules** (Attendance, Homework, Examination, Fees, Payments)
  - **Layer 4: Aggregation & Consumption** (Reports, Dashboard, Notification)
- Use rectangular boxes with subtle rounded corners for modules.
- Use explicit grouping borders or backgrounds to mark functional blocks (e.g., Core, Academics, Finance).
- Ensure connectors flow downwards or horizontally to indicate execution paths clearly without overlapping.

## Connections
- Connect `Subscription` to both `Authentication` and `Notification`.
- Connect `Authentication` to `School`.
- Connect `School` to `Student`, `Teacher`, `Attendance`, `Homework`, and `Examination`.
- Connect `Student` to `Guardian`, `Attendance`, `Homework`, `Examination`, and `Fees`.
- Connect `Teacher` to `Attendance`, `Homework`, and `Examination`.
- Connect `Guardian` to `Fees`.
- Connect `Fees` to `Payments`.
- Connect `Attendance`, `Homework`, `Examination`, `Fees`, and `Payments` directly to `Reports`.
- Connect `Reports` to `Dashboard`.
- Connect `Notification` to `Dashboard`.
- Use solid arrows for hard compile-time dependencies, and dashed arrows for soft/event-driven dependencies (like `Notification` and `Subscription`).

## Color Recommendations
- **System Access & Subscription**: Coral (#FEE2E2) with Red border (#EF4444)
- **Core Context (School/People)**: Sky Blue (#E0F2FE) with Blue border (#0284C7)
- **Academics**: Soft Emerald (#D1FAE5) with Green border (#10B981)
- **Finance**: Pale Yellow (#FEF3C7) with Gold border (#D97706)
- **Reporting & Dashboards**: Lavender (#F3E8FF) with Violet border (#8B5CF6)
- **Cross-Cutting (Notification)**: Soft Rose (#FCE7F3) with Pink border (#DB2777)
- **Background**: Ice Gray (#F1F5F9)

## Swimlanes
- **Lane 1: System Access** (Subscription, Auth)
- **Lane 2: Core Directory** (School, Student, Teacher, Guardian)
- **Lane 3: Transactional Modules** (Attendance, Homework, Exams, Fees, Payments)
- **Lane 4: Insights & Event Delivery** (Reports, Dashboard, Notifications)
