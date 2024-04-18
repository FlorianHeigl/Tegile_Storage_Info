
----
 # `/usr/bin`

`/usr/bin/nvdadm` 
healthcheck und management tool fuer NVDIMM Module
Subkommandos: 

- status
- health 
- ...

Guter Status sieht so aus:

```
Status Summary:
        Controller State: Armed
```


---- 
 # `/var/support/bin`

```
binary_install.sh       iscsiproto        san_vaai_ops        spathrot
boot                    kmastat           san_vaai_ops_3.5    support_email.py
chunkstat               kstats.pl         sanlongios          syscheck.py
colormylog_library      mdbchanges.sh     sanzfsio            trace_function
colormylog.py           nfs_queue_time.d  sasmap.py           trusty-up
ddtstat                 nfslongios        sbdtaskq            ui_spaceused
diskslots.sh            nfszfsio          sbdtq               ulq_addrm
fc_proto                nvpart.sh         scripts             ulq_stats
fixup                   objectclone       smb3_stats.sh       ulq_vp
fsp                     pgr_trace         smload              ulq_walk
getinfo.sh              preload.d         sortchunkmap.py     watch.sh
getpass.py              quick_snoop.sh    space_chk_avail     wr_throt
ifcli                   README            space_chk_err       zebisystem-cleanup.sh
iflash_perf.py          recmpfree         space_chk_err_mini  zfs.bestpractices.json
impfunc.py              recmpnext         space_chk_meta      zfs.py
intellicare_correct.sh  recmpproc         space_chk_tmprsv    zfsio
iperf                   recmptrig         space_chk_update    zfslongios
iraid                   san_odx_trace     spasync
```



`/var/support/bin/nvpart.sh`

Erkennt fehlerhaft eingerichtete NVDIMM Module und partioniert sie zur Verwendung neu.


----

 ### `/zebi/bin`

Das Script `ha.sh` unter `scripts` ist das Hauptscript fuer das Cluster-Management und erlaubt z.b. Cluster Initialisierung.
Zum Anlegen eines Clusters (per CLI und auch per GUI) braucht man die WWNs von drei Quorum Disks im System.
Diese duerfne keine aktiven Reservations haben und duerfen nicht via TCG 'locked' sein.


 ### diskencrypt

Schweizer Taschenmesser fuer das Management der TCG Diskverschluesselung.
- Lock/Unlock
- Key Management (Rollover etc)
- Secure Erase


 ### sg3 tools

Management von SCSI-3 Reservations

