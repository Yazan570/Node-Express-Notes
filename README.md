# Node-Express-Notes
My notes for important node and express information
# Server.js
## Importing modules
1. import express from 'express'
   Imports the express module, which is a Node.js framework.
   It provides methods to handle HTTP requests, set up middleware*, and define routing*.
2. import cors from 'cors'
   Imports the cors middleware module.
   CORS (Cross-Origin Resource Sharing) allows your server to accept requests from a different origin (domain/port), which is often needed for frontend-backend  communication.
3. import catalogRoutes from '.catalogRoutes.js'
   Imports routing logic from a local file named catalogRoutes.js
   This file is exports an Express Router with endpoints related to services like GET, POST, PUT, DELETE.

## Code lines
1. const app = express();
   Creates an instance of the express application.
   This app object is used to define routes, middleware, and start the server.
2. app.use(express.json());
   This middleware parses the incoming requests with JSON payloads.
   Required for handling req.body in POST/PUT requests (body: JSON.stringify({...}) from the frontend).
3. app.use(cors());
   Enables CORS, allowing your server to accept requests from other origins if your frontend is on a different port.
   Without this, browsers will block cross-origin requests due to security policy (check the internet about the * in the browser params for extra details).
4. app.use('/services', catalogRoutes);
   Mounts the catalogRoutes under the /services path.
   For example, if catalogRoutes has a GET '/' route, it will be accessible at GET /services/ .
5. app.use((err, req, res, next) => { console.error(err.stack); res.status(500).send("Something broke!")});
   This is a special express middleware with four arguments (err, req, res, next), which automatically handles errors.
   err.stack logs the full error stack to the console.
   res.status(500).send(...) sends a generic 500 internal server error response to the client.
6. app.listen(8080, ()=>{console.log('Server is running on port 8080')});
   Starts the server and listens on port 8080.
   The callback logs a confirmation message when the server is successfully running.
         
# catalogRoutes.js

MiddleWare*: Middleware is software that acts as a bridge, enabling different applications and systems to communicate and share data with each other, often in a distributed environment.         
