### Cookies
Cookies are blocks of data containing data associated to a user which is stored in the user's browser.

### Cookie Properties
1. **Cookie's Scope** 
	Cookies have scope, meaning if you create a cookie for `example.com` it won't be in the `www.example.com` scope. ==`www.example.com's coockie`== **!=** ==`example.com's cookie`==.
	You can change this behavior and set a global domain cookie which is acceptable in all subdomains using a dot before the domain name `domain=.example.com`.
	You even can set cookies for each path of your web application.

2. **Expiration**
	Sets an expiration date for the cookie. After this date, the cookie will be deleted. The date should be in the format `Wdy, DD Mon YYYY HH:MM:SS GMT`.

3. **Secure**
	When set, the cookie will only be sent over HTTPS connections, enhancing security.

4. **HttpOnly**
	When set, the cookie is inaccessible to JavaScript’s `Document.cookie` API, mitigating the risk of cross-site scripting (XSS) attacks.
	
5. **SameSite**
	Checks if a cookie is sent with cross-site requests or not, providing some protection against cross-site request forgery (CSRF) attacks. The possible values are:
		-->`Strict`: The cookie is not sent with cross-site requests.
		--> `Lax`: The cookie is sent with same-site requests and [[#Top-Level Navigation]] GET requests.
		--> `None`: The cookie is sent with all requests, but the `Secure` attribute must also be set if `None` is used.

### Top-Level Navigation

**Top-level navigation** refers to the primary or main navigation of a web page, which is the highest level of navigation in the browser's context. It usually involves navigating to a new URL that appears in the browser's address bar. Here are a few key points to understand top-level navigation:

1. **Examples:**
    - **Clicking a Link:** When you click a link that takes you to a different page or website, it is top-level navigation.
    - **Entering a URL:** Typing a URL directly into the browser's address bar and hitting enter.
    - **Submitting a Form:** Submitting a form that navigates to a new page.
    - **Redirects:** Being redirected to a new URL by the server.
    
2. **Top-Level Navigation and Cookies:**
    - Some cookie attributes, like `SameSite=Lax`, are designed to allow cookies to be sent during top-level navigation GET requests, providing some level of protection against Cross-Site Request Forgery (CSRF) attacks without completely blocking cross-site cookies.


### Same Origin Policy
same origin policy is determined by browsers, they disallow a web application reading data from another web application. The parameter of this functionality is that when a request is sent, the source needs to have the same origin as destination. example :

* http://x.com --> https://x.com --------> DENY (different protocol)
* http://x.com --> https://x.com/login/ --------> OK 
* http://x.com --> https://x.com:8080 --------> DENY (different port)
##### What is origin ?
origin is defined by protocol, host name, and port of the URL.

### Content Security Policy
**Content Security Policy (CSP)** is a security feature that helps a web app to prevent various types of attacks, such as Cross-Site Scripting (XSS) and data injection attacks, by restricting the sources from which content can be loaded and executed on a web page.

-->**HTTP Header:**
- CSP is implemented via an HTTP header (`Content-Security-Policy`) that the server sends to the browser.

