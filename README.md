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
[Provide an evaluation of the vulnerabilities identified.]

## Prevent Vulnerabilities:
[Recommendations and measures to prevent the identified vulnerabilities.]

## References

1. **OWASP ZAP Official Documentation:** Provides detailed information about OWASP ZAP, including user guides, tutorials, and technical documentation.
   - [OWASP ZAP Documentation](https://www.zaproxy.org/docs/)

2. [Detailed ZAP Scanning Report - MANUAL EXPLORE](https://drive.google.com/file/d/1qiC6JscSML1rPOu_M7OEpNdwWsGeF6FQ/view?usp=sharing)
3. [Detailed ZAP Scanning Report - AUTOMATIC SCANNING](https://drive.google.com/file/d/1tNKfsFedavBK5MpxAY5OYgTEtEjhGYJw/view?usp=sharing)
