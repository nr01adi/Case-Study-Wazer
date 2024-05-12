# Case Study

## Group Name
Wazer

## Group Members
1. Nik Raeidi Bin Nik Salimi (2013837)
2. Muhammad Haikal Bin Azhari (2014711)

## Assigned Tasks
1. Nik Raeidi Bin Nik Salimi (2013837)
    - Identify, evaluate and prevent of:
      - 
      - 
      - 

2. Muhammad Haikal Bin Azhari (2014711)
    - Identify, evaluate and prevent of:
      - 
      - 
      - 

## Table of Contents
1. [Description](#desc)
2. [Observation Results](#obsv)
    1. [Server OS and Server-Side Scripting used (Windows or Linux, PHP or ASP.net or JavaScript, etc)](#serv)
    2. [Hash Disclosure](#hash)
    3. [CSRF](#csrf)
    4. [Secured Cookies](#sec)
    5. [CSP](#csp)
    6. [JS Library](#jsl)
    7. [HTTPS implementation (TLS/SSL)](#https)
    8. [Cookie Poisoning](#coo)
    9. [Potential XSS](#pot)
    10. [Information Disclosure](#inf)

## <a name="desc"/> Description
Our assigned web application is the Pangkalan Data Utama (PADU) website at https://padu.gov.my/ . In this case study, our group will look into the vulnerabilities of the web application by scanning the website using OWASP ZAP using both the automated scan and manual explore. <br>

The alerts observed are listed on the table of contents and we will also identify the level of risk for each alert and additional information on the classification of threats (CWE or CVE).
## <a name="obsv"/>Observation Results
### <a name="serv"/>a. Server OS and Server-Side Scripting used (Windows or Linux, PHP or ASP.net or JavaScript, etc)
#### Identify:
- 
#### Evaluate:
- 
#### Prevent:
- 
### <a name="hash"/> b. Hash Disclosure
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
- Based on the OWASP ZAP scan results for padu.gov.my, no alert for Hash Disclosure vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to hash disclosure on the website.
#### Prevent:
- 
### <a name="csrf"/>c. CSRF
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
-
#### Prevent:
- 
### <a name="sec"/> d. Secured Cookies
#### Identify:
- Cookie Without Secure Flag
- Risk level: low
- Confidence: medium
- CWE ID 614 
#### Evaluate:
-
#### Prevent:
- 
### <a name="csp"/>e. CSP
#### Identify:
- Risk level: medium
- Confidence: high
- CWE ID: 693
- The page involved is at URL: https://www.padu.gov.my/sitemap.xml
#### Evaluate:
- CSP is a security feature that helps prevent cross-site scripting (XSS) attacks by specifying which content sources are allowed to be loaded on a web page. It restricts the execution of scripts, styles, and other resources to trusted origins.
- A medium risk level indicates that the vulnerability could potentially be exploited under certain conditions. While it’s not as severe as a high-risk issue, it still requires attention and mitigation.
- The high confidence level suggests that the alert is likely accurate and not a false positive. ZAP is confident in its findings.
- The Common Weakness Enumeration (CWE) ID 693 corresponds to “Protection Mechanism Failure.” In the context of CSP, this means that the CSP implementation on the specified page might have issues.
#### Prevent:
- Implement a Content Security Policy (CSP): Ensure that a robust CSP is properly configured for the website. The CSP should specify trusted sources for scripts, stylesheets, fonts, images, and other resources. It should also restrict the use of inline scripts and styles, as well as unsafe dynamic execution methods such as eval(). Implementing a strict CSP helps to mitigate the risk of XSS attacks and other injection vulnerabilities.
- Regularly review and update CSP directives: Keep the CSP directives up-to-date by periodically reviewing and refining them based on changes to the website's structure, content, and functionality. This includes adding or removing allowed sources as needed and adjusting the CSP directives to accommodate new features or third-party integrations.
- Test CSP configurations: Regularly test the effectiveness of the CSP configurations using security tools like OWASP ZAP, as done in the initial vulnerability assessment. Automated and manual testing can help identify misconfigurations or weaknesses in the CSP policy that may expose the website to vulnerabilities.

### <a name="jsl"/>f. JS Library
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
-
#### Prevent:
- 

### <a name="https"/>g. HTTPS Implementation (TLS/SSL)
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
- Based on the OWASP ZAP scan results for padu.gov.my, no alert for https implementation vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to https implementation on the website.
#### Prevent:
- 
### <a name="coo"/>h. Cookie Poisoning
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
- 
#### Prevent:
- 
### <a name="pot"/>i. Potential XSS
#### Identify:
  - There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
  - 
#### Prevent:
  - 
### <a name="inf"/>j. Information Disclosure
#### Identify:
- Risk level: informational
- CWE ID: 200
- The page involved is at URL: https://www.
- Evidence:
#### Evaluate:
-
#### Prevent:
- 

Reference:
- https://
- https://
- https://
  
## Weekly Progress Report
