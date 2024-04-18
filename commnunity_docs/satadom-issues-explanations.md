```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```
The SATA doms run as zfs `mirror` to ensure reliability.

However, the SATA doms cannot withstand the many accesses of ZFS, there are different models, but there are probably many problems.


The following cases are conceivable and confirming reports can be found via Google or system monitoring.

- Failure of the DOM after a power failure
- Slowness of the DOM due to exceeded service life (wear)
- Failure of the DOM due to exceeded service life



The slowness affects the entire solution due to the system design.
(There is one config store each in a PGSQL database, this is replicated, and so a "save" with an affected SATA dom can take 20-30s)


Only SLC / MLC flash media were used for enterprise / industrial use, but this was not enough to avoid the problems.


Tegile has - as far as can be understood - gone through the following stages (of grief...)

- Change from setup with mirror between 1 user disk and 1 DOM to 2x DOM
- Change from Supermicro to Innodisk Industrial DOMs (assumed)
- Change to newer Innodisk DOMs
- DOM firmware updates
- Change to larger DOMs (I had 256GB models installed)
- Dedicated project with own developer to solve the problems

Results of the project were the customisation of the installation and a "refactor" tool for DOM Config, which rebuilds the system pool, making the following improvements:

- 4K Blocksize, fixes write amplification by adapting to the Erase Blocks in Flash
- ZFS Trim implementation (different name/flags than OpenZFS and activation of the feature
- Health monitoring and regular status checks of the DOMs
- Healthcheck tools (possibly incl. `smartctl` compatible output, but this may have been the case with the NVDIMMs)


What has not been done as far as can be seen:
- Adjust BIOS settings (DOMs are set up as "Hard Disk" instead of "SSD")
- Adjust logging (it is excessive and there is at least one post on Reddit that clearly points to logging as the cause)
- Boot-to-ram setup with only occasional flushes etc.
- Change to latest generation Innodisk SATA DOMs (v4, which had improved TRIM support)
- The health monitoring is still insufficient, i.e. I have a few SATA DOMs that are completely worn out and reject every SCSI command first (retry then works) and every SMART self-test goes to error. These are reported as "OK"

So you MUST check beyond the existing level, and perhaps SHOULD replace the DOMs every few years.
You CAN deactivate the exec.log (shell and command logging)
