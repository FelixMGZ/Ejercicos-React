<h1>Sequence diagrams</h1>
<p>A Sequence diagram is an interaction diagram that shows how processes operate with one another and in what order.</p>

<h2>Exercise</h2>
<p>Create a similar diagram that describes the situation in which the user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes by writing something in the text field and clicking on the Save button.</p>

<h2>Solution</h2>

```mermaid
    sequenceDiagram
      participant User
      participant Browser
      participant Server

      User->>Browser: Submit "new note" form
      Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note/
      Server-->>Browser: 302 Found\nLocation: /exampleapp/notes

      Browser->>Server: GET /notes
      Server-->>Browser: HTML

      Browser->>Server: GET /main.css
      Server-->>Browser: CSS

      Browser->>Server: GET /main.js
      Server-->>Browser: JavaScript

      Note over Browser: Browser executes JS and requests JSON data
      Browser->>Server: GET /data.json
      Server-->>Browser: [{ content: "...", date: "..." }]
      Browser->>User: Displays the updated page
```
