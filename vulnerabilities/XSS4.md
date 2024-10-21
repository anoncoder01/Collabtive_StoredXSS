Affected Web App: Collabtive in PHP

Version: v3.1

Title: Stored Cross Site Scripting (XSS) vulnerability

Affected Components: File --> /tasklist.php, Parameter --> name, Action --> add/edit <br>
File --> /admin.php, Parameter --> name, Action --> adduser/edituser <br>
name parameter within the files tasklist.php and admin.php under the actions of add/edit and adduser/edituser respectively are vulnerable to stored Cross-Site Scripting

Impact: Cross-Site Scripting (XSS) vulnerability is a serious web security threat. When attackers execute this type of threat by injecting malicious scripts, it can lead to user data being compromised, their account getting hijacked or even malware getting installed on the host machine.

Image: 

![image](https://github.com/user-attachments/assets/8fe5b99a-ac1e-4dac-b9c5-be5b1b3e0b81)


It is important to first create a project in order to be able reproduce the first vulnerability. Following the login to Collabtive application, go to the Administration section and then click on Project Administration. Create a temporary project following the instructions, which will show up under the corresponding customer project administration, as shown in the above image. Note that the customer name has a vulnerability in itself which has been discussed [here] so make sure to include an appropriate name.

Image: 

![image](https://github.com/user-attachments/assets/9e033e99-45fb-4428-8dd0-4ca0a2cba68e)

![image](https://github.com/user-attachments/assets/0d117230-bf9c-447d-8db8-c8b25b15bd99)


Proof of Concept: To reproduce this attack, an attacker can inject a script into the Name field under Project Administration while adding a new tasklist or the Name field under User Administration either when adding or editing a new user for the corresponding project that has been created, as shown in the two figures above, of the Collabtive application. The payload '" onfocus="alert(1)" autofocus="' was successfully accepted, leading to an alert being triggered for the user when the created tasklist is being viewed or when the list of users is being viewed under action=projects in the two figures below.

Image:

![image](https://github.com/user-attachments/assets/68f679b2-ae8e-4373-86dc-bed9f3ba0a7b)

![image](https://github.com/user-attachments/assets/ff029607-5598-4aa4-9a60-260711311f82)



Remediation: It is important to update Collabtive by properly sanitizing code variables and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected. 
