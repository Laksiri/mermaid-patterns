# Sequence Diagram - Password Reset

## When to Use This

Sequence diagrams show interactions between different parts of a system over time. Ideal for documenting API calls, service communication, and system integrations.

## Example Scenario

This diagram shows how different components interact during a password reset: the user interface, backend API, database, and email service.

## Diagram

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant API
    participant EmailService

    User->>Frontend: Request password reset
    Frontend->>API: POST /reset-password
    API->>API: Generate reset token
    API->>EmailService: Send reset email
    EmailService-->>API: Email sent confirmation
    API-->>Frontend: Success response
    Frontend-->>User: Check your email message
```

**Code:**
````markdown
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant API
    participant EmailService

    User->>Frontend: Request password reset
    Frontend->>API: POST /reset-password
    API->>API: Generate reset token
    API->>EmailService: Send reset email
    EmailService-->>API: Email sent confirmation
    API-->>Frontend: Success response
    Frontend-->>User: Check your email message
```
````

## Key Elements Explained

- **Participants**: The actors/systems involved in the interaction
- **Messages**: Communications between participants (arrows)
- **Sequence**: The order of operations from top to bottom
- **Responses**: Return values and confirmations (dashed arrows)

## Tips & Best Practices

- Limit to 3-5 participants for readability
- Show request and response pairs clearly
- Use descriptive message labels
- Keep the sequence linear - avoid too many conditional branches

## When to Use This Pattern

- API documentation
- Microservices communication
- Integration workflows
- Debugging distributed system issues

## Customization Ideas

**With Database Interaction:**
```mermaid
sequenceDiagram
    participant User
    participant API
    participant Database
    participant Email

    User->>API: Reset password request
    API->>Database: Check user exists
    Database-->>API: User found
    API->>Database: Store reset token
    API->>Email: Send reset link
    Email-->>API: Sent
    API-->>User: Check email
```

**Complete Reset Flow:**
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant API
    participant Database

    User->>Frontend: Click reset link
    Frontend->>API: Validate token
    API->>Database: Check token validity
    Database-->>API: Token valid
    API-->>Frontend: Show reset form
    User->>Frontend: Enter new password
    Frontend->>API: Submit new password
    API->>Database: Update password
    Database-->>API: Updated
    API-->>Frontend: Success
    Frontend-->>User: Password changed
```

**With Error Handling:**
```mermaid
sequenceDiagram
    participant User
    participant API
    participant Database

    User->>API: Reset request
    API->>Database: Find user by email
    alt User exists
        Database-->>API: User found
        API-->>User: Email sent
    else User not found
        Database-->>API: Not found
        API-->>User: Email sent (security)
    end
    Note over API,User: Always return success to prevent email enumeration
```
