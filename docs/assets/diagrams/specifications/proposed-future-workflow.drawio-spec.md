# draw.io Design Specification — Proposed Future Workflow

- File name: proposed-future-workflow.drawio
- Source context: docs/02-Business-Requirements/business-requirements.md

## Purpose
Map the end-to-end operational flow of the proposed future EduSync platform. It demonstrates how tenant setup and master data feed into academic and financial management, leading to real-time dashboards and leadership-driven targeted communication, while feeding audit logs in parallel.

## Components
- **Setup & Master Data**
  - School Tenant Setup
  - Master Data Configuration
  - Student & Guardian Records
  - Teacher & Employee Records
- **Daily Operations**
  - Attendance Management
  - Fee Management
  - Examination Management
  - Homework & Assignments
  - Payments & Reconciliation
- **Insights & Leadership**
  - Dashboards & Reports
  - Principal & Owner Decisions
- **Engagement & Communication**
  - Targeted Communication
  - Parents & Students
  - Teachers & Employees
- **Compliance & Security**
  - Audit Logs

## Layout
- Use a landscape layout with a top-to-bottom and left-to-right flow.
- Organize the components across distinct horizontal swimlanes to maintain clarity of data lineage.
- Position the core operational blocks (Attendance, Fees, Exams, Tasks) centrally to show parallel transaction streams.
- The `Audit Logs` component should be placed in a separate lane at the bottom, receiving feeds from the various operations and communication components.

## Connections
- Connect `School Tenant Setup` to `Master Data Configuration`.
- Connect `Master Data Configuration` to both `Student & Guardian Records` and `Teacher & Employee Records`.
- Connect `Student & Guardian Records` to all four core operational modules: `Attendance Management`, `Fee Management`, `Examination Management`, and `Homework & Assignments`.
- Connect `Teacher & Employee Records` to `Attendance Management`, `Examination Management`, and `Homework & Assignments`.
- Connect `Fee Management` to `Payments & Reconciliation`.
- Connect `Payments & Reconciliation`, `Attendance Management`, `Examination Management`, and `Homework & Assignments` directly to `Dashboards & Reports`.
- Connect `Dashboards & Reports` to `Principal & Owner Decisions`.
- Connect `Principal & Owner Decisions` to `Targeted Communication`.
- Connect `Targeted Communication` to the receivers: `Parents & Students` and `Teachers & Employees`.
- Draw dashed lines from `Fee Management`, `Examination Management`, `Attendance Management`, and `Targeted Communication` to `Audit Logs` to represent asynchronous audit writing.

## Color Recommendations
- **Setup Layer**: Pale Orange (#FFEDD5) with Amber border (#D97706)
- **Core Operations**: Pale Blue (#EFF6FF) with Blue border (#2563EB)
- **Payments**: Pale Green (#ECFDF5) with Emerald border (#10B981)
- **Dashboards & Decisions**: Pale Indigo (#EEF2F6) with Indigo border (#4F46E5)
- **Communication & Stakeholders**: Light Purple (#F5F3FF) with Purple border (#7C3AED)
- **Audit Logs**: Light Gray (#F3F4F6) with Dark Gray border (#4B5563)
- **Background**: Soft Gray (#F8FAFC)

## Swimlanes
- **Lane 1: Setup & Identity** (Tenant setup, Master Data, Student/Staff records)
- **Lane 2: Operational Workflows** (Attendance, Fees, Exams, Tasks, Payments)
- **Lane 3: Analytics & Leadership** (Dashboards, Decisions)
- **Lane 4: Audience Engagement** (Communication, Parents, Staff)
- **Lane 5: Governance & Security** (Audit Logs)
- Separating these areas visually prevents cross-line clutter.
