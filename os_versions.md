

### Compatibility 

Known / Found issues

- Fallback via Grub has not worked in test beyond major version (likely due to zpool version on the OS pool?)
- 3.11.xx newest cannot talk to 3.9.0.1, upgrade timeout
- 3.11.0.3 Data cannot be activated on 3.9.0.1

So the feature boundary is between these two and you need an intermediary upgrade to pass it.


### Status

The Tegile download mirror is down^W^W back up.
It's likely that DDN will disable it once there's no customer entitled for access.

## Release files

A release would normally consist of
- ISO File (used in fresh reinstalls of a node etc)
- ISO File md5 checksum
- upgrade.tar.gz (used in upgrades/rolling upgrades)
- upgrade.tar.gz md5 checksum
- User Manual (Accessible via Web GUI)
- API Docs (Accessible via Web GUI)

Sometimes you'll also see add-ons like
- Release Notes for Customer (not publicly available most of the time)
- Release Notes for internal use (same but more verbose/more content but made available publicly. At least not regularly.)
- WAR File containing just the web management (named "Skywalk"?) and/or hotfixes/feature upgrades
- Support Tool bundle being updated/refreshed (*)



(*)This seems to be both a `sosreport` style collector tool and the tools the CE will use for their own maintenance work.  
None of this will be safe to use for other parties without direction by support personell.

## Version history



### Apparent mainline versions

#### 3.11.0....

- 3.11.0.5.126 jun 2021
- 3.10.1.0.254 aug 2022
- 3.11.0.6.4 jan 2023
- 3.11.4.1.4 oct 2022
- 3.11.4.3.3 feb 2023 - latest automatically rolled out? (to my box)

### Unknown feasibility versions

- 3.11.6.2.8 nov 23
- 3.11.0.7.3 jul 23
- 3.11.6.3.13 apr 24
- 3.11.6.4.3 jul 24
- 3.11.6.5 sep 24
- 3.11.6.5.13 dec 24
- 3.11.6.6 apr 25

Basically, the 3.11.6 series will only successfully install on the newer `5xxx` or maybe even only `6xxx` series unless you throw some **serious time** at it. It seems the H6200 are the last arrays standing - somewhere.
The 3.11.6 series probably also seems to be the only one that officially supports **redundant** SAS loop cabling which is a huge loss.
So far, no public table of features in the various trees has been sighted.
3.11.6.6 was most likely only released to a very small number of remaining customers.
(if that's you, please invoke your license rights to get the CDDL sources for your OS)

### Versions with security issues

- There was a [security advisory](https://www.westerndigital.com/support/product-security/wdc-19008-intelliflash-web-management-interface-vulnerability) affecting versions < 3.9.2 

- There's no known published advisories regarding SSL, SSH, or general Solaris issues that might or might not affect the systems, irrespective of advisories published by the projects themselves. Assume that some issues may exist.
- There's no known published advisories regarding iSCSI, NFS, SMB issues that might or might not affect the systems, irrespective of advisories published by the projects themselves. Assume that some issues may exist.


## Setup up repos (for addons or to ensure long-term sustainability)

The upstream (and cloned local) repositories use a P5P format, docs can be found here:
https://docs.oracle.com/cd/E36784_01/html/E36856/pkgdelivery.html
https://www.devtech101.com/how-to-add-a-p5p-pkg-to-a-solaris-11-repo/
