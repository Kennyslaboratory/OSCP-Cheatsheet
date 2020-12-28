# Offensive Security Ultimate Cheatsheet!
The goal of this repository is not to spoil the OSCP Exam, it's to save you as much time as possible when enumerating and exploiting potential low hanging fruit.  It's very easy to get caught up in the weeds of debugging and troubleshooting broken payloads only to lose out on all your time to pass the exam.

You're on your own when the exploits start flying--I'll try to include potential tips and tricks you can try but it's up to you to fully understand the proper material before starting the exam.

-------------

![Hacker](lol_hoody.jpg)

-------------

## Start Here
| # | Step | Description |
| --- | --- | --- |
| 1 | `Discover` | Discover what's on the network |
| 2 | `Document` | Document your findings in CherryTree |
| 3 | `Select` | Select the specific cheatsheet for the box you are attacking |

-------------
# 1 - Discover
Before you can follow my exploitation tips and tricks, you'll need to enumerate what's on the network.

## Automated OSCP Enumeration Script
Use these automated tools to save as much time as possible when enumerating vulnerabilities!

| # | Resource | Description |
| --- | --- | --- |
| 1 | [Reconnoitre](https://github.com/codingo/Reconnoitre) | A tool specifically created for scanning OSCP labs. |
| 2 | [AutoRecon](https://github.com/Tib3rius/AutoRecon) | A tool for scanning both CTFs and OSCP. |


## Manual Scanning Commands

### Nmap
| # | Command | Description |
| --- | --- | --- |
| 1 | `nmap -sn 10.11.1.0/24` | Enum IPs. Quick SYN scan without looking for open ports.  |
| 2 | `nmap -sC -sV -vv -oA quick 10.11.1.4` | Quick TCP scan on target IP |
| 3 | `nmap -sU -sV -vv -oA quick_udp 10.11.1.7` | Quick UDP scan on target IP |
| 4 | `nmap -sV -O -F --version-light 10.11.1.6` | Quick OS Detection & Port Scan on target IP  |
| 5 | `nmap -sC -sV -p- -vv -oA full 10.11.1.8` | Very long and aggressive TCP scan on target IP |

### Interesting Ports
| --- | --- |
| Port # | Description |
| 21 | FTP server, unencrypted. |
| 22 | SSH server, can be connected to via SSH |
| 23 | Telnet. Basically an unencrypted SSH |
| 25 | SMTP - Email sending service. [Query it]() to enum email addresses? |
| 80 | HTTP Server, hosting website? Try visiting IP with web browser |
| 445 | SMB service, likely vulnerable to an SMB RCE |
| 3306 | MySQL Database.  Attempt to connect it? |
| 3389 | Listening for RDP connection |


### Nmap Enum Scripts
| # | Script | Type | Description |
| --- | --- | --- | --- |
| 1 | [smb-check-vulns.nse](https://github.com/mubix/tools/blob/master/nmap/scripts/smb-check-vulns.nse) | SMB  | Scans for multiple SMB vulnerabilities. |
| 2 | [smb-vuln-cve2009-3103.nse](https://www.exploit-db.com/exploits/9594) | SMB  | Windows Vista SP1/SP2 and Server 2008 (x86) |
| 3 | [smb-vuln-ms06-025.nse](https://www.exploit-db.com/exploits/1940) | SMB | Windows 2000 and Windows XP (x86) |
| 4 | [smb-vuln-ms07-029.nse](https://www.exploit-db.com/exploits/16366) | SMB | Windows 2003 SP1/SP2 |
| 5 | [smb-vuln-ms08-067.nse](https://www.exploit-db.com/exploits/40279) | SMB | Windows XP |
| 6 | [smb-vuln-ms10-054.nse](https://www.exploit-db.com/exploits/14607) | SMB | XP, Vista, 7 |
| 7 | [smb-vuln-ms10-061.nse](https://www.exploit-db.com/exploits/16361) | SMB | XP, Vista, 7 |
| 8 | [smb-vuln-ms17-010.nse](https://www.exploit-db.com/exploits/42315) | SMB | EternalBlue.  XP, Vista, 7, 8.1, 10 |
| 9 | [smb-enum-shares.nse](https://github.com/nmap/nmap/blob/master/scripts/smb-enum-shares.nse) | SMB | Enumerates SMB Shares |
| 10 | [smb-enum-users.nse](https://github.com/nmap/nmap/blob/master/scripts/smb-enum-users.nse) | SMB | Attempts to enumerate Windows users |

*Example: Using an Nmap Script*
```
nmap -p 445 -vv --script=[script.nse] 10.10.10.10
```

## Linux Enumeration
```
enum4linux -a 10.11.1.9
```

### Banner Grabbing
| # | Command | Description |
| --- | --- | --- |
| 1 | /dev/tcp/$ip/$port | If nmap didn't banner grab or it's not installed. |

### DNS Zone Transfer
| # | Command | Description |
| --- | --- | --- |
| 1 | `dig example.com any` | View DNS records on a domain. |
| 2 | `dnsrecon -d example.com` | Multiple queries to DNS server that enumerates DNS records. |

### SMTP Email Enumeration
| # | Command | Description |
| --- | --- |
| 1 | `nmap -script smtp-commands.nse 10.11.1.41` | Scan for possible SMTP commands that can be executed |
| 2 | `smtp-user-enum -M VRFY -U /root/sectools/SecLists/Usernames/Names/names.txt -t 10.11.1.41` | SMTP Enum. `-M` for mode. `-U` for userlist. `-t` for target |
