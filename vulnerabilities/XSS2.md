Affected Web App: Collabtive in PHP

Version: v3.1

Title: Stored Cross Site Scripting (XSS) vulnerability

Affected Components: File --> /managemessage.php, Parameter --> title, Action --> add <br>
File --> /managetask.php, Parameter --> title, Action --> editform <br>
title parameter within the files managemessage.php and managetask.php under the actions of add or editform are vulnerable to stored Cross-Site Scripting

Impact: Cross-Site Scripting (XSS) vulnerability is a serious web security threat. When attackers execute this type of threat by injecting malicious scripts, it can lead to user data being compromised, their account getting hijacked or even malware getting installed on the host machine.

Image: 
![image](https://github.com/user-attachments/assets/81a1ca0a-6f11-433c-b2c0-1a45d55698ed)

It is important to first create a project in order to be able reproduce this vulnerability. Following the login to Collabtive application, go to the Administration section and then click on Project Administration. Create a temporary project following the instructions, which will show up under the corresponding customer project administration, as shown in the above image. Note that the customer name has a vulnerability in itself which has been discussed [here] so make sure to include an appropriate name.





Proof of Concept: To reproduce this attack, an attacker can inject a script into the Name field under System Administration or into the Company field or Contact Person field under Customer Administration either while saving the system admin information or while adding new customers (as shown in the two figures above) under the Administration tab of the Collabtive application. The payload '" onfocus="alert(1)" autofocus="' was successfully accepted, leading to an alert being triggered for the user when the system administration is being viewed under action=system and mode=edited or when the customers created are being viewed or edited under action=customers and mode=added respectively as shown in the two figures below.

Image:

![image](https://github.com/user-attachments/assets/842c70c8-a4b5-4cdf-8956-95b31baa1e33)


![image](https://github.com/user-attachments/assets/f65b9800-46c8-449d-94e1-32cbaf923188)


Remediation: It is important to update Collabtive by properly sanitizing code variables and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected. 
