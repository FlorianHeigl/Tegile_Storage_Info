```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```
If you (have to) perform a factory reset of the BIOS, certain information is lost. This applies in particular to the web password.

It is possible to adjust the settings locally in the OS using ipmitool. A long password (>16 chars) is not supported(*).

I simply set "abc" as the password and then corrected it again via the GUI.

# ipmitool user 2 pass abc

(*)It does work if you use a lanplus driver with -I

It would be good to have a KVM cable for this (CBL-0218)


The serial number / chassis ID can also get lost. You can reapply those settings using supermicro ipmiview (the java one). you might need to buy a license (OOB) for it to do that.
