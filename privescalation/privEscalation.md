# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
- The lack of formal authentication in the update-role route allows any user request with a valid userId
to access and attempt to change roles, potentially granting themself admin access.
- An attacker can manipulate the userId in a request to impersonate an admin and gain unauthorized access to the role change functionality.
2. Briefly explain how a malicious attacker can exploit them.
- Through a malicious request with the userId of an admin, an attacker can set their own role to admin. (priviledge escalation)
    - Due to the lack of authentication to verify the identity of the requester, the server will process future requests
as if they came from an admin.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
- The secure file uses session middleware to track authenticated users. Only logged-in users with valid session data can
access the update-role functionality. This prevents users from impersonating others using the userId in the request.
- After verifying that the user is logged in, the system checks the role of the logged-in user to ensure only admins
can perform role changes.
- The session config uses secure options such as httpOnly and sameSite to protect session data from being access or manipulated
by attacks via client scripts or cross-site requests.