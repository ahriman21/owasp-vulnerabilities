Directory traversal is a vulnerability that allows an attacker to read files on the server that is running the application.

### Finding directory traversal and exploiting
* manually testing URL like `../` or `http://example.com/view?file=../../etc/passwd` or `/etc/passwd` or `....//....//etc/passwd`.

* bypass start of path validation, for instance instead of `/etc/passwd` you can bypass it via entering `/var/www/images/../../../etc/passwd`.

* using null byte in the path : using the null byte character before the name of file in the url. the null byte is `%00` which goes before file name. example :  
	`http://example.com/view?file=../../../etc/passwd%00bob.jpg`   

* automated scanners like ZAP, OWASP, burp suite.

* fuzzing : inject a variety of directory traversal payloads into input fields to see if they trigger any file access.

* Check databases like CVE (Common Vulnerabilities and Exposures) and Exploit Database for known directory traversal vulnerabilities in software or frameworks used by the application.

### How to prevent directory traversal vulnerabilities
* validate user input by comparing it to an allow list of permitted values. or ensure that the input only contains alphanumeric characters.