```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```

## KVM

You should _really_ buy an OOB license for the systems if you want to keep using them without vendor support. They're cheap, you need the one that is around $30 (OOB+KVM), not the $130 one (Enterprise management)


## BIOS KVM-USB ISO Boot


Share von Windows VM ging besser als von Synology

SMBv1 Share ggf. notwendig
Synology: Allow NTLMv1 Auth (warning, security risks, use dedicated setup)

If Share won't work

Start JAVA KVM 

If doesn't work

Start JAVA KVM from IPMIview 

You can then map the ISO directly in JAVA KVM.
Then go into the BIOS with `nextboot device bios` and adjust the boot device there.

Bootdevice USB-CDROM or similar does not work!
