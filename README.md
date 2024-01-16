## 0.4: New note diagram

```mermaid
sequenceDiagram
    Note over Browser: the user clicks "Save"
    Browser->>+Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note over Server: the server parses form data and saves the new note
    Server-->>-Browser: 302 Redirect (to reload notes page)

    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    Server-->>-Browser: HTML document
    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>-Browser: CSS file
    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Server-->>-Browser: JavaScript file

    Note over Browser: the browser executes the JavaScript code that fetches JSON from the server
    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>-Browser: JSON file<br/>[{ "content": "Happy coding!", "date": "2024-1-1" }, ... ]
    Note over Browser: the browser executes the callback function that renders the notes
```

## 0.5: Single page app diagram

```mermaid
sequenceDiagram
    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    Server-->>-Browser: HTML document
    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>-Browser: CSS file
    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Server-->>-Browser: JavaScript file

    Note over Browser: the browser executes the JavaScript code that fetches JSON from the server
    Browser->>+Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>-Browser: JSON file<br/>[{ "content": "Happy coding!", "date": "2024-1-1" }, ... ]
    Note over Browser: the browser executes the callback function that renders the notes
```

## 0.6: New note in Single page app diagram

```mermaid
sequenceDiagram
    Note over Browser: the user clicks "Save"
    Note over Browser: the browser executes the callback `onSubmit` that <br/> 1) renders the notes with new note appended, and <br/> 2) send JSON to the server
    Browser->>+Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note over Server: the server parses JSON and saves the new note
    Server-->>-Browser: 201 Created
```
