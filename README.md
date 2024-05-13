# INFO 4345 Case Study - Indah Water Konsortium (IWK)

## Group Name: Indigo Hat

Welcome to the GitHub repository for the INFO 4345 case study on Indah Water Konsortium (IWK). This document contains the detailed breakdown of contributions from each team member.

### Group Members:
- Bashir Md Monjur (2028113)
- Wan Mohd Nazim Bin Wan Muhamad Saidin (2114261)
- Faizal Akhtar Bin Azhar (2124565) - Group Leader

### Work Distribution:

| Name                            | Matric Number | Assigned Tasks                                            | Participation |
|---------------------------------|---------------|-----------------------------------------------------------|---------------|
| Bashir Md Monjur               | 2028113       | Manual explore, proxy setup, report, identify vulnerabilities  | 100%          |
| Wan Mohd Nazim Bin Wan Muhamad Saidin | 2114261       | Automatic scan, report, evaluate vulnerabilities             | 100%          |
| Faizal Akhtar Bin Azhar        | 2124565       | Group coordination, manual explore, group work, prevent vulnerabilities, README.md file, documentation | 100%          |

### Table of Contents:
- [Brief Description](#brief-description)
- [Identify Vulnerabilities](#identify-vulnerabilities)
- [Evaluate Vulnerabilities](#evaluate-vulnerabilities)
- [Prevent Vulnerabilities](#prevent-vulnerabilities)
- [References](#references)

## Brief Description:
The Indah Water Konsortium (IWK) website serves as the online platform for Malaysia's national sewerage company. Owned by the Minister of Finance Incorporated, IWK is tasked with the development and maintenance of a modern and efficient sewerage system for all Malaysians.

Established in 1994, IWK plays a crucial role in managing the nation's sewerage services, ensuring that wastewater is treated before being discharged into rivers. This contributes to preserving Malaysia's water resources, protecting public health, and maintaining a cleaner and safer environment.

The objectives of this case study are to identify, evaluate, and prevent vulnerabilities present within the IWK website, using the OWASP ZAP tool and other relevant techniques. Through comprehensive analysis and recommendations, the aim is to enhance the security and integrity of the IWK online platform, safeguarding it against potential threats and ensuring uninterrupted service delivery to the public.

- **Server:** Apache (Educated Guess)
- **Operating System:** Linux (Educated Guess)
  
*Note: There are no explicit data or information that we can get to confirm the Server and Operating System that IWK is using. This educated guess hinted from the HTTP Response Headers in the generated ZAP scan report.*

## Identify Vulnerabilities:
The security analysis performed using the OWASP ZAP tool revealed several vulnerabilities within the IWK website, categorized by their risk level and confidence rating. Below is a summary of the key findings:

### Medium Risk:
- **CSP: Wildcard Directive**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: Content Security Policy (CSP) implements a wildcard directive, which can allow malicious content to be executed.
- **CSP: script-src unsafe-inline**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: CSP policy allows unsafe inline scripts, increasing the risk of XSS attacks.
- **CSP: style-src unsafe-inline**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: Inline styles are enabled, which can be exploited for malicious purposes.
- **Cross-Domain Misconfiguration**
  - **URL**: `https://fonts.googleapis.com/css?family=Roboto:100,400,500`
  - **Details**: Misconfigured CORS policy that could be exploited to leak information.
- **Secure Pages Include Mixed Content**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: Mixed content found, where secure pages include resources from insecure sources.
- **Vulnerable JS Library**
  - **URL**: `https://www.iwk.com.my/compiledjs/jquery-1-9631852.js`
  - **Details**: Use of an outdated JavaScript library with known vulnerabilities.
- **Absence of Anti-CSRF Tokens**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: No CSRF tokens were found, which can lead to cross-site request forgery attacks.

### Low Risk:
- **Strict-Transport-Security Header Not Set**
  - **URL**: `https://www.statcounter.com/counter/counter.js`
  - **Details**: The Strict-Transport-Security header is not set, which can make the site more susceptible to man-in-the-middle attacks.
- **Server Leaks Version Information via "Server" HTTP Response Header Field**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: Server version information is exposed, which could help attackers identify server vulnerabilities.
- **Cookies Issues**
  - **Details**: Several cookies-related issues were identified, including cookies without HttpOnly flags, cookies without Secure flags, and cookies without SameSite attributes, leading to potential security vulnerabilities.
- **Cross-Domain JavaScript Source File Inclusion**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: Inclusion of cross-domain JavaScript files, which can potentially include malicious sources.

### Informational:
- **Modern Web Application**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: The site is identified as a modern web application.
- **Session Management Response Identified**
  - **URL**: `https://www.iwk.com.my`
  - **Details**: Standard session management is in use.
- **Information Disclosure - Suspicious Comments**
  - **URL**: `https://www.iwk.com.my/compiledjs/jquery-1-9631852.js`
  - **Details**: Suspicious comments found in JavaScript code, which could disclose sensitive information.

This comprehensive analysis helps us to understand the security posture of the IWK website and guide the necessary steps to mitigate these vulnerabilities.

## Evaluate Vulnerabilities:
Based on the security analysis report of the IWK website, several vulnerabilities have been identified, categorized by their risk level. Here is an evaluation of the vulnerabilities:

### Medium Risk:
1. **CSP: Wildcard Directive:** This vulnerability indicates that the Content Security Policy (CSP) implemented on the website allows for a wildcard directive, which can potentially enable the execution of malicious content. It is recommended to restrict the CSP directives to specific trusted sources.

2. **CSP: script-src unsafe-inline:** The CSP policy allows the execution of unsafe inline scripts, which increases the risk of cross-site scripting (XSS) attacks. It is advisable to modify the CSP policy to disallow unsafe inline scripts and instead rely on external script sources.
 
3. **CSP: style-src unsafe-inline:** Similar to the previous vulnerability, allowing unsafe inline styles can be exploited for malicious purposes. It is recommended to update the CSP policy to disallow unsafe inline styles.

4. **Cross-Domain Misconfiguration:** This vulnerability relates to a misconfigured Cross-Origin Resource Sharing (CORS) policy on the fonts.googleapis.com domain. Exploiting this misconfiguration could potentially lead to information leakage. It is important to properly configure CORS to restrict cross-domain access.
   
5. **Secure Pages Include Mixed Content:** Mixed content refers to a situation where secure (HTTPS) pages include resources from insecure (HTTP) sources. This can weaken the security of the website and make it vulnerable to attacks. It is advised to ensure that all resources are loaded securely over HTTPS.

6. **Vulnerable JS Library:** The usage of an outdated JavaScript library (jquery-1-9631852.js) with known vulnerabilities poses a risk. It is crucial to update to the latest version of the library or find alternative secure solutions.

7. **Absence of Anti-CSRF Tokens:** The absence of Cross-Site Request Forgery (CSRF) tokens leaves the website susceptible to CSRF attacks. It is essential to implement anti-CSRF measures such as generating and validating tokens to protect against CSRF attacks.

### Low Risk:
1. **Strict-Transport-Security Header Not Set:** The absence of the Strict-Transport-Security (HSTS) header makes the site more vulnerable to man-in-the-middle attacks. Implementing the HSTS header helps ensure secure communication over HTTPS.

2. **Server Leaks Version Information via "Server" HTTP Response Header Field:** Exposing server version information in the response headers can aid attackers in identifying potential vulnerabilities. It is recommended to configure the server to suppress or obfuscate this information.

3. **Cookies Issues:** The report identifies several issues with cookies, including missing HttpOnly flags, missing Secure flags, and missing SameSite attributes. These issues can lead to security vulnerabilities. It is important to properly configure cookies with the appropriate flags and attributes to enhance security.

4. **Cross-Domain JavaScript Source File Inclusion:** Including JavaScript files from cross-domains can introduce potential security risks. It is advisable to avoid including JavaScript files from untrusted or external sources.

### Informational:
1. **Modern Web Application:** The report identifies the website as a modern web application, which indicates the use of contemporary web technologies and frameworks.

2. **Session Management Response Identified:** The report indicates that standard session management mechanisms are in use on the website.

3. **Information Disclosure - Suspicious Comments:** Suspicious comments found in the JavaScript code could potentially reveal sensitive information. It is recommended to review and remove any suspicious or sensitive comments from the codebase.

Overall, the vulnerabilities identified in the report highlight potential security risks that should be addressed to enhance the security posture of the IWK website.

## Prevent Vulnerabilities:
The security analysis performed using the OWASP ZAP tool revealed several vulnerabilities within the IWK website, categorized by their risk level and confidence rating. Below is a summary of the key findings:

### Medium Risk:
1. **CSP: Wildcard Directive**
   - **Recommendation:** Update the Content Security Policy (CSP) to specify allowed sources explicitly, avoiding the use of wildcard directives. Implement a strict CSP policy that only allows trusted sources for scripts, styles, and other resources.
   
2. **CSP: script-src unsafe-inline**
   - **Recommendation:** Remove the allowance for inline scripts in the CSP policy. Instead, refactor the code to use external script files and implement nonce-based CSP to allow specific inline scripts when necessary.

3. **CSP: style-src unsafe-inline**
   - **Recommendation:** Similar to scripts, eliminate the use of inline styles and rely on external style sheets. Implementing nonce-based CSP can provide a mechanism for allowing specific inline styles securely.

4. **Cross-Domain Misconfiguration**
   - **Recommendation:** Configure Cross-Origin Resource Sharing (CORS) headers to restrict access to resources only from trusted domains. Use the `Access-Control-Allow-Origin` header to specify allowed origins explicitly.

5. **Secure Pages Include Mixed Content**
   - **Recommendation:** Ensure that all resources loaded on secure pages (HTTPS) are also served securely. Update the website to use HTTPS for all resources, including external scripts, stylesheets, and images.

6. **Vulnerable JS Library**
   - **Recommendation:** Update the jQuery library to the latest secure version or consider using a more secure alternative. Regularly monitor for security updates and apply patches promptly to mitigate known vulnerabilities.

7. **Absence of Anti-CSRF Tokens**
   - **Recommendation:** Implement anti-CSRF tokens in web forms to prevent cross-site request forgery attacks. Include unique tokens with each form submission and validate them on the server-side to ensure requests originate from legitimate users.

### Low Risk:
1. **Strict-Transport-Security Header Not Set**
   - **Recommendation:** Enable HTTP Strict Transport Security (HSTS) by configuring the server to include the `Strict-Transport-Security` header in HTTP responses. Set the `max-age` directive to a sufficient duration to enforce HTTPS for all subsequent requests.

2. **Server Leaks Version Information via "Server" HTTP Response Header Field**
   - **Recommendation:** Configure the server to suppress or obfuscate version information from the HTTP response headers. Minimize exposure of server details to reduce the risk of targeted attacks.

3. **Cookies Issues**
   - **Recommendation:** Address cookies-related issues by setting appropriate flags such as HttpOnly, Secure, and SameSite attributes based on the sensitivity of the cookies. Ensure that session cookies are secure and transmitted over HTTPS only.

4. **Cross-Domain JavaScript Source File Inclusion**
   - **Recommendation:** Review and validate the inclusion of cross-domain JavaScript files. Whenever possible, host JavaScript files locally or from trusted CDNs to reduce the risk of tampering or injection attacks.

### Informational:
1. **Modern Web Application**
   - **Recommendation:** Continuously update the website's technology stack and adhere to modern security best practices to maintain the security posture of the application.

2. **Session Management Response Identified**
   - **Recommendation:** Implement secure session management practices, including session expiration, session regeneration, and secure storage of session identifiers to prevent session hijacking and unauthorized access.

3. **Information Disclosure - Suspicious Comments**
   - **Recommendation:** Remove or obfuscate any suspicious comments or sensitive information present in JavaScript files. Minimize the exposure of internal code comments and configuration details to external users.

These recommendations aim to address the identified vulnerabilities and strengthen the security posture of the Indah Water Konsortium (IWK) website. It's essential to implement these preventive measures proactively and regularly assess the website's security to mitigate potential risks effectively.


## References

1. **OWASP ZAP Official Documentation:** Provides detailed information about OWASP ZAP, including user guides, tutorials, and technical documentation.
   - [OWASP ZAP Documentation](https://www.zaproxy.org/docs/)

2. [Detailed ZAP Scanning Report - MANUAL EXPLORE](https://drive.google.com/file/d/1qiC6JscSML1rPOu_M7OEpNdwWsGeF6FQ/view?usp=sharing)
3. [Detailed ZAP Scanning Report - AUTOMATIC SCAN](https://drive.google.com/file/d/1tNKfsFedavBK5MpxAY5OYgTEtEjhGYJw/view?usp=sharing)
4. [Weekly Progress Report](https://drive.google.com/file/d/1_Uwadp-VyH9iY3AVeReqLr_6lJfBuvqM/view?usp=sharing)
