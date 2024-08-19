Broken Access Control vulnerability is a highly dangerous bug that can let attackers to get access to modify or delete data illegally. Not checking the access control or a horrible design in the logic of an application could cause this vulnerability. It includes many sub topics and the most important one is IDOR.

#### How to find broken access control vulnerabilities
* Map the application : probe all pages of a web application and check the user inputs.
* Understand how access control is implemented for each privilege level.
* Manipulating parameters that are potentially used to make access control decisions in the back-end.
* Automate testing extensions like Authorize in burp suite.


#### Some notes
* manipulate URL to find admin panel

* while submitting a form in a web page check if you can manipulate inputs or add more inputs plus related values to see whether target has implemented the access controls or not. you can manipulate it both in html source using inspector or in a HTTP request body using JSON.

* Find session of an admin and replacing session ID of a regular user with an privileged user.

*  Manipulate URL to access other users using id parameter. example : `domain.com/profile?id=x`

* In some web applications you can see the detail data about someone (writer, vendor) by clicking on their link. it is possible that their ID is displayed in HTTP request body.

* It is possible information leaks in redirect requests.

