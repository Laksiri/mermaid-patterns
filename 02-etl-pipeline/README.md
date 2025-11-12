# ETL Pipeline Diagram

## When to Use This

ETL (Extract, Transform, Load) diagrams visualize data processing workflows. Essential for data engineering documentation, pipeline design, and communicating data architecture.

## Example Scenario

This diagram shows a daily sales report generation pipeline: extract sales data from the database, clean and aggregate it, load into a data warehouse, and trigger automated reporting.

## Diagram

```mermaid
graph LR
    A[Extract: Pull from Sales DB] --> B[Transform: Clean & Aggregate]
    B --> C[Transform: Calculate Metrics]
    C --> D[Load: Insert into Data Warehouse]
    D --> E[Notify: Trigger Report Generation]
```

## Key Elements Explained

- **Extract**: Source data retrieval from operational database
- **Transform**: Data cleaning, aggregation, and business logic
- **Load**: Moving processed data to analytics storage
- **Trigger**: Automated downstream processes

## Tips & Best Practices

- Clearly label data sources and destinations
- Show transformation steps explicitly (don't hide complexity)
- Use subgraphs if you have multiple parallel pipelines
- Include frequency/schedule in documentation (daily, hourly, real-time)

## Common Variations

**With Error Handling:**
```mermaid
graph LR
    A[Extract Data] --> B{Data Valid?}
    B -->|Yes| C[Transform Data]
    B -->|No| D[Log Error & Alert]
    C --> E[Load to Warehouse]
    D --> F[Dead Letter Queue]
```

**Parallel Processing:**
```mermaid
graph TD
    A[Extract Data] --> B[Split by Type]
    B --> C[Process Sales Data]
    B --> D[Process Customer Data]
    B --> E[Process Inventory Data]
    C --> F[Merge & Load]
    D --> F
    E --> F
```

**With Data Quality Checks:**
```mermaid
graph LR
    A[Extract] --> B[Validate Schema]
    B --> C[Check Nulls]
    C --> D[Verify Ranges]
    D --> E[Transform]
    E --> F[Load to Warehouse]
```
