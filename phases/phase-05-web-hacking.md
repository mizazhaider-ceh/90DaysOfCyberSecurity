# Phase 5: Web Hacking with the PenTrix VulnLab

Days 43 to 56 turn you from a web user into a web attacker. You will learn how HTTP really works, how to intercept and modify traffic with Burp Suite, and how the most common web vulnerabilities are found and exploited. The heart of this phase is the PenTrix VulnLab, an intentionally vulnerable web app with 201 hands-on challenges across 29 modules, each its own small website. Flags in the lab are earned only by genuine exploitation, so every flag you collect proves a real skill.

## Day 43: How the Web Works and Burp Suite Setup
- **Learn:** Every website is built on HTTP. Your browser sends requests (method, path, headers, cookies) and the server sends back responses (status code, headers, body). Status codes like 200 (ok), 302 (redirect), 404 (not found), and 500 (server error) tell you what happened, while cookies and session tokens keep you logged in between requests.
- **Do:** Download and install Burp Suite Community from https://portswigger.net/burp/communitydownload, then install its CA certificate in your browser and route your browser traffic through the Burp proxy (127.0.0.1:8080) so you can see raw requests and responses in the Intercept tab.
- [ ] Done: I see live HTTP requests and responses flowing through Burp when I browse any website.

## Day 44: HTML Forms, GET vs POST, and Burp Repeater
- **Learn:** Forms send your input to the server, usually with GET (data visible in the URL, used for searches and lookups) or POST (data hidden in the request body, used for logins and submissions). Anything the browser sends can be edited before it reaches the server, which is exactly what attackers rely on.
- **Do:** Find any login or search form online, intercept its request in Burp, send it to Repeater, change the submitted values by hand, and resend it to watch how the server responds to modified input.
- [ ] Done: I captured a form request in Burp, edited its values in Repeater, and observed the server's response to the change.

## Day 45: Setting Up the PenTrix VulnLab
- **Learn:** The PenTrix VulnLab (https://github.com/mizazhaider-ceh/PenTrix-VulnLab) is an intentionally vulnerable web application with 201 challenges across 29 modules, each module its own small website. It runs locally with docker compose, so you get a safe, legal playground for real hacking practice.
- **Do:** Clone the repo with git clone, follow the README quickstart to bring it up with docker compose, open it in your browser through the Burp proxy, and solve your first 5 flags in the easiest modules (start with the beginner-rated challenges).
- [ ] Done: The lab is running locally and I have earned my first 5 flags through genuine exploitation.

## Day 46: SQL Injection Basics
- **Learn:** SQL injection happens when your input is pasted directly into a database query. With in-band injection you see results on the page, and UNION-based injection lets you append your own SELECT statement to pull data from other tables. A single quote (') is the classic test: if the page breaks or errors, the input is reaching the database.
- **Do:** In the lab's SQLi beginner modules, try a single quote in a search or login field, confirm the error behavior, then build a working UNION-based payload to extract data you were not supposed to see and earn the flags.
- [ ] Done: I completed the lab's SQLi beginner challenges using in-band and UNION-based injection.

## Day 47: Cross-Site Scripting (XSS)
- **Learn:** XSS happens when a website reflects your input back into the page without escaping it. Reflected XSS fires from a single crafted link or request, while stored XSS is saved on the server and executes for every visitor who loads the page. The proof-of-concept test is a simple alert box, like `<script>alert(1)</script>`.
- **Do:** In the lab's XSS modules, find an input field that reflects back into the page, craft a payload that pops an alert (reflected), then find one that persists your payload so it fires on reload (stored), earning the flags for both.
- [ ] Done: I completed the lab's XSS challenges, including at least one reflected and one stored payload.

## Day 48: Authentication Flaws
- **Learn:** Authentication breaks when logins accept brute-forced passwords, ship with default credentials like admin/admin, or have weak reset flows that let you take over someone else's account. Rate limiting, lockouts, and unpredictable reset tokens are the defenses; their absence is the vulnerability.
- **Do:** In the lab's authentication modules, try default credential pairs on the login pages, use Burp Intruder (Community edition supports this on a single host) to brute-force a weak password, and abuse a password reset flow to hijack an account and earn the flags.
- [ ] Done: I completed the lab's authentication challenges, including a successful brute-force or reset-flow takeover.

## Day 49: Broken Access Control and IDOR
- **Learn:** IDOR (insecure direct object reference) happens when the server trusts an ID in your request, like `?user_id=123`, without checking that the ID belongs to you. Changing the number can expose other users' data. Broken access control is the wider problem: hidden admin pages or functions that work for anyone who finds them.
- **Do:** In the lab's IDOR modules, log in as a low-privilege user, intercept a request that fetches your own data, change the ID parameter to another user's, and read data you should not see to earn the flags. Also try reaching a hidden admin function directly by URL.
- [ ] Done: I completed the lab's IDOR challenges by accessing another user's data through a modified ID parameter.

## Day 50: Server-Side Request Forgery (SSRF)
- **Learn:** SSRF happens when a server fetches a URL you control, for example an image proxy or webhook feature. By pointing it at internal addresses like 127.0.0.1 or cloud metadata endpoints, you can make the server attack itself or leak internal information. The defense is strict allow-lists on fetchable URLs.
- **Do:** In the lab's SSRF modules, find a feature that fetches a remote URL, point it at 127.0.0.1 with a port you suspect is open internally, and read the internal response to earn the flags.
- [ ] Done: I completed the lab's SSRF challenges by making the server fetch an internal resource for me.

## Day 51: File Upload Vulnerabilities
- **Learn:** File upload flaws happen when a server accepts files without proper checks. Uploading a web shell (a file the server then executes, like a PHP script) can give you code execution. Common bypasses include changing the extension, the MIME type, or hiding code inside an allowed file type.
- **Do:** In the lab's upload modules, upload a harmless test file first to learn what is allowed, then bypass the extension or type check to upload an executable payload and trigger it through the browser to earn the flags.
- [ ] Done: I completed the lab's file upload challenges by bypassing the upload checks and executing my payload.

## Day 52: OS Command Injection
- **Learn:** Command injection happens when your input is passed to a system shell, for example a ping or lookup tool that runs your text inside a shell command. Characters like `;`, `&&`, and `|` let you chain your own commands after the intended one. The telltale test is appending `; id` or `| whoami` and seeing system output in the response.
- **Do:** In the lab's command injection modules, find an input that reaches the operating system, confirm injection with a harmless command like `id`, then chain a command that reads a protected file to earn the flags.
- [ ] Done: I completed the lab's command injection challenges by executing system commands through a vulnerable input.

## Day 53: JWT and Session Flaws
- **Learn:** JSON Web Tokens (JWTs) carry your login claims in three base64 parts: header, payload, signature. If the server accepts tokens with the `none` algorithm, or with a weak or guessable secret, you can forge a token and become any user, including an admin. Session flaws are similar: predictable session IDs or tokens that never expire.
- **Do:** In the lab's JWT modules, decode your token, try the `none` algorithm trick and a weak-secret brute force, forge an admin token, and use it to access admin-only content and earn the flags.
- [ ] Done: I completed the lab's JWT challenges by forging a token and escalating my privileges.

## Day 54: XXE and SSTI Basics
- **Learn:** XXE (XML external entity) attacks abuse XML parsers that resolve external entities, letting you read server files through a crafted XML document. SSTI (server-side template injection) happens when your input lands inside a template engine, so expressions like `{{7*7}}` get evaluated by the server, which can lead to code execution.
- **Do:** In the lab's XXE or SSTI modules, submit a crafted XML document with an external entity to read a local file (XXE), or inject `{{7*7}}` into a template field and confirm the server evaluates it to 49 (SSTI), earning the flags.
- [ ] Done: I completed the lab's XXE or SSTI challenges by getting the server to process my crafted input.

## Day 55: Race Conditions
- **Learn:** Race conditions exploit the tiny gap between a check and an action. If a server checks your balance and then deducts it in two separate steps, sending many requests at once can let you spend the same money twice. Attackers use Burp's parallel request features or simple scripts to hit the endpoint simultaneously.
- **Do:** In the lab's race condition modules, find an action that should only work once (a coupon, a transfer, a vote), send many identical requests in parallel using Burp Repeater's request grouping or a small script, and earn the flag when the server processes more than it should.
- [ ] Done: I completed the lab's race condition challenges by winning a race against the server's check.

## Day 56: Milestone, 50 Flags and Your First Writeup
- **Learn:** Real security work ends with a writeup: what the vulnerability was, how you found it, the exact steps to reproduce it, and how to fix it. A clear one-page writeup is also the core of bug bounty reports and security consulting deliverables, so this is a career skill, not just homework.
- **Do:** Push your lab total to 50 earned flags, pick your favorite vulnerability from the phase, and write a one-page writeup covering the vulnerability type, how you discovered it, the exact payload or steps that earned the flag, and the fix you would recommend. For deeper theory on anything in this phase, work through the free labs at https://portswigger.net/web-security and check the vulnerability categories at https://owasp.org/www-project-top-ten/.
- [ ] Done: I reached 50 earned flags in the PenTrix VulnLab and wrote a one-page writeup of my favorite exploit.
