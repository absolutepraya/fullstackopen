<!--- to enable mermaid extension on vsc -->
```mermaid

sequenceDiagram
    participant Browser
    participant Server

    Note over Browser: User submits form
    Browser->>Browser: Prevent default form submission
    Browser->>Browser: Create new note and add to notes list
    Browser->>Browser: Rerender note list on page
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate Server
    Server-->>Browser: Respond with status 201 (note created)
    deactivate Server
    Note right of Browser: The JavaScript code sends the new note to the server, and renders it
    Note right of Browser: The code e.preventDefault() prevents the page from refreshing
