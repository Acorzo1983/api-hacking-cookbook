
# API Attack Techniques

## API Discovery

### Tools and Methods for Discovering Hidden APIs
Uncovering hidden APIs is crucial in understanding the full scope of a target system's surface. Various tools and techniques can be used for this purpose:

#### Using OWASP Amass
**OWASP Amass** performs network mapping and external asset discovery using a variety of techniques including DNS enumeration, scraping web pages, and brute forcing subdomains.

**Example Command:**
```bash
amass enum -d example.com
```
This command will enumerate all subdomains associated with `example.com`, potentially revealing API endpoints hosted on these subdomains.

#### Discovering API Endpoints with Kiterunner
**Kiterunner** is designed to perform rapid content discovery of APIs by attempting requests against known endpoint patterns.

**Example Command:**
```bash
kr scan example.com -w /path/to/apiswordlist
```
This will scan `example.com` using a predefined list of API endpoints stored in `apiswordlist`.

### Active Reconnaissance Techniques
Active scanning techniques involve directly interacting with the API to discover its structure and functions:

#### Crawling APIs with OWASP ZAP
**OWASP ZAP** can automatically discover API endpoints by crawling applications.

**Setup Guide:**
1. Configure ZAP as a proxy for your web traffic.
2. Navigate through the application to generate traffic and let ZAP record the API calls.

## Endpoint Analysis

### Process for Evaluating and Exploiting Endpoints
Evaluating API endpoints involves detailed analysis of each endpoint's response to various inputs.

#### Using Burp Suite for Endpoint Analysis
**Burp Suite** is an integrated platform for attacking web applications, which includes testing for API security.

**Example Use Case:**
- Intercept API requests in Burp Suite.
- Modify parameters to test for SQL injection, parameter tampering, etc.

**Sample Burp Suite Manipulation:**
```http
GET /api/v1/users?user_id=1' OR '1'='1 HTTP/1.1
Host: vulnerable-api.com
```
This manipulated request might reveal if the API endpoint is vulnerable to SQL injection by trying to manipulate the SQL query.

### Security Testing

#### Testing for Information Disclosures
Information disclosures can occur when APIs inadvertently provide more data than they should in error messages or data responses.

**Example Vulnerability Test:**
```http
GET /api/v1/users?user_id=1 HTTP/1.1
Host: vulnerable-api.com
```
If the response includes sensitive data beyond what a regular user should access, the endpoint is considered vulnerable.

#### Business Logic Flaw Identification
Business logic flaws occur when the design of the API allows users to perform actions that should not be possible.

**Example Scenario:**
Suppose an API allows changing user email without adequate security checks, thus:
```http
POST /api/v1/change-email HTTP/1.1
Host: vulnerable-api.com
Content-Type: application/json

{"user_id":"1", "new_email":"attacker@example.com"}
```
Testing this endpoint could reveal flaws like missing authorization checks.

## Summary
This guide outlines essential techniques for discovering and evaluating APIs. By combining tools like OWASP Amass, Kiterunner, and Burp Suite with thoughtful testing strategies, you can uncover and potentially exploit vulnerabilities within API endpoints.

---
