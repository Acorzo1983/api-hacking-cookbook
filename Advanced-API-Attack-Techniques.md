
# Advanced API Attack Techniques

## Evasive Techniques

### Overview
Evasive techniques in API hacking are designed to bypass or fool security measures such as Web Application Firewalls (WAFs) and rate limiting controls. These techniques allow an attacker to operate under the radar, extending the duration and depth of their penetration testing without triggering alarms.

### Techniques to Avoid Detection
- **IP Rotation and Spoofing**: Changing the IP address from which the requests originate can help evade IP-based blocking and rate limiting. Using tools like VPNs or proxy networks like Tor can be effective.
- **User-Agent Randomization**: Switching between different user agents can prevent security systems from recognizing a pattern in the requests.
- **Advanced Request Tweaking**: Modifying request headers, using string terminators or URL encoding, and strategically crafting payloads to bypass filters or WAF rules.

**Example Using Advanced Request Tweaking**:
\`\`\`http
POST /api/updateProfile HTTP/1.1
Host: example.com
Content-Type: application/json

{"username":"admin\0", "data":"new data"}
\`\`\`
This payload uses a null byte to attempt to terminate input processing prematurely, potentially bypassing security filters.

### Automating Evasion with Burp Suite
Burp Suite can be configured to automate evasive attacks, systematically applying techniques like encoding payloads and rotating user agents to simulate a wide range of attack vectors.

## Rate Limit Testing

### Importance of Rate Limit Testing
Rate limit testing is crucial for identifying how an API enforces usage limits and how these limits can be bypassed, which is essential for understanding API resilience against denial-of-service attacks and other abuse scenarios.

### Methods to Test Rate Limits
- **Distributed Testing**: Utilizing multiple machines or cloud-based services to simulate requests from various sources can test the robustness of rate limits.
- **Manipulation of Rate Limiting Headers**: Modifying HTTP headers such as \`X-Forwarded-For\` to simulate requests from different IP addresses.

**Example of Manipulating Rate Limiting Headers**:
\`\`\`http
GET /api/resource HTTP/1.1
Host: target.com
X-Forwarded-For: 192.168.1.1
\`\`\`
This request uses the \`X-Forwarded-For\` header to simulate coming from a different IP address, potentially bypassing IP-based rate limiting.

**Path Bypass Example**:
Some APIs may not enforce rate limits uniformly across all endpoints or paths. By slightly modifying the endpoint path, an attacker might bypass the rate limit.
\`\`\`http
POST /api/resource%00
\`\`\`
Using encoding or appending characters like \`%00\` (null byte) can help test how different paths affect rate limiting.

### Conclusion

Advanced API attack techniques that focus on evasion and sophisticated rate limit testing are critical for deep penetration testing. These methods ensure that testers can thoroughly evaluate the security measures of an API without prematurely ending their assessment due to detection or rate limiting.
