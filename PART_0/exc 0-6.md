```mermaid
sequenceDiagram

participant browser
participant server

browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/spa
activate server
server ->> browser: HTML document
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server-->>browser: CSS file
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
activate server
server-->>browser: JS file
deactivate server

The browser starts the execution of the JS file
browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
activate server
server ->> browser: displays JSON data
deactivate server

Note over browser, server: Upon submitting a new form, JS event handler prevents default behaviour (refreshing the page)
Note over browser, server: A new note object is created and pushed to the notes list
Note over browser, server: redrawNotes() function is called to re-render note list

browser ->> server: POST request to https://fullstack-exampleapp.herokuapp.com/new_note_spa with some new note data (user hits the submit button) as JSON
activate server
server ->> browser: responds with status code 201 created
deactivate server

```
