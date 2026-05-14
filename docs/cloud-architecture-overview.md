# Cloud Architecture Overview

This monorepo contains a simple TODO application with a React frontend, an Express API, and an in-memory data store. The architecture is intentionally minimal and does not depend on any cloud-provider-specific services.

## System Context

```mermaid
flowchart LR
    user[User]
    frontend[React Frontend\npackages/frontend]
    api[Express API\npackages/backend]
    store[(In-Memory SQLite Store)]

    user -->|Uses browser UI| frontend
    frontend -->|HTTP /api/tasks| api
    api -->|Reads and writes tasks| store
```

## Sequence Diagram: User Creating a TODO

```mermaid
sequenceDiagram
    actor User
    participant Frontend as React Frontend
    participant API as Express API
    participant Store as In-Memory SQLite Store

    User->>Frontend: Enter title, optional description, optional due date
    User->>Frontend: Click Add Task
    Frontend->>API: POST /api/tasks with task payload
    API->>API: Validate title and normalize request data
    API->>Store: INSERT task record
    Store-->>API: Return new task id and stored row
    API-->>Frontend: 201 Created with new task JSON
    Frontend->>API: GET /api/tasks
    API->>Store: SELECT tasks
    Store-->>API: Return task list
    API-->>Frontend: 200 OK with updated tasks
    Frontend-->>User: Render updated TODO list
```