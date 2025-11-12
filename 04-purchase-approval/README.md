# Business Process Flow - Purchase Approval

## When to Use This

Business process diagrams document operational workflows, approval processes, and standard operating procedures. Perfect for business analysts, operations teams, and process documentation.

## Example Scenario

This diagram shows a purchase request approval workflow with automatic approval for small purchases and manager/finance approval for larger amounts.

## Diagram

```mermaid
graph TD
    A[Employee Submits Purchase Request] --> B[Manager Reviews Request]
    B --> C{Amount Under $1000?}
    C -->|Yes| D[Auto-Approve]
    C -->|No| E[Send to Finance Team]
    E --> F[Finance Reviews]
    F --> G{Approve?}
    G -->|Yes| H[Purchase Approved]
    G -->|No| I[Purchase Rejected]
    D --> H
```

## Key Elements Explained

- **Submission**: Starting point initiated by employee
- **Review Stages**: Different approval levels based on amount
- **Decision Logic**: Conditional routing based on purchase value
- **End States**: Clear outcomes (approved or rejected)

## Tips & Best Practices

- Clearly label who is responsible for each step
- Show decision criteria explicitly ($1000 threshold)
- Include both approval and rejection paths
- Consider adding timing/SLA information in actual documentation

## Common Use Cases

- Approval workflows (expense, vacation, hiring)
- Order fulfillment processes
- Customer onboarding workflows
- Incident response procedures

## Customization Ideas

**Multi-Level Approval:**
```mermaid
graph TD
    A[Submit Request] --> B{Amount?}
    B -->|Under $500| C[Manager Approves]
    B -->|$500-$5000| D[Director Approves]
    B -->|Over $5000| E[VP Approves]
    C --> F[Approved]
    D --> F
    E --> F
```

**With Rejection Feedback Loop:**
```mermaid
graph TD
    A[Submit Request] --> B[Manager Review]
    B --> C{Decision}
    C -->|Approve| D[Approved]
    C -->|Reject| E[Return with Feedback]
    C -->|Request Changes| F[Employee Updates]
    E --> G[Rejected]
    F --> A
```

**Parallel Approvals:**
```mermaid
graph TD
    A[Submit Large Purchase] --> B[Manager Review]
    A --> C[Finance Review]
    A --> D[IT Security Review]
    B --> E{All Approved?}
    C --> E
    D --> E
    E -->|Yes| F[Purchase Approved]
    E -->|No| G[Purchase Rejected]
```
