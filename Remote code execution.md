RCE is a vulnerability that attacker can inject a programming language code into vulnerable application and the app executes the code without validating it, for example the `eval()` function in PHP gets an input and executes it :

```php
$code = $_GET['input_name'];
eval($code);
```

Given the code attacker can enter malicious code according to the programming language used in the application. although code above can easily be exploited but you can use tricks to break the codes with higher security. We all know we can't read the source code but we can fuzz the input to find the suitable payload.

## How to prevent 
- don't use commands like `eval` which takes and process every input.
- validate the input before executing it in the back-end.