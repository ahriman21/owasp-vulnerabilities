Vulnerable and outdated components  is a topic in OWASP top ten vulnerabilities that focuses on CVEs.

## How to find vulnerable components used in an application?
- **Inspect Source Code**: If accessible, review the application's source code for dependency files (e.g., `package.json` for Node.js, `requirements.txt` for Python).
- **Analyze HTTP Headers**: Sometimes HTTP headers can reveal server details (e.g., `X-Powered-By`).
- **Fingerprinting Tools**: Use tools like `Wappalyzer` or `BuiltWith` to identify the technology stack.
- **Responses**: You can find the version of component by the response of that service after making a request.

## How to exploit the vulnerability ?
- You can find exploitation for a vulnerability in `exploit DB` which is a web site.
- You can come up with a exploitation by testing some payloads.

### Note
> Nuclei is a tool for scanning on large number of targets based on templates. In this concept `template` is a data structure based on YAML.