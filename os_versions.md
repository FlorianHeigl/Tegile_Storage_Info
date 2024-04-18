

### Compatibility 

Known / Found issues

- Fallback via Grub has not worked in test beyond major version (likely due to zpool version on the OS pool?)
- 3.11.xx newest cannot talk to 3.9.0.1, upgrade timeout
- 3.11.0.3 Data cannot be activated on 3.9.0.1

So the feature boundary is between these two and you need an intermediary upgrade to pass it.


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

### Versions with security issues

- There was a [security advisory](https://www.westerndigital.com/support/product-security/wdc-19008-intelliflash-web-management-interface-vulnerability) affecting versions < 3.9.2 

- There's no known advisories regarding SSL, SSH, or general Solaris issues that might or might not affect the systems. Assume that some issues may exist.
- There's no known advisories regarding iSCSI, NFS, SMB issues that might or might not affect the systems. Assume that some issues may exist.


## Setup up repos

The upstream (and cloned local) repositories use a P5P format, docs can be found here:
https://docs.oracle.com/cd/E36784_01/html/E36856/pkgdelivery.html
https://www.devtech101.com/how-to-add-a-p5p-pkg-to-a-solaris-11-repo/
