# New note in Single page app diagram    

diagram depicting the situation where the user creates a new note using the single-page version of the app.

```mermaid
sequenceDiagram

    participant browser
    participant server

    browser --> server: CONNECTED https://studies.cs.helsinki.fi/exampleapp/spa

    note left of browser : when user clicks save,<br> new note is added to the<br> list & then sent to server
    browser ->> server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa

    activate server
    note right of server: server stores new note & then<br> responds with ackowledgement
    server ->> browser: 201 Created, {"message":"note created"}
    deactivate server    

```
