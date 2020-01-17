# c4a-ansi4comply
Repo created for the C4A event

## Usage :
* ansible-playbook -i ./list_hosts -u 5.2_SSH_Server_Configuration.yml

## Purpose:
* Make use of ansible to comply with IBM or Clients Security Compliance Policy for Linux servers.

1 Initial Setup
* 1.1 Filesystem Configuration

2 Services
* 2.1 inetd Services
* 2.2 Special Purpose Services
* 2.3 Service Clients

3 Network Configuration
* 3.1 Network Parameters (Host Only)
* 3.2 Network Parameters (Host and Router)
* 3.3 IPv6
* 3.4 TCP Wrappers
* 3.5 Uncommon Network Protocols

4 Logging and Auditing
* 4.1 Configure System Accounting (auditd)
* 4.2 Configure Logging

5 Access, Authentication and Authorization
* 5.1 Configure cron
* 5.2 SSH Server Configuration

6 System Maintenance
* 6.1 System File Permissions

## References:
1. https://www.cisecurity.org/benchmark/red_hat_linux/<br>
CIS Red Hat Enterprise Linux 8 Benchmark v1.0.0<br>
CIS Red Hat Enterprise Linux 7 Benchmark v2.2.0<br>
CIS Red Hat Enterprise Linux 6 Benchmark v2.1.0<br>
CIS Red Hat Enterprise Linux 5 Benchmark v2.2.0<br>
2. https://secscan.acron.pl/centos7/start


### Example:
* Rule Title: Ensure SSH root login is disabled
* Fix Text: To explicitly disallow root login. Add or correct the following line in "/etc/ssh/sshd_config":
* PermitRootLogin no
  > name: "5.2.8 Ensure SSH root login is disabled"<br>
  > lineinfile:<br>
  > 	state: present<br>
  > 	dest: /etc/ssh/sshd_config<br>
  > 	regexp: ^#?PermitRootLogin<br>
  > 	line: PermitRootLogin no<br>
  > 	validate: sshd -tf %s<br>
  > notify: reload sshd<br>

## Team Members:
* Ami Shamril
* Ikmal Ahmad
* Hilman Hafiz
* Zamani Zainal
* Adi Razlan
