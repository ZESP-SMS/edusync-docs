# Diagram Standards for EduSync Documentation

| Field | Value |
| --- | --- |
| Title | Diagram Standards for EduSync Documentation |
| Document ID | DOC-DIAG-001 |
| Version | 1.0 |
| Status | Draft |
| Author | EduSync Documentation Team |
| Created Date | 2026-07-02 |
| Last Updated | 2026-07-02 |
| Reviewers | Product, Architecture, Engineering, Security, UX |
| Approval Status | Pending Review |
| Confidentiality | Internal |

## 1. Executive Summary

This document defines the enterprise standards for creating, maintaining, and reviewing diagrams used in the EduSync documentation repository. The objective is to ensure that all diagrams are accurate, maintainable, consistent, and suitable for both business and technical audiences.

EduSync documentation must present architecture, workflows, data structures, and system interactions through diagrams that are precise, reusable, and version controlled. The standards in this document establish when to use Mermaid, draw.io, Figma, dbdiagram.io, Structurizr, and other diagram tools in the context of a production SaaS documentation system.

## 2. Purpose

The purpose of this document is to standardize diagram creation across the EduSync documentation repository so that:

- diagrams remain consistent across product, architecture, backend, frontend, and security documents;
- diagrams can be reviewed and maintained easily;
- diagrams are appropriate to the audience and the level of abstraction;
- diagrams align with enterprise documentation expectations;
- diagrams support effective collaboration between product, engineering, security, and design teams.

## 3. Objectives

This standard aims to:

- define the appropriate tool for each diagram type;
- provide naming and organization rules;
- define repository storage conventions;
- establish review expectations and quality criteria;
- improve maintainability of architecture and workflow documentation.

## 4. Scope

This document applies to all diagrams used in:

- product documentation;
- software requirements documentation;
- architecture documentation;
- API and backend design documentation;
- deployment and infrastructure documentation;
- security documentation;
- UI and user flow documentation;
- database and data model documentation.

## 5. Out of Scope

This document does not define:

- detailed UI component libraries;
- low-level database implementation details;
- backend coding standards;
- non-documentation diagram tools outside the approved toolset.

## 6. Audience

This standard is intended for:

- product managers;
- business analysts;
- architects;
- backend and frontend engineers;
- DevOps and security engineers;
- technical writers;
- UX designers;
- QA engineers.

## 7. Definitions

- Diagram: A visual representation of a system, workflow, relationship, or process.
- Mermaid: A Markdown-native diagramming format that is ideal for lightweight documentation and Git-based collaboration.
- draw.io: A collaborative diagramming tool for technical and business diagrams that require rich editing and export flexibility.
- Figma: A UI and experience design tool suited for wireframes, user flows, and high-fidelity visual design artifacts.
- dbdiagram.io: A database modeling tool specifically for ER diagrams and relational schema representation.
- Structurizr: A tool for C4 model architecture diagrams and system context modeling.
- Source Diagram: The editable master file maintained in version control.
- Exported Diagram: A rendered or static artifact used inside documentation or external presentations.

## 8. Diagram Philosophy

EduSync diagrams must be created with the following principles:

1. Clarity over decoration.
   Diagrams must communicate the intended concept clearly and without visual noise.

2. Correctness over complexity.
   The diagram must represent the system accurately and avoid unnecessary abstraction.

3. Maintainability over one-time convenience.
   Diagrams must remain easy to update as the product evolves.

4. Context over detail.
   Every diagram must show the right level of abstraction for the intended audience.

5. Consistency over personal style.
   The same types of diagrams should use a common structure, naming approach, and visual language.

6. Security and tenant awareness.
   Diagrams must reflect multi-tenant boundaries, access control, and data isolation where relevant.

7. Documentation-first design.
   Diagrams must support the documentation narrative and not exist as isolated artifacts.

## 9. When to Use Mermaid

Use Mermaid when:

- the diagram is intended to live directly inside Markdown documentation;
- the diagram is simple to medium complexity;
- the diagram is part of a Git-based documentation workflow;
- the diagram should be easy to review in pull requests;
- the diagram is a flowchart, sequence diagram, activity diagram, state diagram, ER diagram, or deployment diagram for documentation purposes;
- the diagram needs to be rendered by MkDocs or GitHub-compatible Markdown tools.

Mermaid is preferred for:

- workflow diagrams;
- system interaction diagrams;
- sequence interactions;
- activity flows;
- basic deployment views;
- simple ER diagrams for documentation context.

Mermaid should not be used when:

- the diagram requires advanced layout control;
- the diagram must be highly visual and presentation-oriented;
- the diagram is a complex enterprise architecture model;
- the diagram needs pixel-precise design or print-quality presentation.

## 10. When to Use draw.io

Use draw.io when:

- the diagram is a conceptual or technical architecture sketch that needs frequent editing;
- the diagram requires rich formatting, connectors, containers, or custom visual styling;
- the diagram is shared across business and engineering stakeholders;
- the diagram needs to be exported into PNG, SVG, or PDF;
- the diagram is an operational or infrastructure diagram that benefits from manual layout control.

draw.io is preferred for:

- architecture diagrams that need frequent refinement;
- system topology diagrams;
- process maps;
- internal workflow diagrams;
- diagrams that must be reviewed in a visual editor rather than code.

## 11. When to Use Figma

Use Figma when:

- the diagram is part of a user experience or interface experience artifact;
- the diagram is a user journey, wireframe, interaction flow, or user experience map;
- the design must be highly visual and presentation-ready;
- the artifact requires collaboration with product designers and UX stakeholders.

Figma is preferred for:

- user journeys;
- wireframe-based flows;
- prototype screens and interaction diagrams;
- experience maps;
- product-facing visual communication.

## 12. When to Use dbdiagram.io

Use dbdiagram.io when:

- the primary artifact is an ER diagram or relational data model;
- the team needs a concise database schema representation for documentation and implementation alignment;
- the diagram should be easy to edit collaboratively and exported as Markdown or image assets.

dbdiagram.io is preferred for:

- entity relationship diagrams;
- relational schema planning;
- core domain model documentation;
- database design collaboration with engineering teams.

## 13. When to Use Structurizr

Use Structurizr when:

- the team needs C4 architecture diagrams;
- the documentation must present system context, containers, components, and dependencies at a professional architecture level;
- the diagram should be maintained as part of an architectural model rather than a one-off drawing;
- the architecture needs to show boundaries, responsibilities, and technologies clearly.

Structurizr is preferred for:

- C4 Model context diagrams;
- container diagrams;
- component diagrams;
- architecture views for technical stakeholders.

## 14. Naming Conventions

All diagram files must follow a consistent naming convention.

### 14.1 General Rule

Use lowercase, hyphen-separated names.

Example:

- authentication-flow.mmd
- student-attendance-sequence.mmd
- school-tenant-context.puml
- er-student-management.dbml

### 14.2 Naming Pattern

Use the following pattern:

- <domain>-<view>-<type>

Examples:

- auth-login-flow
- student-attendance-sequence
- school-tenant-c4-context
- er-student-guardian

### 14.3 Versioned Files

If a diagram is maintained as a source file with an exported artifact, the source file should use the base name and the exported artifact should use the same name plus the file extension.

## 15. Folder Structure

Diagrams must be stored in a structured and predictable location.

Recommended structure:

```text
docs/
  assets/
    diagrams/
      mermaid/
      drawio/
      figma/
      dbdiagram/
      structuriwr/
      exports/
```

For repository documentation, the preferred approach is:

- store editable source files in the documentation repository under a dedicated diagrams folder;
- store exported image files in an exports subfolder;
- link the exported file from the relevant Markdown document;
- keep source and exported diagrams in sync.

## 16. Export Formats

The export format must match the purpose of the diagram.

### 16.1 Mermaid

Preferred export formats:

- SVG
- PNG
- Markdown render in documentation

### 16.2 draw.io

Preferred export formats:

- SVG
- PNG
- PDF

### 16.3 Figma

Preferred export formats:

- PNG
- SVG
- PDF

### 16.4 dbdiagram.io

Preferred export formats:

- PNG
- SVG
- DBML source

### 16.5 Structurizr

Preferred export formats:

- SVG
- PNG
- Mermaid or PlantUML export where supported

## 17. Version Control Strategy

All source diagrams must be version controlled.

### 17.1 Requirements

- Store diagram source files in Git.
- Keep source files under the documentation repository.
- Use descriptive commit messages for diagram changes.
- Review diagram updates in pull requests.
- Avoid storing only exported images without the editable source file.

### 17.2 Change Management

When a diagram changes:

- update the source file;
- regenerate the exported artifact if required;
- update any document that references the diagram;
- include a short note in the commit or PR describing the change.

## 18. Diagram Review Checklist

Every diagram must be reviewed against the following checklist before being accepted into the repository:

- The diagram has a clear purpose and target audience.
- The diagram uses the correct tool for the use case.
- The diagram is accurate and reflects the current system state.
- The labels and naming are consistent.
- The diagram uses a readable layout and spacing.
- The diagram avoids unnecessary visual clutter.
- The diagram aligns with the surrounding documentation narrative.
- The diagram is stored in the correct folder.
- The diagram has an exported artifact when required.
- The diagram is reviewed by the relevant domain owner.
- The diagram does not expose sensitive or non-public implementation details where unnecessary.

## 19. Mermaid Coding Standards

When creating Mermaid diagrams:

- keep the syntax simple and readable;
- use clear node labels;
- use consistent capitalization and naming;
- prefer simple edge labels where helpful;
- avoid overly dense graphs;
- use subgraphs where the diagram contains multiple domains;
- keep the diagram aligned to the documentation context;
- use comments sparingly and only when they improve readability.

### Mermaid conventions

- Use flowchart for process and workflow views.
- Use sequenceDiagram for request and response interactions.
- Use stateDiagram-v2 for lifecycle-driven behavior.
- Use activityDiagram for operational steps.
- Use erDiagram for relational data modeling.
- Use classDiagram only where object-oriented design is being documented.
- Use deploymentDiagram for infrastructure and runtime topology.

### Mermaid quality rules

- Avoid crossing lines unnecessarily.
- Prefer top-to-bottom or left-to-right layouts where readable.
- Use short labels and standard terminology.
- Ensure the diagram is still readable in GitHub and MkDocs renderers.

## 20. Draw.io Standards

When creating draw.io diagrams:

- use a consistent shape language for systems, actors, services, data stores, and external entities;
- keep layout balanced and easy to scan;
- use consistent connector styles and labels;
- name layers or groups clearly where appropriate;
- store the editable draw.io source file in the repository;
- export a static SVG or PNG for inclusion in documentation.

## 21. Figma Standards

When creating Figma diagrams:

- use the approved design system colors and spacing where applicable;
- ensure the artifact is clearly structured for stakeholders;
- maintain a clean and presentation-ready layout;
- export assets using consistent dimensions and formats;
- keep the source file available for collaborative iteration.

## 22. C4 Model Standards

EduSync architecture documentation should use the C4 Model for system-level architecture where appropriate.

### 22.1 C4 Levels

- Level 1: System Context Diagram
- Level 2: Container Diagram
- Level 3: Component Diagram
- Level 4: Code Diagram

### 22.2 C4 Rules

- Use the correct abstraction level for the audience.
- Keep system boundaries explicit.
- Show major responsibilities rather than implementation minutiae.
- Use consistent terminology for systems, containers, and components.
- Show external actors and dependencies clearly.
- Ensure the diagram supports the architecture narrative in the documentation.

### 22.3 Recommended C4 Usage

- Use C4 for high-level architecture documentation.
- Use Structurizr or equivalent tooling to maintain the model.
- Keep component diagrams aligned with the modular monolith and microservice-ready architecture of EduSync.

## 23. ER Diagram Standards

ER diagrams must follow these rules:

- show logical entities and relationships clearly;
- identify primary keys, foreign keys, and cardinality where relevant;
- reflect multi-tenant design by showing school_id where applicable;
- avoid overloading the diagram with implementation-only details;
- use consistent naming with the domain model and database design documents;
- ensure the diagram reflects the actual domain boundaries of EduSync.

## 24. Flowchart Standards

Flowcharts should:

- represent a single workflow or process clearly;
- use consistent labels for decision points and actions;
- show the main success path first;
- show alternate and exception paths clearly;
- avoid unnecessary branching that reduces readability.

## 25. Sequence Diagram Standards

Sequence diagrams should:

- represent interaction between major actors, services, and components;
- show the sequence of messages in a readable top-to-bottom order;
- indicate synchronous and asynchronous interactions where relevant;
- keep the diagram focused on the key interaction path.
- avoid including every implementation detail when it dilutes the purpose.

## 26. Activity Diagram Standards

Activity diagrams should:

- represent business or operational processes with clear start and end points;
- use decision nodes where branching is required;
- depict parallel or concurrent activities only when relevant;
- preserve readability for non-developer readers where necessary.

## 27. Deployment Diagram Standards

Deployment diagrams should:

- show the deployment topology of the EduSync platform;
- include application runtime components, reverse proxies, databases, cache, queues, object storage, and external service integrations;
- distinguish between cloud-managed services and self-managed components;
- reflect security boundaries and network zones where relevant;
- clearly show tenant isolation and operational regions where applicable.

## 28. Conclusion

Effective diagrams are essential to the clarity, quality, and maintainability of EduSync documentation. By following this standard, the documentation repository will produce diagrams that are consistent, enterprise-grade, reviewable, and appropriate for both business and engineering audiences.

The guiding principle is simple: every diagram must help the reader understand the system better, faster, and with less ambiguity.
