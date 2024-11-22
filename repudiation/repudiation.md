# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
- There is no form of authentication setup for retrieving all messages in the system,
so a malicious user could directly access the messages endpoint and retrieve all of the data in the system.
- There is also no logging setup for the requests made to the server allowing users to anonymously
send and retrieve information from the server with no recourse from server admins. 
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
- The addition of request logging for every request containing the IP of the request. This ensures
that actions are traceable and creates a request history for server admins to track.
- It is not implemented, but it is implied that authentication is added to the endpoints that return
potentially sensitive server information.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
- The middleware design pattern is used to address the vulnerability. In this instance, a logging middleware is added
to each request made to the server, logging a timestamp, url, method and IP address for each request that allows admins
to track each request made to the server. 