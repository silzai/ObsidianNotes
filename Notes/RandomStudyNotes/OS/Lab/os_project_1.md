# Server Side:
- Make scripts for:
	- [x] Webserver Setup
	- [x]  SSH Configuration
	- [ ] SFTP Configuration
	- [x] DNS Configuration
	- [ ] Managing Unsuccessful Attempts Log:
		- [ ] make `unsuccessful_attempts.log` do this by taking the client side logs and consolidate them. 
		- [x] Automatically erase this log after one week   
# Client Side:
- [ ] `main.sh`: to manage user credentials 
	- [ ] Check User Group Membership
	- [ ] Log Invalid Attempts: save in `invalid_attempts.log`
	- [ ] Handle Excessive Invalid Attempts: save in `unsuccessful_attempts.log` and send to server using `rsync`
	- [ ] Schedule user logout: `gnome-session-quit-no-prompt`
- [ ] `verify.sh`:
	- [ ] test by creating an `admin` group and adding `techuser` to it
# Testing:
- [ ] Scripts:
	- [ ] `meshping.sh` to ping all ==???? Who is pinging who and vice versa and how many times ????==
	- [ ] `traceroute.sh` check connectivity using trace route, and reboots the machine in case the target cannot be reached.
		- [ ] all info is saved in `network.log`
	- [ ] otherwise show the current date with this message `Connectivity with $target_IP is ok`
# tools to use, just fyi:
- apache http server
- quad9 for dns
- ssh
- sftp
- rsync: used to send `client_timestamp_invalid_attempts.log` to the server to consolidate in `unsuccessful_attempts.log`

