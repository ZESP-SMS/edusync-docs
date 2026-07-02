# Frontend

The frontend experience is focused on fast navigation, role-based dashboards, and consistent school operations workflows.

```mermaid
flowchart LR
    Shell[App Shell] --> Router[Route Layer]
    Router --> Pages[Dashboard, Students, Fees, Attendance]
    Pages --> State[API and State Management]
    State --> Components[Reusable UI Components]
```
