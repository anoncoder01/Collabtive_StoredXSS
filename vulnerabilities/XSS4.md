Affected Web App: Collabtive in PHP

Version: v3.1

Title: Stored Cross Site Scripting (XSS) vulnerability

Affected Components: File --> /managemilestone.php, Parameter --> name, Action --> add/edit <br>
File --> /admin.php, Parameter --> name, Action --> addpro <br>
name parameter within the files managemilestone.php and admin.php under the actions of add/edit or addpro are vulnerable to stored Cross-Site Scripting

Impact: Cross-Site Scripting (XSS) vulnerability is a serious web security threat. When attackers execute this type of threat by injecting malicious scripts, it can lead to user data being compromised, their account getting hijacked or even malware getting installed on the host machine.

Image: 



It is important to first create a project in order to be able reproduce the first vulnerability. Following the login to Collabtive application, go to the Administration section and then click on Project Administration. Create a temporary project following the instructions, which will show up under the corresponding customer project administration, as shown in the above image. Note that the customer name has a vulnerability in itself which has been discussed [here] so make sure to include an appropriate name.

Image: 



Proof of Concept: To reproduce this attack, an attacker can inject a script into the Name field under Project Administration while adding a new project or the Name field under Milestone when adding/editing a milestone for the corresponding project that has been created, as shown in the two figures above, of the Collabtive application. The payload '" onfocus="alert(1)" autofocus="' was successfully accepted, leading to an alert being triggered for the user when the created milestone is being viewed or when the created project is being viewed under action=projects in the two figures below.

Image:





Remediation: It is important to update Collabtive by properly sanitizing code variables and including restrictions for special characters so that malicious input such as the one showed in the example cannot be injected. 
