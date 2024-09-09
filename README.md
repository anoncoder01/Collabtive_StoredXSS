Affected Web App: Collabtive in PHP

Version: v3.1

Title: Stored Cross Site Scripting (XSS) vulnerability

Affected Component: /admin.php <br>
name parameter under action=system as well as company/contact parameters under action=addcust within admin.php file is vulnerable to stored Cross-Site Scripting

Impact: Cross-Site Scripting (XSS) vulnerability is a serious web security threat. When attackers execute this type of threat by injecting malicious scripts, it can lead to user data being compromised, their account getting hijacked or even malware getting installed on the host machine.

Image: 


<br>


Proof of Concept: To reproduce this attack, an attacker can inject a script into the Name field under System Administration, Company field or Contact field under Customer Administration of the application. The payload '" onfocus="alert(1)" autofocus="' was successfully accepted in each of the above fields, leading to an alert being triggered for the user after saving the system state or customer information respectively. Please not that the full payload " onfocus="alert(1)" autofocus=" needs to be used when testing the XSS.

Image:

<br>


Remediation: It is important to update Collabtive by properly sanitizing code variables and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected. 
