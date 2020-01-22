# c4a-ansi4comply
Repo created for the C4A event

## Title of the automation:
IBM or Clients Security Compliance Policy for Linux servers.

## User story:
Each quater there server that not comply with Security Compliance issue.  There is  a lot of time taken to ensure most of the server in the environment to follow the Security guideline.

## Request Category:
Ansible

## Sub Category:
Ansible Asset

## Types:
Ansible Playbook

## Details:
* Make use of ansible to comply with IBM or Clients Security Compliance Policy for Linux servers.

## Platform:
Linux

## Scope of Automation:
New IBM clients which need to follow security guideline as per Security Compliance for Linux servers in their environment.

## Solution:
Ansible will be used to fixed implement Security Compliance Policy for Linux server.

## What is the estimation or assumption of saved time in minutes per case (per server, per execution, per schedule, etc)?:
1. How much time does it currently take to execute this task manually: 1-2 hours/server.
2. How much time this automation will reduce from the manual task: Will probably reduced time taken for a single server to 5-10 min.

## How often is this automation used? What is the frequency for this automation?
Each time an environment Security Compliance need to be enforced.

## Usage :
* ansible-playbook -i ./list_hosts -u <username> SecurityCompliance.yml

SecurityCompliance.yml will call:
1. 1.1_Filesystem_Configuration.yml
2. 2.2_Special_Purpose_Services.yml
3. 3_TCP_Wrappers.yml
4. 4_Configure_Logging.yml
5. 5_SSH_Server_Configuration.yml
6. 6.1_System_File_Permissions.yml

The name of of need to be include in: list_hosts before the execution
This playbook run with assumption that user can sudo without using password (this can be fixed in future release by using ansible-vault).

## Topics covered:
1 Initial Setup
* 1.1 Filesystem Configuration

2 Services
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

## References / Benchmark:
1. https://www.cisecurity.org/benchmark/red_hat_linux/<br>
- CIS Red Hat Enterprise Linux 8 Benchmark v1.0.0<br>
- CIS Red Hat Enterprise Linux 7 Benchmark v2.2.0<br>
- CIS Red Hat Enterprise Linux 6 Benchmark v2.1.0<br>
- CIS Red Hat Enterprise Linux 5 Benchmark v2.2.0<br>

## Example:
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
