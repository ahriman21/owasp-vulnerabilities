through misconfiguration we can disclose information that causes serious risks. These miss configurations can be default or week user & passwords, displaying errors that include sensitive data, and so on.

## How to find it
- To see if an application has default user pass or week passwords we can try entering multiple characters or using some disclosed dictionaries

- To find sensitive info we can try to break the application like entering shit data to see whether the application pop ups the development errors or not.

- We can use verb tamper approach to see if we can find any break in the application or not( for example using POST PUT DELETE methods instead of GET).

- Force browsing : we can fuzz the application and look for directories or content which is no linked in the application. you can use `ffuf` to scan an application

- **Tools**: Use security header analysis tools like `securityheaders.com`, or built-in features in Burp Suite.

- **Manual Check**: Look for missing or misconfigured headers like `Content-Security-Policy`, `X-Frame-Options`, `X-XSS-Protection`, `Strict-Transport-Security`.