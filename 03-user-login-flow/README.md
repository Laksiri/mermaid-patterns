# User Login Process Flow

## When to Use This

Process flow diagrams with decision points are perfect for documenting authentication flows, user journeys, or any process with conditional logic.

## Example Scenario

This diagram shows a standard user login process with two-factor authentication, including decision points for validation and 2FA verification.

## Diagram

```mermaid
graph TD
    A[User Enters Credentials] --> B{Valid Credentials?}
    B -->|No| C[Show Error Message]
    C --> A
    B -->|Yes| D[Send 2FA Code]
    D --> E[User Enters 2FA Code]
    E --> F{Valid 2FA Code?}
    F -->|No| G[Show Error & Retry]
    G --> E
    F -->|Yes| H[User Logged In Successfully]
```

**Code:**
````markdown
```mermaid
graph TD
    A[User Enters Credentials] --> B{Valid Credentials?}
    B -->|No| C[Show Error Message]
    C --> A
    B -->|Yes| D[Send 2FA Code]
    D --> E[User Enters 2FA Code]
    E --> F{Valid 2FA Code?}
    F -->|No| G[Show Error & Retry]
    G --> E
    F -->|Yes| H[User Logged In Successfully]
```
````

## Key Elements Explained

- **Decision Points**: Where the flow branches based on conditions
- **Validation Steps**: Security checks before granting access
- **Error Paths**: What happens when validation fails
- **Success State**: Final outcome of the process

## Tips & Best Practices

- Limit decision points to 1-2 per diagram for clarity
- Always show both success and failure paths
- Use descriptive labels on decision branches (Yes/No, Valid/Invalid)
- Keep error handling visible but don't let it dominate the diagram

## When to Use This Pattern

- Authentication and authorization flows
- User onboarding processes
- Feature access logic
- Form submission workflows

## Customization Ideas

**Simple Login (No 2FA):**
```mermaid
graph TD
    A[Enter Username & Password] --> B{Valid?}
    B -->|No| C[Show Error]
    C --> A
    B -->|Yes| D[Grant Access]
```

**With Session Management:**
```mermaid
graph TD
    A[User Login] --> B{Valid Credentials?}
    B -->|No| C[Reject]
    B -->|Yes| D[Create Session]
    D --> E[Set Cookie]
    E --> F[Redirect to Dashboard]
```

**OAuth Flow:**
```mermaid
graph LR
    A[Click Login] --> B[Redirect to OAuth Provider]
    B --> C[User Authorizes]
    C --> D[Return Auth Code]
    D --> E[Exchange for Token]
    E --> F[User Logged In]
```
