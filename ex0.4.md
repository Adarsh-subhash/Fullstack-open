```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Browser->>Browser: User enters note in text field
    Browser->>Server: HTTP POST /exampleapp/new_note
    activate Server
    Note right of Server: Server processes and stores the new note
    Server-->>Browser: Redirect to /exampleapp/notes
    deactivate Server

    Browser->>Server: HTTP GET /exampleapp/notes
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    Browser->>Server: HTTP GET /exampleapp/main.css
    activate Server
    Server-->>Browser: main.css
    deactivate Server

    Browser->>Server: HTTP GET /exampleapp/main.js
    activate Server
    Server-->>Browser: main.js
    deactivate Server

    Browser->>Browser: Execute main.js
    Browser->>Server: HTTP GET /exampleapp/data.json
    activate Server
    Server-->>Browser: JSON data (updated with new note)
    deactivate Server

    Browser->>Browser: Render updated notes on the page
