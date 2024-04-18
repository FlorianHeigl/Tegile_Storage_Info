```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```



## Monitoring 

 ### satadom command

`# satadom-status`

- Device Life
- Total Bad Blocks
- Spare Blocks
- Ave / Max Erase Count

The tool also issues warnings if the system pool is not (yet) set up correctly (TRIM/Sector Size)


 ### SMART Info

smartctl can be used, needs parameters:

`# smartctl -a -d sat,12 /dev/c1tNd0..._s0`

According to the information in the `satadom` script, the modules use some manufacturer-specific fields, which are automatically translated by the script.


On my SATADOM only 27GB are occupied, so you don't really need a 256GB DOM, just a sufficiently up-to-date one with the fixes and TRIM enable - you would also have done well not to format it completely.

It is unclear whether anything sends a TRIM to the modules, the ZFS version used does not recognise a `# zpool trim` command. 
If necessary, you can do this manually with SATA Secure Erase. It seems best to overhaul the DOMs in another system.
