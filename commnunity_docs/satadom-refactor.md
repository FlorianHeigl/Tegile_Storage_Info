```
this also is a contributed document, no warranties, use at own risk and own discretion
please send PRs for any corrections
```



## Goal

- Convert Pool ZebiSystem to 4K Sector Size
- Flash Erase SATA Doms (does not repair them but releases blocks)
- ZFS Trim enable (needs 4K)

You should delete/wipe defective SATA doms anyway and you MUST consider them a finite lifetime ressource.

Procedure that worked for me

Enable USB boot

Boot from USB (installer iso)

Login for "repair (root/root123)

`zpool import -f ZebiSystem`

you should only start it with 'all'.

`satadom-refactor all`

Notes:

1. run cancelled

started again so that scrub works.
Probably the right way is

1. import -f  
2. export 
3. refactor
4. import
5. fs mountpoint fixes (see below)
6. export
7. reboot

It seems to work well in this order.
If it aborts, there may be various "intermediate states".

In general it is probably not an 'easy' job.

If an error occurs, you have to check whether/how far it has come.
Then, if necessary, discard the TempZebiSystem pool or the ZebiSystem pool.

Then restart, e.g. `# satadom-refactor c1t0d0p0`.

The mirror is rebuilt. If the SATADOMs are already worn out, this can take an extremely long time. (10h+). In my case it took about 2-3h for this.
On two non-defective DOMs you can see shorter runtimes - still approx. 1h @ 45MB/s.

Ideally, you should probably replace them before Lifetime drops below 80%.
For me it was 61% and 12%

The current generation is faster and more reliable (firmware etc)

### Tips:

- you can skip the 1st scrub by pressing `-s` - but this is only safe if one has already run
- the scrub is very slow at the start
- it is best to do the scrub before the reboot - from the normal OS


During the refactor - reproducibly - a filesystem mount parameter is lost.
You can clearly see errors at system startup that certain files are not found. The files are searched for under `/ZebiSystem/system/conf`. Fortunately they are not gone, but only in unmounted filesystems 

The mountpoints are zfs options, you can simply set them again, preferably before the reboot. But you can also do it afterwards, then you just have to reboot the node again.

If you look at the mountpoint column under `zfs list`, you can see that almost all of them are set to `legacy`.

The following commands set it right again for the important FS.

```
# zfs set mountpoint=/ZebiSystem ZebiSystem
# zfs set mountpoint=/ZebiSystem/ROOT ZebiSystem/ROOT
# zfs set mountpoint=/ZebiSystem/system ZebiSystem/system
```


If you need more advice on the mountpoints / file layout, the script [`upgrade-solution.sh`](https://web.archive.org/web/20251116164330/http://s1.tegile.com/ps/fw/upgrade_solution.sh) gives you some more insights


(sorry for the crappy english, had to autotranslate for time reasons)
