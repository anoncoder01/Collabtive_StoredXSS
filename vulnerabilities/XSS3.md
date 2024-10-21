Affected Web App: Collabtive in PHP

Version: v3.1

Title: Stored Cross Site Scripting (XSS) vulnerability

Affected Components: File --> /managemilestone.php, Parameter --> name, Action --> add/edit <br>
File --> /admin.php, Parameter --> name, Action --> addpro <br>
name parameter within the files managemilestone.php and admin.php under the actions of add/edit or addpro are vulnerable to stored Cross-Site Scripting

Impact: Cross-Site Scripting (XSS) vulnerability is a serious web security threat. When attackers execute this type of threat by injecting malicious scripts, it can lead to user data being compromised, their account getting hijacked or even malware getting installed on the host machine.

Image: 

![image](https://github.com/user-attachments/assets/533df32a-fc93-4e38-8865-36327d1d2573)

![image](https://github.com/user-attachments/assets/81a1ca0a-6f11-433c-b2c0-1a45d55698ed)

It is important to first create a project in order to be able reproduce the first vulnerability. Following the login to Collabtive application, go to the Administration section and then click on Project Administration. Create a temporary project following the instructions, which will show up under the corresponding customer project administration, as shown in the above image. Note that the customer name has a vulnerability in itself which has been discussed [here] so make sure to include an appropriate name.

Image: 

![image](https://github.com/user-attachments/assets/2d8fd1ee-2ada-482d-b44d-5e98333fe589)

![image](https://github.com/user-attachments/assets/d52b1f80-7edc-4222-bfc5-bc47ae5df019)

Proof of Concept: To reproduce this attack, an attacker can inject a script into the Title field under Messages or Tasks under Customer Administration either while adding messages or while adding tasks respectively for the corresponding project that has been created, as shown in the two figures above, of the Collabtive application. The payload '" onfocus="alert(1)" autofocus="' was successfully accepted, leading to an alert being triggered for the user when the messages and tasks are being viewed under action=system and mode=edited or when the customers created are being viewed or edited under action=showproject & mode=listadded respectively as shown in the two figures below.

Image:


![image](https://github.com/user-attachments/assets/7bfa0b13-2064-4cee-bd53-199b6096a4ad)



Remediation: It is important to update Collabtive by properly sanitizing code variables and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected. 
