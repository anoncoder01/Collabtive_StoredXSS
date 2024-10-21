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

Image: 
![image](https://github.com/user-attachments/assets/a615c3e2-f8e3-4969-8b7e-929bb763ffba)

![image](https://github.com/user-attachments/assets/c9abe68b-ae6d-4ec9-a9b0-e05fe5e7af20)
![image](https://github.com/user-attachments/assets/23d9d492-252d-4c0b-9d74-09ad2176ef3c)


Proof of Concept: To reproduce this attack, an attacker can inject a script into the Title field under Messages or Tasks under Customer Administration either while adding messages or while adding tasks respectively for the corresponding project that has been created, as shown in the two figures above, of the Collabtive application. The payload '" onfocus="alert(1)" autofocus="' was successfully accepted, leading to an alert being triggered for the user when the messages and tasks are being viewed under action=system and mode=edited or when the customers created are being viewed or edited under action=showproject & mode=listadded respectively as shown in the two figures below.

Image:

![image](https://github.com/user-attachments/assets/0b06c6de-1267-42fc-8276-0fb8020d0bb5)
![image](https://github.com/user-attachments/assets/d58fb16b-b5fb-47bd-a1a8-7f62d3b2e2e2)



Remediation: It is important to update Collabtive by properly sanitizing code variables and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected. 
