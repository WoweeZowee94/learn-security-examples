# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
- There is a lack of input validation when the session is taking the user input from req.body
    which allows for potentially malicious inputs.
2. Briefly explain how a malicious attacker can exploit them.
- For example, a malicious attacker could input a script that creates a url that prompts
    unsuspecting users to input potentially sensitive information.
3. Briefly explain why **secure.ts** does not have the same vulnerabilties?
- secure.ts escapes any HTML input into the input and sanitizes it, preventing malicious
    users from injecting things like scripts into the document from the form input.
