



# **Step-by-Step Bug Bounty Hunting Process**

### **1. Information Gathering / Reconnaissance**

Recon is the **first and most important step** in any bug bounty hunting process. You want to gather as much information about the website as possible to understand its structure, services, and points of entry.

#### **Key Goals**:
- **Identify subdomains**
- **Learn about technologies used**
- **Gather DNS information**
- **Find open ports or services**

#### **Tools & Techniques**:

1. **Subdomain Discovery**:
   - **Tools**: 
     - **Sublist3r**: Quick subdomain enumeration tool that uses search engines, APIs, and DNS records.
     - **Amass**: Comprehensive tool that performs subdomain discovery and mapping of the infrastructure.
     - **Subfinder**: Fast tool for passive subdomain enumeration.
     - **Findomain**: Another fast tool for subdomain enumeration.
   - **What to Do**: Run these tools to get a list of subdomains like `blog.example.com`, `api.example.com`, etc.
     ```bash
     sublist3r -d example.com
     amass enum -d example.com
     subfinder -d example.com
     findomain -t example.com
     ```

2. **DNS & WHOIS Information**:
   - **Tools**:
     - **DNSdumpster**: A free online tool for finding subdomains and DNS records.
     - **SecurityTrails**: Offers detailed historical data on DNS records and subdomains.
     - **whois**: To check domain registration information (who owns the domain, contact details, etc.).
   - **What to Do**: Look for records like MX (mail exchange), TXT (text), and A (address) records. Also, check for misconfigurations or hidden subdomains.

3. **Technology Stack Identification**:
   - **Tools**:
     - **Wappalyzer**: Browser extension that identifies technologies used on a website (like CMS, JavaScript frameworks, etc.).
     - **BuiltWith**: Another tool for finding the technology stack used by the website.
   - **What to Do**: Scan the website to identify the CMS (WordPress, Joomla, etc.), JavaScript libraries, web servers, and backend technologies.

4. **Port Scanning**:
   - **Tools**:
     - **Nmap**: For port scanning and discovering open ports on the website.
   - **What to Do**: Identify open ports on the target domain and subdomains, which might lead to additional attack surfaces.
     ```bash
     nmap -p- example.com
     ```

---

### **2. Vulnerability Scanning**

Once you’ve gathered initial reconnaissance information, you’ll move on to the **automated scanning** phase. This is where you use specialized tools to check for common vulnerabilities on the website.

#### **Key Goals**:
- **Find common vulnerabilities** (XSS, SQL injection, etc.)
- **Automate scanning for known vulnerabilities**
  
#### **Tools & Techniques**:

1. **Automated Vulnerability Scanners**:
   - **Tools**:
     - **OWASP ZAP**: An open-source tool for finding security vulnerabilities in web applications.
     - **Burp Suite** (Free or Pro): A powerful suite for web application security testing. It includes a scanner for common vulnerabilities.
   - **What to Do**: Run an initial scan to look for common web vulnerabilities such as Cross-Site Scripting (XSS), SQL injection, security misconfigurations, etc.
     - In Burp Suite: Use the **Active Scan** or **Spider** features.
     - In ZAP: Use the **Automated Scan** or **Passive Scan** options.

2. **Crawling & Mapping the Site**:
   - **Tools**:
     - **Burp Suite**: Use the **Spider** tool to crawl the site and map out all the available endpoints.
     - **OWASP ZAP**: Use **ZAP's Spider** tool to discover URLs and endpoints.
     - **Gobuster**: A fast directory and file brute-forcing tool, useful for finding hidden directories or files.
   - **What to Do**: Crawl through the website, logging all pages, parameters, and endpoints. Identify hidden or obscure pages that might have vulnerabilities.

---

### **3. Manual Testing (Deep Dive)**

Automated tools can only get you so far. **Manual testing** is crucial for identifying business logic vulnerabilities, complex flaws, and hidden attack vectors that tools can’t catch.

#### **Key Goals**:
- **Test parameters** (URL, headers, cookies, etc.)
- **Identify logic flaws** or hidden functionality
- **Verify automated findings** (e.g., XSS, SQLi)

#### **Tools & Techniques**:

1. **Testing for Input Validation (XSS, SQLi, Command Injection)**:
   - **Tools**:
     - **Burp Suite**: Manually tamper with requests (using the **Intruder** tool) to test for XSS or SQL injection.
     - **OWASP ZAP**: Use the **Request Editor** to modify HTTP requests.
   - **What to Do**: Test inputs for:
     - **XSS (Cross-Site Scripting)**: Try injecting JavaScript code into forms or URL parameters.
     - **SQL Injection**: Use payloads like `' OR 1=1 --` in form fields or URL parameters.
     - **Command Injection**: Test for shell command injections in parameters.
   
2. **Test Authentication & Session Management**:
   - **What to Do**:
     - Check for weak password policies (e.g., `admin:admin`).
     - Test for **Session Fixation** or **Session Hijacking** vulnerabilities.
     - Test whether the website is vulnerable to **Broken Authentication** (e.g., by guessing weak credentials or brute-forcing login endpoints).

3. **Test for CSRF (Cross-Site Request Forgery)**:
   - **Tools**:
     - **Burp Suite**: Use the **CSRF PoC Generator** to check for CSRF vulnerabilities.
     - **Manual Testing**: Look for forms or actions that don’t require authentication to trigger a sensitive action.
   - **What to Do**: Check whether state-changing requests (like changing an account password or transferring funds) can be triggered without proper validation.

4. **Test for Access Control Issues**:
   - **What to Do**: Try accessing resources that should be restricted by using different HTTP methods or unauthorized accounts. For example, try accessing `/admin` or `/user/profile` endpoints by changing the URL parameters or using different user roles.

---

### **4. Reporting & Submission**

Once you’ve found and validated a vulnerability, it’s time to **report the issue** responsibly.

#### **Key Goals**:
- **Document vulnerabilities** clearly and concisely.
- **Provide PoC (Proof of Concept)** for reproducibility.
- **Follow responsible disclosure practices**.

#### **Steps**:
1. **Write a Clear Report**:
   - **Title**: Clear and descriptive title of the bug (e.g., "Stored XSS in the login form").
   - **Description**: Describe the vulnerability, how you discovered it, and why it’s critical.
   - **Steps to Reproduce**: Detailed steps (screenshots or video) showing how to reproduce the issue.
   - **Impact**: Explain what an attacker can do with this vulnerability (e.g., steal user data, escalate privileges).
   - **Proof of Concept (PoC)**: Provide any exploit code or payloads that demonstrate the issue.
   - **Fix Recommendations**: Suggest how to mitigate the issue (e.g., input validation, escaping user inputs).

2. **Submit to Bug Bounty Platform**:
   - For platforms like **HackerOne**, **Bugcrowd**, **Open Bug Bounty**, or **Synack**, follow their submission guidelines carefully. Most platforms have a **responsible disclosure process** where you submit the bug privately and wait for the website owner to acknowledge it.

3. **Communicate Effectively**:
   - Be polite, professional, and clear when submitting your report.
   - Be patient and allow the team time to verify and fix the issue.

---

## **Tools Summary**:

1. **Reconnaissance**:
   - Sublist3r, Amass, Subfinder, DNSdumpster, Wappalyzer, BuiltWith, Nmap
2. **Vulnerability Scanning**:
   - Burp Suite, OWASP ZAP, Gobuster
3. **Manual Testing**:
   - Burp Suite (Intruder, Repeater), OWASP ZAP, Proxy tools, SQLmap (for SQLi)
4. **Reporting**:
   - Bug bounty platforms (HackerOne, Bugcrowd, Open Bug Bounty), Markdown/HTML for PoCs

---

