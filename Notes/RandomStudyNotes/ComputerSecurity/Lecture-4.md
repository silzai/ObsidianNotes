# Authentication
- Replay Attack:
	- legit user has already authenticated to a website, and is communicating with the website (called a session), attacker is sniffing hash values, the attacker will continue the session, even the original user had terminated the session.
		- to secure the channel: 
			- with time stamps,
			- use challenge-response mechanism