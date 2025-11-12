# Data Flow Diagram

## When to Use This

Use data flow diagrams to visualize how data moves through a system. Perfect for documenting APIs, understanding system architecture, or explaining data pipelines to stakeholders.

## Example Scenario

This diagram shows a typical web application data flow: a user submits a form, the API validates the data, stores it in a database, and sends a confirmation back to the user.

## Diagram

```mermaid
graph TD
    A[User Submits Form] --> B[API Receives Request]
    B --> C[Validate Data]
    C --> D[Store in Database]
    D --> E[Return Confirmation]
    E --> A
```

**Code:**
````markdown
```mermaid
graph TD
    A[User Submits Form] --> B[API Receives Request]
    B --> C[Validate Data]
    C --> D[Store in Database]
    D --> E[Return Confirmation]
    E --> A
```
````

## Key Elements Explained

- **User Input**: Starting point of the data flow
- **API Layer**: Handles validation and business logic
- **Database**: Persistent storage layer
- **Response**: Confirmation sent back to user

## Tips & Best Practices

- Keep flows left-to-right or top-to-bottom for readability
- Use clear, specific labels (avoid generic terms like "Process 1")
- Limit to 7 nodes or fewer for clarity
- Add colors/styling sparingly - clarity over aesthetics

## When to Use This Pattern

- Documenting API endpoints
- Explaining system architecture to non-technical stakeholders
- Onboarding new team members
- Technical design documents

## Customization Ideas

**Add Decision Points:**
```mermaid
graph TD
    A[User Submits Form] --> B[API Receives Request]
    B --> C{Valid Data?}
    C -->|Yes| D[Store in Database]
    C -->|No| E[Return Error]
    D --> F[Return Success]
```

**Show Parallel Processing:**
```mermaid
graph LR
    A[User Request] --> B[API Gateway]
    B --> C[Auth Service]
    B --> D[Data Service]
    C --> E[Response]
    D --> E
```
