Vulnerability	Payload Used	Vulnerable Result	Safe Result
Reflected XSS	<script>alert('reflected')</script>	Popup executed	Shown as escaped text, no popup
Stored XSS	<img src=x onerror=alert('stored-xss')>	Popup on page load (comment stored in DB)	Comment shown as plain text, no popup
DOM-based XSS	#<img src=x onerror=alert(1)> in URL hash	Popup via innerHTML	Text shown via textContent, no popup
CSRF	Hidden auto-submit form to /change-email	Email changed to attacker@evil.com silently	ForbiddenError: invalid csrf token
SQL Easy	' OR '1'='1' -- 	Login bypassed (logged in as alice)	Invalid credentials
SQL
Intermediate	?id=1 AND 1=1  vs  ?id=1 AND 1=2	Different responses (User found / No such user)	Invalid id (rejected)
SQL
Advanced	UNION SELECT chain: columns → tables → columns → data	Full username/password dump leaked	Empty result []
