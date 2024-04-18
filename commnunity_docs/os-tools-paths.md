```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```



 ## /etc

 ### main config files

- /etc/zebi/conf/zebi.conf primary config file
- /etc/zebi/conf/zebi.conf.old primary config file

 ### `zebi.conf` critical parameters:

- database.main.username
- database.main.password
- appliance.model
- appliance.revision
- appliance.controller.no
- zebi.upgrade.force
- zebi.guid
- appliance.ses
- chassis_id
- tegile.internal.server
- gui.network.ipmp.probe.enabled

The main config is in a PGSQL database (clustered?)
No information gathered on the schema, as of now.


 ### Other config bits that matter:

- /etc/zebi/conf/zebi-smf.conf service config, decides which services to start. Note that some will be cluster controlled (FC target etc)
- /etc/ixgbeN.info base nic config and assignment to interface groups

- /etc/zebi/ssl/zebi.key priv key


 ### Upgrade logs

- /var/svc/log/tegile-zebi-upgrade:default.log upgrade status log
- /var/log/tegile/upgrade-cleanup/upgrade-zebios_DATE_TIME

Only in the log directory

./1234-2022_09_01_21_14_58-tegile02-a_abc.de-C0-nvdimm-arm/system_config/zebiversion

 ### Debugging logs

- /var/log/tegile/ZebiFixQuorumDisk.log
- /var/log/tegile/zebi/zebiui.log
- /var/log/tegile/zebi/zebirep.log


 ### Firmware

- /usr/share/firmware

This contains the firmware updates for CPLD, BIOS, Backplane, SAS or NVMe drives
Only recent updates for recently introduced components seem to have been released via this method.
(i.e. it contains no SAS SSD firmware)


 ### Webapp Raid definions

This folder holds single .conf files for various scenarios depending on Raid levels and Drive types.
This is interesting if you want to mess with vdev sizes or the number of hot spares.
