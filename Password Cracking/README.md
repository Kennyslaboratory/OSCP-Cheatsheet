# Cracking Passwords

## Password Cracking Tools
| # | Tool | Description |
| --- | --- | --- |
| 1 | Hashcat | Effective & popular offline password cracker.  Can utilize your GPU for cracking. |
| 2 | John-the-Ripper | Alternative offline password cracker. |
| 3 | Hydra | Popular tool for doing online password brute forcing. |

## Utilizing GPU & CPU fore cracking
These agruments will force Hashcat to use the CUDA GPU interface which is buggy but provides more performance. (–force) will Optimize for 32 characters or less passwords (-O) and will set the workload to "Insane" (-w 4) which is supposed to make your computer effectively unusable during the cracking process. Finally "--opencl-device-types 1,2 " will force HashCat to use BOTH the GPU and the CPU to handle the cracking.
```
--force -O -w 4 --opencl-device-types 1,2
```

## Cracking Linux Hashes - /etc/shadow file
| ID | Description |
| --- | --- |
| 500 |	md5crypt $1$, MD5(Unix)
| 200 |	bcrypt $2*$, Blowfish(Unix)
| 400	| sha256crypt $5$, SHA256(Unix)
| 1800 |	sha512crypt $6$, SHA512(Unix)


## Cracking Windows Hashes
| ID | Description |
| --- | --- |
| 3000 | LM |
| 1000 | NTLM |

## Cracking File Passwords
| ID | Description | Type |
| --- | --- | --- |
| 11600	| 7-Zip	| Archives |
| 12500 |	RAR3-hp |	Archives |
| 13000 |	RAR5 | Archives |
| 13200 |	AxCrypt | Archives |
| 13300 |	AxCrypt | in-memory SHA1 | Archives |
| 13600	| WinZip | Archives |
| 9700 | MS Office <= 2003 $0/$1, MD5 + RC4	| Documents |
| 9710 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #1 | Documents |
| 9720 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #2 | Documents |
| 9800 | MS Office <= 2003 $3/$4, SHA1 + RC4 | Documents |
| 9810 | MS Office <= 2003 $3, SHA1 + RC4, collider #1 | Documents |
| 9820 | MS Office <= 2003 $3, SHA1 + RC4, collider #2 | Documents |
| 9400 | MS Office 2007 | Documents |
| 9500 | MS Office 2010	| Documents |
| 9600 | MS Office 2013	| Documents |
| 10400	| PDF 1.1 - 1.3 (Acrobat 2 - 4) | Documents |
| 10410	| PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #1 | Documents |
| 10420	| PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #2 | Documents |
| 10500	| PDF 1.4 - 1.6 (Acrobat 5 - 8)	| Documents |
| 10600	| PDF 1.7 Level 3 (Acrobat 9)	| Documents |
| 10700	| PDF 1.7 Level 8 (Acrobat 10 - 11)	| Documents |
| 16200	| Apple Secure Notes | Documents | 

## Crack a Zip Password

Hashcat appears to have issues with some zip hash formats generated from zip2john. You can fix this by editing the zip hash contents to align with the example zip hash format found on the hash cat example page: `$zip2$*0*3*0*b5d2b7bf57ad5e86a55c400509c672bd*d218*0**ca3d736d03a34165cfa9*$/zip2$`

zip2john seems to accept a wider range of zip formats for cracking.

```
zip2john Zipfile.zip | cut -d ':' -f 2 > hashes.txt
hashcat -a 0 -m 13600 hashes.txt /usr/share/wordlists/rockyou.txt
```

## Cracking a WordPress Hash
```
hashcat --force -m 400 -a 0 -o found1.txt --remove wphash.hash /usr/share/wordlists/rockyou.txt
```

# Bruteforcing with Hashcat
When all else fails, go for a bruteforce.

### Hashcat Predefined Charsets
| Key | Value |
| --- | --- |
| ?l | abcdefghijklmnopqrstuvwxyz |
| ?u | ABCDEFGHIJKLMNOPQRSTUVWXYZ |
| ?d | 0123456789 |
| ?s | «space»!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~ |
| ?a | ?l?u?d?s |
| ?b | 0x00 - 0xff |

Brute force all passwords length 1-8 with possible characters A-Z a-z 0-9:
```
hashcat64 -m 500 hashes.txt -a 3 ?1?1?1?1?1?1?1?1 --increment -1 ?l?d?u
```


