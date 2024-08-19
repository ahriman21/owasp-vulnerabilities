Insecure Design vulnerabilities occur because of wrong validations/controls on the inputs. such as :
- Uploads :
	- uploading large files to fill the target's storage
	- uploading `php` or `js` `python` files on a host relevant to its back-end tech.
	
- URL user entries :
	- enter URLs like `../../../etc/host`

- Business logic errors like **using payed features** by an unauthorized user, using unlimited discounts, double spending


## How to bypass file uploads
- stick some tricking extension to our file, for example `evil.php.png`, `evil.php%00.png` ... and so on.
- using image initializer bytes in the beginning of the malicious file.