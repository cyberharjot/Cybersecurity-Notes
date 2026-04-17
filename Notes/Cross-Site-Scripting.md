# Cross-Site Scripting (XSS)

Cross-Site Scripting, or **XSS**, is a web security vulnerability where an attacker injects malicious JavaScript into a website so that it runs in another user’s browser. This happens when a web application does not properly filter, escape, or sanitize user input.

XSS is one of the most common web attacks because many websites allow users to enter text, comments, messages, profile details, search terms, and other content. If that input is handled carelessly, the browser may treat it as code instead of normal text.

---

## What is XSS?

XSS means injecting harmful script into a website page. The script usually runs in the victim’s browser, not on the server.

That is what makes XSS dangerous. The attacker is not directly attacking the server database like SQL Injection. Instead, they are making the browser execute malicious code in the context of a trusted website.

---

## Why XSS is dangerous

If an attacker successfully injects JavaScript, they may be able to:

- steal cookies
- steal session tokens
- redirect users to fake websites
- show fake login forms
- log keystrokes
- change page content
- perform actions as the victim
- access sensitive information visible in the browser

In simple words, XSS can break the trust between the user and the website.

---

## How XSS happens

XSS usually happens when an application takes user input and displays it back without proper protection.

For example, if a website accepts a comment and then shows that comment on the page without escaping special characters, an attacker can put script code inside the comment.

Instead of showing text, the browser may run the script.

The main problem is:
**the application trusts user input too much**.

---

## Simple example

Suppose a website shows a user’s name on the page.

If someone enters a normal name, it is fine.

But if the website does not protect input properly, the attacker may enter something like:

`<script>alert('XSS')</script>`

If that gets executed in the victim’s browser, the attacker has successfully performed XSS.

---

## Types of XSS

There are three main types of XSS:

### 1. Stored XSS
Stored XSS happens when the malicious script is saved on the server or database and then shown to many users later.

Example places:
- comments
- forum posts
- profile fields
- chat messages

This is often the most dangerous type because many users can be affected.

### 2. Reflected XSS
Reflected XSS happens when the malicious script is sent in a request and immediately reflected back in the response without being properly handled.

Example places:
- search results
- error messages
- URL parameters
- form submissions

This type often requires the victim to click a malicious link.

### 3. DOM-based XSS
DOM-based XSS happens when the vulnerability exists in client-side JavaScript code.

In this case, the script changes the page directly in the browser using unsafe data from the URL, form fields, or other browser-based sources.

This type is harder to notice because the problem is inside the frontend code.

---

## Stored XSS in detail

Stored XSS is when the payload is permanently stored somewhere.

For example:
- attacker submits malicious comment
- server stores it in database
- other users open the page
- script runs in their browser

This is dangerous because the script keeps affecting users until it is removed.

---

## Reflected XSS in detail

Reflected XSS happens when the malicious input is part of a request and is reflected in the response.

For example:
- attacker sends a crafted link
- victim clicks it
- website includes the input in the page response
- browser runs the script

This type often depends on social engineering, because the victim must interact with the malicious link or request.

---

## DOM-based XSS in detail

DOM-based XSS is caused by unsafe JavaScript handling in the browser.

This can happen when frontend code reads data from:
- `window.location`
- URL fragments
- query strings
- form inputs
- local data

If that data is inserted into the page unsafely, the browser may execute attacker-controlled script.

This type is especially common in modern JavaScript-heavy websites.

---

## What XSS can steal or damage

XSS is dangerous because the malicious script runs in the victim’s browser as if it belongs to the trusted site.

That means it may be able to:

- read cookies if they are not protected properly
- hijack sessions
- perform actions on behalf of the user
- change displayed content
- capture input from forms
- send data to attacker-controlled servers
- trick users into giving credentials

If the site uses weak session handling, the damage can be serious.

---

## Real-life impact of XSS

A successful XSS attack can lead to:

- account takeover
- phishing inside a trusted website
- stolen sessions
- privacy leakage
- fake messages or fake pages
- loss of user trust
- damage to the website’s reputation

For websites with lots of users, this can be a major security problem.

---

## Common places where XSS appears

XSS can happen anywhere untrusted input is shown in a browser without proper escaping.

Common examples include:

- comment sections
- profile bios
- search fields
- chat boxes
- feedback forms
- URL parameters
- admin panels
- frontend DOM updates

Any location that takes input and displays it back should be treated carefully.

---

## Difference between XSS and SQL Injection

These two are often confused, but they are different.

- **SQL Injection** targets the database
- **XSS** targets the browser
- **SQL Injection** manipulates SQL queries
- **XSS** injects script code into web pages

Both are serious, and both come from unsafe input handling, but the attack target is different.

---

## How attackers usually test for XSS

In authorized security testing, people check whether the application:

- reflects input back to the page
- escapes special characters properly
- stores user input safely
- uses unsafe DOM methods
- allows script execution in comments or forms

Attackers often look for places where input is shown directly to the user.

---

## Prevention of XSS

The best defense against XSS is to never trust user input and always handle it safely.

### 1. Escape output
This is one of the most important defenses.

When displaying user input on a webpage, special characters should be escaped so the browser treats them as text, not code.

### 2. Sanitize input
Remove or block dangerous content when needed. This is useful for fields that allow limited formatting.

### 3. Use safe DOM methods
In frontend code, use safe methods that insert text as text, not as HTML.

Avoid unsafe methods like directly setting raw HTML from untrusted input.

### 4. Use Content Security Policy (CSP)
CSP helps reduce the impact of XSS by restricting what scripts can run.

It is not a full replacement for secure coding, but it adds an extra layer of protection.

### 5. Set HttpOnly cookies
If cookies are marked `HttpOnly`, JavaScript cannot read them directly. This helps reduce cookie theft through XSS.

### 6. Validate input
Check whether input is valid for the field, but remember that validation alone is not enough.

### 7. Avoid unsafe JavaScript patterns
Do not write frontend code that inserts raw user input into HTML without protection.

### 8. Keep frameworks updated
Older libraries and packages may have security issues, so updates matter.

---

## Safe vs unsafe handling

Unsafe idea:
- taking user input
- putting it directly into HTML
- letting the browser interpret it as code

Safe idea:
- treat user input as plain text
- escape special characters
- insert it using safe methods

This simple difference can prevent many XSS issues.

---

## XSS payload examples

These are common examples used in testing and learning:

- `<script>alert(1)</script>`
- `<img src=x onerror=alert(1)>`
- `<svg onload=alert(1)>`

These are not for misuse. They are commonly shown in security education to demonstrate how script injection works.

---

## Signs that a site may have XSS

Some warning signs include:

- input appears on the page exactly as entered
- script-like content behaves strangely
- page content changes unexpectedly
- popup alerts appear from injected input
- user data is reflected in response without escaping
- frontend code uses unsafe HTML insertion

These signs suggest that the application may not be handling input correctly.

---

## Best practices for developers

A secure website should follow these habits:

- escape output everywhere user input is displayed
- sanitize input when needed
- use secure frontend methods
- avoid raw HTML injection
- apply CSP
- mark cookies properly
- test all user input paths
- review code for unsafe DOM handling

Security should be built into both backend and frontend code.

---

## Important points to remember

- XSS means injecting malicious script into a website.
- It runs in the victim’s browser.
- It can steal sessions, show fake content, or perform actions as the user.
- The main types are stored, reflected, and DOM-based XSS.
- The best defense is output escaping, safe coding, and proper browser protections.

---

## Final summary

Cross-Site Scripting is a vulnerability where an attacker injects malicious JavaScript into a trusted website so that it runs in another user’s browser. It is dangerous because it can steal data, hijack sessions, and trick users inside a real website.

The best protection is to treat all input as untrusted, escape output properly, sanitize where needed, and use safe frontend and backend coding practices.

If you understand XSS well, you understand one of the biggest lessons in web security: **never let user input become executable code**.