# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

    `$ npx install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

    `npx ts-node mal.ts`

4. Open __http://localhost:8000__ in a browser, type a name and Submit.

5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage__. You should see a __connect.sid__ cookie being set.

6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out? 


## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.
- The cookie validating the user is not secure, so it is vulnerable to being stolen or intercepted through a spoofing
    attack, such as what is done in mal-steal-cookie.html/mal.ts 
2. Briefly explain different ways in which vulnerability can be exploited.
- If a malicious attacker can direct a logged in user to a spoofed webpage, such as mal-steal-cookie.html,
they can trick them into sending a request that contains their validation cookie, which can they be stolen and used 
to infiltrate the system. 
3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.
- Secure.ts has the 'httpOnly' property of the cookie set to 'true' which disallows malicious users from
interacting with the cookie programatically, securing it from spoofing attacks.