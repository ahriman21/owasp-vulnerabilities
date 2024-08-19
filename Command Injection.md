OS Command injection is a vulnerability that hackers execute unauthorized commands on the host operating system via a vulnerable application.

### How to find command injection vulnerability
- Check source code and see if there is any validations or not (in white-box context).

- Look for inputs or URL parameters that it are suspicious for communicating with operating system and test them via OS commands like `sleep` or `ping` or you can use command separators .

- Fuzz the application with command separators such as :
```
; cat /etc/passwd

&& cat /etc/passwd

| cat /etc/passwd

|| cat /etc/passwd

` /etc/passwd

$(/etc/passwd)

{/etc/passwd}

cat{$IFS}/etc/passwd

```

### How to prevent 
* In your application use more specific OS command functions instead of general functions that take all kinds of commands.
	example :
		1. `system('mkdir dirname')` -----> VULNERABLE
		2. `mkdir('dirname')`               -----> OK

* Validate the inputs, you can literally use conditional statements to find malicious user inputs.

### Command injection tools  
- commix ---> `https://github.com/commixproject/commix.git`


### Reverse shell
HTTP is a stateless protocol, in the command injection attackers execute commands on a non-interactive shell. So if you want to have an interactive and solid access to the victim's host you can use `reverse shell` payloads.

-> **Reverse shell procedure :**
- attacker listens on a port (like using `nc` command in terminal)
- victim connects to a port (you can send a payload to do this)
- attacker spawns a shell and gets access to it



### Notes
- You can find a blind vulnerability by using `sleep` command.
- If you can't use HTTP to pull data  use DNS protocol. 
