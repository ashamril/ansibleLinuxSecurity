# c4a-ansi4comply
Repo created for the C4A event

Usage:
To use ansible to comply with IBM Security Compliance

Example:
Rule Title: Ensure SSH root login is disabled

Fix Text: To explicitly disallow root login. Add or correct the following line in "/etc/ssh/sshd_config":

PermitRootLogin no

name: "5.2.8 Ensure SSH root login is disabled"<br>
lineinfile:<br>
	state: present<br>
	dest: /etc/ssh/sshd_config<br>
	regexp: ^#?PermitRootLogin<br>
	line: PermitRootLogin no<br>
	validate: sshd -tf %s<br>
notify: reload sshd<br>

Team Members:
