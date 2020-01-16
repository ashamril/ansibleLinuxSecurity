# c4a-ansi4comply
Repo created for the C4A event

To use ansible to comply with IBM Security Compliance

Example:
Rule Title: Ensure SSH root login is disabled

Fix Text: To explicitly disallow root login. Add or correct the following line in "/etc/ssh/sshd_config":

PermitRootLogin no

name: "5.2.8 Ensure SSH root login is disabled"
lineinfile:
  state: present
  dest: /etc/ssh/sshd_config
  regexp: ^#?PermitRootLogin
  line: PermitRootLogin no
  validate: sshd -tf %s
  notify: reload sshd
