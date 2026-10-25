# 0.4: New note diagram   

diagram depicting the situation where the user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes by writing something into the text field and clicking the Save button.

```mermaid
sequenceDiagram

    participant browser
    participant server

    browser --> server: CONNECTED : https://studies.cs.helsinki.fi/exampleapp/notes

    Note left of browser: User types text into<br>inputbox & clicks save

    browser ->> server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: Reads new_note & Stores it
    server ->> browser: 302 Found, Location: /exampleapp/notes 
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server->>browser: notes (HTML Document)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server->>browser: main.css
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: main.js
    deactivate server

    Note left of browser: browser runs javascript <br>& fetches json file

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: data.json
    deactivate server

    Note left of browser: browser runs callback<br> function to display notes
```
