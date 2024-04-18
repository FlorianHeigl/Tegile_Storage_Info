```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```

### PAths:


Running / active OS:

`ZebiSystem/ROOT/zebios-`3.9.1.0.190430.12.49`/zebi`
with the running version as the middle element here.

(Bootenvs werden offenbar genutzt)


`/var/log/tegile/exec.log`
Shell  history etc
This is one of the files that kill the SATA DOMs.


`/home/zebiadmin/jedec-v2.9-fw.bin`
NVDIMM Firmware

`/var/log/tegile/cbce.log`
Upgrade logfile


`/var/support/bin`
Tool Path for tools used by tech support or at instruction of tech support.
These are information gathering, maintenance/destructive ones and misceneanellous.

`/usr/bin`
OS + Tegile Tool Path


### Config Database
```
/dp0/Database:
db.lck  dbex.lck  log  seg0  service.properties  tmp
```


### Dataset paths with internal functions etc.

```
/dp0/Local:

/dp0/Replica:

/dp0/rrdFileStore:
zebi-blocksize-monitor  zebi-disk-monitor  zebi-disk-type-monitor  zebi-smb-monitor

/dp0/System:
SUNW.nfs

```


### SMB Share:
This is how a share looks like (keep in mind there's clustering and remote replication, as seen above)

```
[root@tegile02-a:zebi]# ls /export/halloshare/halloshare/
1   2      2b     3a  4.iso  5      5b  6b  7b  8b                                    TESTFILE
1a  2.iso  3      3b  4a     5.iso  6   7   8   FIOTEST
1b  2a     3.iso  4   4b     5a     6a  7a  8a  nw12-installer-2208091520-x86_64.iso
```



`/etc/zebi`
Primary Config directory


`/etc/zebi/ssl/tegilezebi.ts` - keystore
