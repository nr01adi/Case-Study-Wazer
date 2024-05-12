# Case Study

## Group Name
Wazer

## Group Members
1. Nik Raeidi Bin Nik Salimi (2013837)
2. Muhammad Haikal Bin Azhari (2014711)

## Assigned Tasks
1. Nik Raeidi Bin Nik Salimi (2013837)
    - Identify, evaluate and prevent of:
      - Hash Disclosure
      - CSRF
      - JS Library
      - HTTPS implementation (TLS/SSL)
      - CSP

2. Muhammad Haikal Bin Azhari (2014711)
    - Identify, evaluate and prevent of:
      - Secured Cookies
      - Server OS and Server-Side Scripting used
      - Information Disclosure
      - Potential XSS
      - Cookie Poisoning

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
![image](https://github.com/nr01adi/Case-Study-Wazer/assets/90669152/aab19e6f-7195-402b-9805-ab515f873b5d)

### <a name="serv"/>a. Server OS and Server-Side Scripting used (Windows or Linux, PHP or ASP.net or JavaScript, etc)
#### Identify: 
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate: 
- Based on the OWASP ZAP scan results for padu.gov.my, no alert for Server OS and Server-Side Scripting used vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to hash disclosure on the website. However it is using CloudWaf server
#### Prevent: 
- Nothing to prevent
### <a name="hash"/> b. Hash Disclosure
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
- Based on the OWASP ZAP scan results for padu.gov.my, no alert for Hash Disclosure vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to hash disclosure on the website.
#### Prevent:
- For this website, since there is no login screen at the momment, the specific concern of hash disclosure may not apply.
### <a name="csrf"/>c. CSRF
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
- The absence of a CSRF alert in the OWASP ZAP scan results for padu.gov.my suggests that no potential vulnerabilities related to Cross-Site Request Forgery were detected during the assessment as there is no authentication at the momment.
#### Prevent:
- No prevention at the momment as no alert appears in the OWASP ZAP scan results.
### <a name="sec"/> d. Secured Cookies
#### Identify:
1. Cookie Without Secure Flag
   - Risk level: low
   - Confidence: medium
   - CWE ID: 614
   - WASC ID: 13
   - Evidence: Set-Cookie: HWWAFSESID  
   - The page involved is at URL: https://padu.gov.my/
2. Cookie No HttpOnly Flag
   - Risk level: low
   - Confidence: medium
   - CWE ID: 1004
   - WASC ID: 13
   - Evidence: Set-Cookie: HWWAFSESID  
   - The page involved is at URL: https://padu.gov.my/
3. Cookie without SameSite Attribute
   - Risk level: low
   - Confidence: medium
   - CWE ID: 1275
   - WASC ID: 13
   - Evidence: Set-Cookie: HWWAFSESID 
   - The page involved is at URL: https://padu.gov.my/
#### Evaluate:
- The Secure attribute for sensitive cookies in HTTPS sessions is not set, which could cause the user agent to send those cookies in plaintext over an HTTP session.
- The HttpOnly flag directs compatible browsers to prevent client-side script from accessing cookies. Including the HttpOnly flag in the Set-Cookie HTTP response header helps mitigate the risk associated with Cross-Site Scripting (XSS) where an attacker's script code might attempt to read the contents of a cookie and exfiltrate information obtained. When set, browsers that support the flag will not reveal the contents of the cookie to a third party via client-side script executed via XSS.
- The SameSite attribute controls how cookies are sent for cross-domain requests. This attribute may have three values: 'Lax', 'Strict', or 'None'. If the 'None' value is used, a website may create a cross-domain POST HTTP request to another website, and the browser automatically adds cookies to this request. This may lead to Cross-Site-Request-Forgery (CSRF) attacks if there are no additional protections in place (such as Anti-CSRF tokens).

#### Prevent:
-   Whenever a cookie contains sensitive information or is a session token, then it should always be passed using an encrypted channel. Ensure that the secure flag is set for cookies containing such sensitive information.
- Ensure that the HttpOnly flag is set for all cookies.
- Ensure that the SameSite attribute is set to either 'lax' or ideally 'strict' for all cookies.

#### Additional Information
- ![image](https://github.com/nr01adi/Case-Study-Wazer/assets/90669152/7cf5508d-ebee-4d8a-ab43-126805c8d421)
- ![image](https://github.com/nr01adi/Case-Study-Wazer/assets/90669152/080a1e02-66c7-41ed-a212-0699c576df36)
- ![image](https://github.com/nr01adi/Case-Study-Wazer/assets/90669152/abb928da-5721-467a-9ab4-b36c98becbe6)

#### References:
- https://cwe.mitre.org/data/definitions/614.html
- https://cwe.mitre.org/data/definitions/1004.html
- https://cwe.mitre.org/data/definitions/1275.html

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
- Based on the OWASP ZAP scan results for padu.gov.my, no alert for JS Library vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to JS Library implementation on the website.
#### Prevent:
- No prevention at the momment as no alert appears in the OWASP ZAP scan results.

### <a name="https"/>g. HTTPS Implementation (TLS/SSL)
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
- Based on the OWASP ZAP scan results for padu.gov.my, no alert for https implementation vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to https implementation on the website.
#### Prevent:
- No prevention at the momment as no alert appears in the OWASP ZAP scan results.
### <a name="coo"/>h. Cookie Poisoning
#### Identify:
- There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
- Based on the OWASP ZAP scan results for padu.gov.my, no alert for Cookie Poisoning vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to Cookie Poisoning on the website.
#### Prevent:
- No prevention at the momment as no alert appears in the OWASP ZAP scan results.
### <a name="pot"/>i. Potential XSS
#### Identify:
  - There is no alert found on OWASP ZAP and no risk level and CWE ID can be identified.
#### Evaluate:
  - Based on the OWASP ZAP scan results for padu.gov.my, no alert for Potential XSS vulnerabilities was found. Since there is no alert, it suggests that OWASP ZAP did not detect any potential issues related to Potential XSS on the website.
#### Prevent:
  - 
### <a name="inf"/>j. Information Disclosure
#### Identify:
- Risk level: informational
- Confidence: low
- CWE ID: 200
- WASC ID: 13
- The page involved is at URL: https://padu.gov.my

#### Evaluate:
There are many different kinds of mistakes that introduce information exposures. The severity of the error can range widely, depending on the context in which the product operates, the type of sensitive information that is revealed, and the benefits it may provide to an attacker. Some kinds of sensitive information include:
   - private, personal information, such as personal messages, financial data, health records, geographic location, or contact details
   - system status and environment, such as the operating system and installed packages
   - business secrets and intellectual property
   - network status and configuration
   - the product's own code or internal state

Information might be sensitive to different parties, each of which may have their own expectations for whether the information should be protected. These parties include:
   - the product's own users
   - people or organizations whose information is created or used by the product, even if they are not direct product users
   - the product's administrators, including the admins of the system(s) and/or networks on which the product operates

This particular information disclosure is that response appears to contain suspicious comments which may help an attacker. Note: Matches made within script blocks or files are against the entire content not only comments.
#### Prevent:
- Remove all comments that return information that may help an attacker and fix any underlying problems they refer to.

#### Reference:
- https://cwe.mitre.org/data/definitions/200.html
  
## Weekly Progress Report
- https://drive.google.com/drive/folders/1l-oRw4g35iqj0GJyuy1DDVjStHPXIfxo?usp=drive_link
