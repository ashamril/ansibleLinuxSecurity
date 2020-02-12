# c4a-ansi4comply
Repo created for the C4A event

## Title of the automation:
IBM or Clients Security Compliance Policy for Linux servers.

## User story:
Security compliance is a legal concern for organizations in many industries today. Regulatory standards prescribe recommendations for protecting data and improving info security management in the enterprise. In demonstrating security compliance, enterprises are better able to define and achieve specific IT security goals as well as mitigate the threat of network attacks through processes like vulnerability management. In some cases, failure to achieve and maintain security compliance can result in financial and legal penalties.

## Request Category:
Ansible

## Sub Category:
Ansible Asset

## Types:
Ansible Playbook

## Details:
CIS benchmarks are configuration baselines and best practices for securely configuring a system. Each of the guidance recommendations references one or more CIS controls that were developed to help organizations improve their cyberdefense capabilities. CIS controls map to many established standards and regulatory frameworks, including the NIST Cybersecurity Framework (CSF) and NIST SP 800-53, the ISO 27000 series of standards, PCI DSS, HIPAA, and others.

This playbook have been create to make use ansible to ensure server is comply as per Center for Internet Security (CIS) benchmark.

The playbook uses 3 modules listed below:
* Commands modules
** command
* Files modules
** file
** lineinfile
* System modules
** service
** sysctl
* Packaging modules
** yum

## Platform:
Red Hat Linux 7.x and below

## Scope of Automation:
As per Security Compliance Guideline, below is the topic that have been cover :
### Topics covered:
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

## Solution:
Ansible will be used to ensure the server that have been deployed follow the Security Compliance Policy.

## What is the estimation or assumption of saved time in minutes per case (per server, per execution, per schedule, etc)?:
1. How much time does it currently take to execute this task manually: 1-2 hours/server.
2. How much time this automation will reduce from the manual task: Will probably reduced time taken for a single server to 5-10 min.

## How often is this automation used?  What is the frequency for this automation?
The more offen to run this playbook to ensure we comply with Security Compliance is better but it would be adviceable to run it :
- at least every 90 days/once per quarter.
- run it on every new system that being deployed.

## Usage:
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

## Playbook Status:
Continuous developement need to for this playbook to ensure it cover more such as:
- Newest/Latest Red Hat release.
- Ubuntu based linux.
- Other Operating System  such as Solaris, HP-UX, and AIX
- Future additional compliance standards.

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
* Adi Razlan
* Hilman Hafiz
* Zamani Zainal
