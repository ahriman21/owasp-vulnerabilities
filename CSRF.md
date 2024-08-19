**Cross-Site Request Forgery (CSRF)** is a type of attack that tricks a user into executing unwanted actions on a web application where they are authenticated. This can lead to unauthorized actions being performed without the user's consent or knowledge. **For example** *==a user is tricked to click on a link, so after user/victim going to the malicious website an action will be executed such as changing the victim's password or transferring money.==*

## How CSRF Works

1. **User Authentication:**
    - The user logs into a web application, such as their bank, and receives a ==session cookie== that keeps them authenticated.

1. **Malicious Request:**
    - The attacker creates a malicious website with a request that targets the authenticated web application. This request could perform actions like transferring money or changing the user's email address. It can be either a script which the inputs are already filled by attacker or a form that user fills without knowing that it is a fraud. 

1. **Execution:**
    - When the user visits the malicious site, the malicious request is automatically sent to the targeted web application with the user's session cookie, causing the action to be performed without the user's consent.

## How To Detect CSRF
1. **Code Review:**
    - Inspect the application's code for forms and actions that do not include anti-CSRF tokens.
    
1. **Automated Tools:**
    - Use automated security scanners like OWASP ZAP or Burp Suite to detect CSRF vulnerabilities.
    
1. **Manual Testing:**
    - verb tampering and see if the targets is ok with it.
    - change the CSRF token to a random value and see if the target validated it or not.
    - 




## How To Prevent CSRF Vulnerability In Our App
1. **Anti-CSRF Tokens:**
	- Include a unique token in each form that is validated on the server side. This token must be unpredictable and tied to the user's session.
	```html
	<input type="hidden" name="csrf_token" value="unique_token_value">`
	```

2. **Use SameSite cookies:**
	- Set cookies with the `SameSite` attribute to prevent them from being sent on cross-origin requests.
	```
	`Set-Cookie: sessionid=abc123; SameSite=Lax`
	```

3. **Referer and Origin Header Validation:**
	- Check the `Referer` and `Origin` headers to ensure the request originates from a trusted domain.
