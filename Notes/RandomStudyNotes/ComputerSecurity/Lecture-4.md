# Authentication
# Content
- Authentication Methods:
	1) something user knows
		1) passwords
		2) storing passwords
		3) 
	2) something user is
	3) something user has
	4) Challenge-Response
		1) simple challenge response
		2) 2 way challenge response
		3) efficient 2 way challenge response
	5) 2-Factor Authentication:
	6) Universal 2 Factor


# 4) Challenge-Response
1) simple challenge response
2) 2 way challenge response
3) efficient 2 way challenge response
# 5) 2-Factor Authentication
- The "factors" in 2 factor are basically one of the authentication methods, namely, user knows, user is, user has.
- So to be 2-factor authentication, it must be 2 of the 3 factors stated above, but cannot be the 2 from the same factor, i.e. cannot be user knows and then user knows again.
- 
# 6) Universal 2 Factor
- Registration flow
- Authentication flow
- ==????==
# 7) WebAuthn
- Registration Flow:
	- ==??==
- Authentication Flow

- Replay Attack:
	- legit user has already authenticated to a website, and is communicating with the website (called a session), attacker is sniffing hash values, the attacker will continue the session, even the original user had terminated the session.
		- to secure the channel: 
			- with time stamps,
			- use challenge-response mechanism