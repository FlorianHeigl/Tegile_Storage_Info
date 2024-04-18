```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```


ou can update using Supermicro tools, but a licence must be purchased for this.

You can recognise a current BIOS version by the fact that it no longer displays the Tegile logo, but the Tintri logo matching the build year.
As far as I know, there is no version with the Western Digital or DDN logo.


When updating the BIOS remotely via SuperMicro Tools, it can happen that it remains at 100%, but the "do you want to reboot" dialogue never appears.

It is also possible that it gets stuck completely.

Corresponding KB entries at Supermicro can be found here:


- Link2 https://www.supermicro.org.cn/support/faqs/faq.cfm?faq=30295
- Link1 https://www.supermicro.com/support/faqs/faq.cfm?faq=32206
    A 'Factory Reset' of the management is recommended.
- Forum link for wilder problems
https://www.truenas.com/community/threads/supermicro-x10slm-f-applied-firmware-and-bios-out-of-order-now-stuck-in-reboot-loop-help.78413/


For me, a `# ipmitool mc reset cold` was sufficient for the time being.
Once the BMC is working properly again, you can then initiate the update again. The updated version is then displayed.

You then have to power cycle the node yourself.


Another problem I have seen is that the FRU information is lost or has encoding errors. This may have been in connection with the factory reset, but I think it just happened that way.


In my case, the serial numbers etc. were lost on one of two nodes.
It is therefore essential to back this up.

You can view them via IPMIView under `Users`->`FRU Information` and then update them with `Update FRU`.

I was able to read out the serial number of the mainboard with `smbios`, the FRU ID came from the other node, I could not trace the serial number of the node via software.

If you can use the Supermicro Update Manager (SUM) to save all the values, you should definitely do this (also interesting if you want to virtualise the SMBIOS for KVM)

Warning:

After BIOS update or factory reset my NVDIMM was "failed to ARM" again.
Recommended to take resources offline. (`Settings`->`High Availability`->`Take Resource Group offline`)
