```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```

 ### `/usr/bin`

`/usr/bin/nvdadm` 
healthcheck and management tool for NVDIMM Module
Subcommands: 

- status
- health 
- ...

OK Status looks like this:

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
Detects incorrectly set up NVDIMM modules and repartitions / rearms them for use.
- This is DESTRUCTIVE to the module content
- If you're not having NVDIMMs that can no longer be ARM'ed you don't need this
- If you have the latest BIOS updates you likely don't even end up in the situation
- 
(But I don't know how many Tegile customers got the luxury situation of having an up to date BIOS)


----

 ### `/zebi/bin`

The script `ha.sh` under `scripts` is the main script for cluster management and allows e.g. cluster initialisation.
To create a cluster (via CLI and also via GUI) you need the WWNs of three quorum discs in the system.
These must not have any active reservations and must not be 'locked' via TCG.


 ### diskencrypt

Swiss Army Knife for Management of TCG disk encryption.
- Lock/Unlock
- Key Management (Rollover etc)
- Secure Erase


 ### sg3 tools

Management von SCSI-3 Reservations

