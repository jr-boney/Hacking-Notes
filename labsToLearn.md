# Server-Side Vulnerabilities

This document outlines common server-side vulnerabilities that developers and security professionals should be aware of.

## 1. Cross-site Scripting (XSS)
- XSS vulnerabilities occur when an attacker is able to inject malicious scripts into web pages viewed by other users.
- These scripts can steal user data, perform actions on behalf of users, or alter the page content.

## 2. File Upload Vulnerabilities
- Improper handling of file uploads can allow attackers to upload malicious files.
- This can result in remote code execution, data leaks, or other security breaches.

## 3. Clickjacking (UI Redressing)
- Clickjacking involves tricking users into clicking on invisible or disguised elements, often leading to unintended actions or security compromises.

## 4. Path Traversal
- Path traversal vulnerabilities allow attackers to access files and directories outside of the intended directory structure.
- This can result in unauthorized access to sensitive files.

## 5. Server-side Request Forgery (SSRF) Attacks
- SSRF occurs when an attacker is able to send requests from the vulnerable server to internal resources or other servers.
- This can lead to unauthorized access, data leaks, or system compromise.

## 6. Cross-site Request Forgery (CSRF)
- CSRF tricks a user’s browser into making unwanted requests to a web application where the user is authenticated.
- It can lead to actions being performed without the user's consent.

## 7. Cross-Origin Resource Sharing (CORS)
- CORS vulnerabilities occur when servers improperly configure cross-origin requests, potentially allowing malicious websites to access sensitive data.

## 8. API Testing
- APIs must be rigorously tested to prevent vulnerabilities such as improper authentication, insufficient rate limiting, and data exposure.
- API testing ensures that the backend services are protected from unauthorized access and attacks.

## 9. Web Cache Deception
- Attackers exploit the caching mechanism of web servers to serve malicious content to users by manipulating cache headers and URLs.

## 10. SQL Injection
- SQL injection occurs when an attacker inserts malicious SQL queries into input fields, potentially gaining access to or modifying a database.
- It can result in data leaks, unauthorized access, and even system compromise.

## 11. NoSQL Injection
- Similar to SQL injection but targeting NoSQL databases, NoSQL injection vulnerabilities allow attackers to inject queries into databases like MongoDB, CouchDB, etc.

## 12. Authentication Vulnerabilities
- Weak authentication mechanisms can allow attackers to bypass login controls, access unauthorized resources, or perform actions on behalf of legitimate users.

## 13. WebSockets Vulnerabilities
- WebSockets vulnerabilities can occur if input is not properly sanitized, or if insecure connections or authorization mechanisms are used.
- This can lead to data interception, session hijacking, or remote code execution.
