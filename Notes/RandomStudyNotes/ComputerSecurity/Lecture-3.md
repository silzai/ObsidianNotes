# Basics of Cryptography
1) symmetric crypto: uses shared key
	- goal is confidentiality but
	- does not provide authenticity
	- does not provide non-repudiation
	- cannot verify integrity
	- requires management of large number of keys that are shared:
		- if user is communicating with 10 different users, then user has to store 9 keys, and do exchanges of $\frac{10 \times (10-1)}{2}=45 \ exchanges$
1) asymmetric crypto:
	- goal is confidentiality and integrity and authenticity on both sides (who sent it and who received it)
	- encrypting and decrypting the data is very slow
1) Hybrid crypto:
	- send the shared key using asymmetric encryption, because the key is small in size, and is not slow to use asymmetric cryptography to exchange the key
3) hashing
	- goal is integrity
	- One-Way Function
	- is very fast, easy to calculate
	- use it mainly in digital signatures
4) digital signature
	- goal is proving authenticity of sender, and integrity and non repudiation of sender
	- (but no non-repudiation of recipient)
	- does not give confidentiality
	- ==???==

	
- 