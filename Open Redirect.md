Web application redirects user based on not trusted  input. We can leverage it to achieve XSS or trick the victim by the look of URL.

## Examples Of Open Redirect
- Attackers can leverage a trusted domain to send victims to the malicious website by manipulating URL :
```
example.com?next=evil.com
```
as you can see victim thinks it is example.com but when they click on it they will be redirected to the `evil.com`.

- Attackers can use a JS code to manipulate url and send victims to a malicious website :
```javascript
<script>window.location = 'something';</script>
```