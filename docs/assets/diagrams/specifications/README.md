# Draw.io Diagram Specifications

This folder contains draw.io design specifications for diagrams that are too detailed, layered, or frequently evolving to remain maintainable in Mermaid.

## Included Specifications

1. [vision-opportunity-map.drawio-spec.md](vision-opportunity-map.drawio-spec.md)  
   Reason: The strategic opportunity map has multiple parallel branches and would benefit from a manually arranged, presentation-friendly canvas.

2. [business-context.drawio-spec.md](business-context.drawio-spec.md)  
   Reason: The business context diagram spans market, school, solution, capability, and value layers and is easier to review in a structured draw.io layout.

3. [product-architecture-context.drawio-spec.md](product-architecture-context.drawio-spec.md)  
   Reason: The product architecture context includes many domain modules and platform services that need precise grouping and frequent revision.

4. [software-system-context.drawio-spec.md](software-system-context.drawio-spec.md)  
   Reason: The software system context is a multi-layer technical topology with external integrations and operational concerns that are better expressed in draw.io.

5. [proposed-future-workflow.drawio-spec.md](proposed-future-workflow.drawio-spec.md)  
   Reason: The proposed future workflow connects numerous setup, operations, dashboarding, communication, and audit systems, leading to a spiderweb of overlapping connections in Mermaid.

6. [module-dependency-map.drawio-spec.md](module-dependency-map.drawio-spec.md)  
   Reason: Represents highly interconnected domain modules with deep compilation and execution dependency chains that are extremely difficult to layout clearly in Mermaid code.

7. [vision-model.drawio-spec.md](vision-model.drawio-spec.md)  
   Reason: A massive 26-node tree model representing high-level product vision and functional domains that requires professional vertical card stacking.

8. [swot-analysis.drawio-spec.md](swot-analysis.drawio-spec.md)  
   Reason: A matrix-style 2x2 grid representing internal and external factors that cannot be natively formatted in a standard Mermaid flowchart.

9. [monitoring-flow.drawio-spec.md](monitoring-flow.drawio-spec.md)  
   Reason: A telemetry pipeline linking application components, databases, and queues through multiple telemetry lines (logs, metrics, traces) into a central observability engine and alerts.

