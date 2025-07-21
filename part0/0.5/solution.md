## Single page app diagram (Exercise 0.5)

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User navigates to SPA URL

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JavaScript file (spa.js)
    deactivate server

    Note right of browser: JavaScript runs and fetches notes data

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON with notes
    deactivate server

    Note right of browser: Browser renders notes dynamically

    Note right of browser: User enters note and submits

    browser->>server: POST /new_note_spa (AJAX request with JSON)
    activate server
    server-->>browser: HTTP 201 Created (no redirect)
    deactivate server

    Note right of browser: Browser updates notes list dynamically without page reload
