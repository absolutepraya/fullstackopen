<!--- to enable mermaid rendering -->
```mermaid

sequenceDiagram
    participant Browser
    participant Server

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Server-->>Browser: Tell to GET https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Server

    Note right of Browser: The data is sent via POST, then the server-side app saves the data to JSON
    Note right of Browser: The server-side app then redirects the browser to GET /notes page

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: CSS file
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Server
    Server-->>Browser: JavaScript file
    deactivate Server

    Note right of Browser: The browser starts executing the JavaScript code that fetches the JSON from the Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{content: "gjh", date: "2024-06-04T19:21:43.705Z"}, ...]
    deactivate Server

    Note right of Browser: The browser executes the callback function that renders the notes
