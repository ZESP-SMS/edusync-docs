# draw.io Design Specification — Strategic Vision Model

- File name: vision-model.drawio
- Source context: docs/01-Vision/vision.md

## Purpose
Present a structured, multi-tier capability map of the EduSync product vision. This diagram helps align stakeholders by grouping the platform's core capabilities (Academics, Security, AI, Leadership, Engagement) into high-level strategic domains stemming from a single vision anchor.

## Components
- **Vision Anchor**
  - EduSync Vision
- **Strategic Domains**
  - Unified School Operations
  - Secure Multi-Tenant SaaS
  - AI-Assisted Productivity
  - Data-Driven Leadership
  - Parent & Student Engagement
- **Platform Capabilities**
  - **School Operations Branch**: Admissions, Attendance, Academics, Fees & Payments, Staff Workflows
  - **SaaS Security Branch**: Tenant Isolation, Role-Based Access, Audit Logs, Secure APIs
  - **AI Productivity Branch**: Drafting Assistance, Operational Insights, Risk Signals, Workflow Recommendations
  - **Leadership Branch**: Dashboards, Reports, Forecasting, Compliance Visibility
  - **Engagement Branch**: Mobile Access, Notifications, Fee Transparency, Academic Updates

## Layout
- Use a central hub-and-spoke or structured horizontal cascade layout (from left to right or top to bottom).
- **Cascade Layout (Recommended)**:
  - Top level: Single centered box representing `EduSync Vision`.
  - Second level: 5 horizontally spaced cards representing the `Strategic Domains`.
  - Third level: Vertical stacks of rectangular cards directly under each respective domain.
- Group each branch inside a shaded background container matching the domain color scheme.
- Use card style nodes with bold headers for the domains, and simple flat rectangles for the platform capabilities.

## Connections
- Connect `EduSync Vision` to all 5 `Strategic Domains` with thick, centered lines.
- Connect each `Strategic Domain` to its child capability nodes. Use clean orthogonal connector paths (right angles) instead of direct diagonal lines to maintain a grid-like alignment.
- No cross-domain links are allowed in this structure to keep it strictly hierarchical.

## Color Recommendations
- **Vision Anchor**: Deep Purple (#581C87) with white text
- **Unified School Operations Branch**: Light Slate Blue (#EEF2F6) with Royal Blue headers (#2563EB)
- **SaaS Security Branch**: Light Teal (#F0FDFA) with Dark Teal headers (#0D9488)
- **AI Productivity Branch**: Light Rose (#FFF1F2) with Crimson headers (#E11D48)
- **Leadership Branch**: Light Emerald (#ECFDF5) with Forest Green headers (#059669)
- **Engagement Branch**: Light Amber (#FFFBEB) with Gold headers (#D97706)
- **Background**: Soft Clean Gray (#F8FAFC)

## Swimlanes
- Swimlanes are not strictly required since it is a pure hierarchical card tree.
- However, vertical columns or background containers for each of the 5 branches must be used to visually segregate the domains.
