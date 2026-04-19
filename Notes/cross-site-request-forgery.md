# Cross-Site Request Forgery (CSRF)

Cross-Site Request Forgery, also called **CSRF**, is a web security attack where an attacker tricks a logged-in user into sending an unwanted request to a website they are already authenticated on.

In simple words, the browser already trusts the website because the user is logged in. The attacker takes advantage of that trust and makes the victim perform an action without realizing it.

CSRF is dangerous because the request looks valid to the server. The server thinks the user intentionally made that request, but in reality, it was forced by an attacker.

---

## What is CSRF?

CSRF is an attack that targets the **trust between the browser and the server**.

It does not usually steal data directly like SQL Injection, and it does not inject script like XSS. Instead, it abuses the fact that a user is already logged in and the browser automatically sends session cookies or authentication tokens.

That means the attacker can make the victim’s browser send requests such as:

- changing password
- transferring money
- changing email address
- posting something
- deleting an account
- changing settings

---

## Why CSRF is dangerous

CSRF is dangerous because the victim does not usually notice anything unusual.

The request comes from the victim’s own browser, so the server may treat it as a legitimate action.

This can lead to:

- unauthorized account changes
- money transfer or payment actions
- email or password changes
- fake form submissions
- unwanted purchases
- deletion of important data
- admin-level actions in some cases

If the user is logged into a sensitive site like banking, email, or admin panel, the impact can be serious.

---

## How CSRF happens

CSRF works because browsers automatically send authentication information like cookies when a request goes to a website.

If a user is already logged in to `example.com`, the browser may automatically attach the session cookie when a request is made to that site.

An attacker can exploit this by making the victim visit a malicious page or click a crafted link that sends a request to the trusted site.

If the website does not have CSRF protection, it may accept the request as valid.

---

## Simple idea of CSRF

Imagine you are logged in to a shopping website.

You open a malicious website in another tab.

That malicious website secretly sends a request to the shopping site, maybe to change your delivery address or place an order.

Because your browser is already logged in, the shopping site may accept the request.

That is CSRF.

---

## Common places where CSRF can happen

CSRF can affect any action that changes data or performs a sensitive task, such as:

- changing password
- changing email
- updating profile settings
- transferring money
- adding a new payment method
- deleting content
- making purchases
- changing account permissions

Generally, any action that uses authentication and changes state can be a CSRF target.

---

## CSRF vs XSS

These two are often confused, but they are different.

- **XSS** injects malicious script into a website and runs it in the victim’s browser
- **CSRF** tricks the victim into sending a request they did not intend

A simple way to remember it:

- XSS = attack code runs in the browser
- CSRF = browser sends a forged request

XSS can sometimes be used to make CSRF easier, but they are still different vulnerabilities.

---

## How CSRF works technically

When a browser sends a request to a site, it may include cookies automatically.

If the website depends only on cookies to trust the user, then a forged request can look real.

For example, if a bank website accepts a request like:
`/transfer?to=attacker&amount=1000`

and the user is already logged in, the browser may send the session cookie along with that request.

If the site does not verify that the request was intentionally made by the user, the action may go through.

---

## Types of CSRF

CSRF can appear in a few different ways:

### 1. GET-based CSRF
This happens when dangerous actions are allowed through GET requests.

That is bad because GET requests are easy to trigger from links, images, or embedded resources.

### 2. POST-based CSRF
This happens when an attacker forces the victim’s browser to submit a forged POST request.

This is more common for sensitive actions like form submissions.

### 3. Login CSRF
This is when an attacker forces the victim to log into an account controlled by the attacker.

Later, the victim may unknowingly use the attacker’s account or leak information into it.

---

## Examples of vulnerable actions

CSRF often targets functions like:

- update profile
- change password
- change email
- transfer funds
- add shipping address
- enable notification settings
- delete account
- submit forms

If these actions are not protected properly, they may be vulnerable.

---

## Signs that a site may be vulnerable to CSRF

Some warning signs include:

- sensitive actions happen with no confirmation
- the site relies only on cookies for authentication
- there is no anti-CSRF token in forms
- important actions can be triggered by simple requests
- GET requests are used for changes
- no same-site cookie protection is set

These are not proof by themselves, but they are strong signs of weak CSRF protection.

---

## Prevention of CSRF

The good news is that CSRF can be prevented well if developers follow secure practices.

### 1. Use CSRF tokens
This is the most common and important defense.

A CSRF token is a random secret value that is added to a form or request. The server checks whether the token matches.

If the token is missing or wrong, the request is rejected.

This helps prove that the request came from the real site, not from a fake attacker page.

### 2. Use SameSite cookies
Setting cookies with `SameSite` helps reduce cross-site request abuse.

This tells the browser when cookies should or should not be sent with cross-site requests.

### 3. Require re-authentication for sensitive actions
For actions like password change, money transfer, or email change, asking the user to confirm again can help.

### 4. Use POST instead of GET for state-changing actions
Do not use GET requests for actions that change data.

GET should be used for reading data, not modifying it.

### 5. Check Origin and Referer headers
The server can verify where the request came from.

If the request is coming from an unexpected site, it can be blocked.

### 6. Avoid relying only on cookies
Use stronger request validation for sensitive actions.

### 7. Add confirmation screens
For risky actions, ask the user to confirm before continuing.

---

## CSRF token idea

A CSRF token works like a secret proof.

When the server gives a form to the user, it also gives a unique token.

When the form is submitted, the token must be sent back.

If an attacker tries to send a fake request from another site, they usually will not have the correct token.

That is why the server can reject it.

---

## Why SameSite cookies help

SameSite cookies reduce the chance that cookies will be sent in cross-site requests.

This makes it harder for another website to force an authenticated request.

It is not always enough by itself, but it is a very useful defense.

---

## Real-life impact of CSRF

A CSRF attack can cause serious problems such as:

- changing account details without permission
- transferring money
- deleting data
- changing security settings
- logging a user into the wrong account
- causing unwanted purchases
- damaging trust in the application

For websites with sensitive actions, CSRF protection is essential.

---

## CSRF in login systems

Some login systems can also be affected.

For example, a victim may be forced to log into an account controlled by the attacker.

This can confuse the user and may lead to session problems or data being linked to the wrong account.

---

## CSRF vs session hijacking

CSRF is not the same as stealing a session.

- **CSRF** tricks the browser into sending a request
- **Session hijacking** means the attacker steals or uses the actual session

CSRF uses the victim’s own authenticated browser session, while session hijacking means the attacker has the session itself.

---

## How developers should protect against CSRF

A secure website should:

- use CSRF tokens
- set cookies properly
- use SameSite protections
- avoid GET for sensitive actions
- validate request origin
- require confirmation for risky actions
- test forms and endpoints carefully
- apply security controls consistently

One weak endpoint can still create a big risk.

---

## Important points to remember

- CSRF tricks a logged-in user into performing an unwanted request.
- It works because browsers automatically send authentication cookies.
- It usually targets actions that change data.
- CSRF tokens are one of the best defenses.
- SameSite cookies, secure request methods, and header checks also help.

---

## Final summary

Cross-Site Request Forgery is a vulnerability where an attacker makes a victim’s browser send a request to a trusted website without the victim’s permission. It is dangerous because the server may think the action was intentionally done by the user.

The best protection is to use **CSRF tokens**, secure cookies, proper request validation, and safe handling of sensitive actions.

If you understand CSRF well, you understand an important part of web security: **a logged-in browser should never be trusted without proof of user intent**.