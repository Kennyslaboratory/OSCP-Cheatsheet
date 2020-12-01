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
## 1 - Discover
First, you must enumerate the attack surface of the box.  I have a curated list for each possible scenario you might run into.  The majority of recon is about following a checklist you are comfortable with, prioritizing your scanning efforts, and documenting your findings well.  Get a high-level overview of the network and the available attack surface before diving into the weeds with exploitation, evasion, and data exfiltration. 


### Nmap
| # | Command | Description |
| --- | --- | --- |
| 1 | `nmap -sn 10.11.1.0/24` | Quick SYN scan without looking for open ports  |
| 2 | `nmap -sV -O -F --version-light 10.11.1.` | Quick OS Detection & Port Scan  |

### Nmap Scripts
| # | Command | Type | Description |
| --- | --- | --- | --- |
| 1 | `smb-vuln-cve2009-3103.nse` | SMBv2  | https://cvedetails.com/cve/CVE-2009-3103/ - Windows Vista SP1/SP2 and Server 2008 (x86) |
| 2 | `smb-vuln-ms06-025.nse` | SMB  | ... |
| 3 | `smb-vuln-ms07-029.nse` | SMB  | ... |
| 4 | `smb-vuln-ms08-067.nse` | SMB  | ... |
| 5 | `smb-vuln-ms10-054.nse` | SMB  | ... |
| 6 | `smb-vuln-ms10-061.nse` | SMB  | ... |
| 7 | `smb-vuln-ms17-010.nse` | SMB  | ... |
| 8 | `smb-enum-shares.nse` | SMB Shares Enum  | ... |
| 9 | `smb-enum-users.nse` | SMB Users Enum | ... |

## Linux Enumeration
```
enum4linux -a 10.10.10.10
```

### Banner Grabbing


### DNS Zone Transfer

