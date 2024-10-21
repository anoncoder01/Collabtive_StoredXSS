Affected Web App: Collabtive in PHP

Version: v3.1

Title: Stored Cross Site Scripting (XSS) vulnerability

Affected Components: File --> /admin.php, Parameter --> name, Action --> system <br>
File --> /admin.php, Parameter --> company, contact, Action --> addcust <br>
name parameter within the file admin.php under action system, and company parameter as well as contact parameter within the file admin.php under action addcust are vulnerable to stored Cross-Site Scripting

Impact: Cross-Site Scripting (XSS) vulnerability is a serious web security threat. When attackers execute this type of threat by injecting malicious scripts, it can lead to user data being compromised, their account getting hijacked or even malware getting installed on the host machine.

Image: 

![image](https://github.com/user-attachments/assets/59eb0ae6-928f-4476-b523-2d67dd3f01dd)


![image](https://github.com/user-attachments/assets/03dd7394-6e0e-494d-b5c7-223c2cec7fe5)


Proof of Concept: To reproduce this attack, an attacker can inject a script into the Name field under System Administration or into the Company field or Contact Person field under Customer Administration either while saving the system admin information or while adding new customers (as shown in the two figures above) under the Administration tab of the Collabtive application. The payload '" onfocus="alert(1)" autofocus="' was successfully accepted, leading to an alert being triggered for the user when the system administration is being viewed under action=system and mode=edited or when the customers created are being viewed or edited under action=customers and mode=added respectively as shown in the two figures below.

Image:

![image](https://github.com/user-attachments/assets/842c70c8-a4b5-4cdf-8956-95b31baa1e33)


![image](https://github.com/user-attachments/assets/f65b9800-46c8-449d-94e1-32cbaf923188)


Remediation: It is important to update Collabtive by properly sanitizing code variables and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected. 
