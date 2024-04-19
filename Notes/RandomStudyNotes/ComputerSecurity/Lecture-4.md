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
	5) 2-Factor Authentication
	6) Universal 2 Factor
- Replay Attack:
	- legit user has already authenticated to a website, and is communicating with the website (called a session), attacker is sniffing hash values, the attacker will continue the session, even the original user had terminated the session.
		- to secure the channel: 
			- with time stamps,
			- use challenge-response mechanism