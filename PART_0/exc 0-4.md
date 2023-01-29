```mermaid
sequenceDiagram

participant browser
participant server

browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/notes
activate server
server ->> browser: HTML document
deactivate server

browser-->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server-->>browser: CSS file
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
activate server
server->>browser: JS file
deactivate server

Note over browser, server: JS event handler function is called upon change of state of the object.
Note over browser, server: The browser starts the execution of the JS file
browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
activate server
Note over browser, server: JS displays JSON data in the browser as a list, each li tag containing individual note content


browser ->> server: POST request to https://fullstack-exampleapp.herokuapp.com/new_note with some new note data (user hits the submit button) as the body of the POST request
activate server
Note over browser, server: Server creates a new note object with "content" data received from the req.body field of the request object req
Note over browser, server: New note is pushed to the notes array

server ->> browser: re-renders the page with the new data displayed


```
