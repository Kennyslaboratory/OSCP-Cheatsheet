# Cracking Passwords

## Password Cracking Tools
| # | Tool | Description |
| --- | --- | --- |
| 1 | Hashcat | Effective & popular offline password cracker.  Can utilize your GPU for cracking. |
| 2 | John-the-Ripper | Alternative offline password cracker. |
| 3 | Hydra | Popular tool for doing online password brute forcing. |

## Utilizing GPU & CPU fore cracking
```
--force -O -w 4 --opencl-device-types 1,2
```

The above agruments will force Hashcat to use the CUDA GPU interface which is buggy but provides more performance. (–force) will Optimize for 32 characters or less passwords (-O) and will set the workload to "Insane" (-w 4) which is supposed to make your computer effectively unusable during the cracking process. Finally "--opencl-device-types 1,2 " will force HashCat to use BOTH the GPU and the CPU to handle the cracking.

## Cracking a WordPress Hash

```
hashcat --force -m 400 -a 0 -o found1.txt --remove wphash.hash /usr/share/wordlists/rockyou.txt
```

## Crack a Zip Password
```
zip2john Zipfile.zip | cut -d ':' -f 2 > hashes.txt
hashcat -a 0 -m 13600 hashes.txt /usr/share/wordlists/rockyou.txt
```

Hashcat appears to have issues with some zip hash formats generated from zip2john. You can fix this by editing the zip hash contents to align with the example zip hash format found on the hash cat example page: `$zip2$*0*3*0*b5d2b7bf57ad5e86a55c400509c672bd*d218*0**ca3d736d03a34165cfa9*$/zip2$`

zip2john seems to accept a wider range of zip formats for cracking.

## Bruteforcing with Hashcat
When all else fails, go for a bruteforce.
Brute force all passwords length 1-8 with possible characters A-Z a-z 0-9:
```
hashcat64 -m 500 hashes.txt -a 3 ?1?1?1?1?1?1?1?1 --increment -1 ?l?d?u
```
### Predefined Charsets
| Key | Value |
| --- | --- |
| ?l | `abcdefghijklmnopqrstuvwxyz` |
| ?u | `ABCDEFGHIJKLMNOPQRSTUVWXYZ` |
| ?d | `0123456789` |
| ?s | ```«space»!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~``` |
| ?a | `?l?u?d?s` |
| ?b | `0x00 - 0xff` |


