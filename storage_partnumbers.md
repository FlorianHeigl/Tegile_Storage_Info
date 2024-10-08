


### Collection of Disk Drives

This is a list of both SSD and HDD, Info mostly gathered from Ebay auction screenshots etc, some also from disks and spaces in running systems.

#### SSD

|Type|Size|seen in|Model|Firmware|P/N|
|--|--|--|--|--|--|
|SSD|200||||0B28587|  
|SSD|200||HUSML4020ASS?00|A337|0B26577|
|SSD|250GB|ESH-25-A1||||
|SSD|250||HUSMR1625ASS201|B204||
|SSD|400||SSD800MM||0B28588|
|SSD|500||MUSMR1650ASS201|B300|0B32233|
|SSD|960|T4700|SS200 SXHLLL|X130|0TS1397|
|SSD|1000|T4700|HUSMR1610ASS201|B300|0B32235|
|SSD|1600||HUSMR3216ASS205 (SS300)||0B29793|
|SSD|960||HUSMR7696BDP3Y1 (SN200)|?|0T81354|
|SSD|1920||HUSMR1619ASS235|D1C0|0B32297|
|SSD|1920|ESF-xx|HUSMR1619ASS231|B1C0||
|SSD|1920|N-Series|SN200|D110|0TS1889|
|SSD|2000|HA-Series|Optimus ECO TXA2E2|?|SDLLGC6R-020T-5CA1|
|SSD|2TB + 3.84TB|N5100(*)|SN200|?||
|SSD|1920|E-Series|MZWLR1T9HCJR (PM1733a)|MPPA5B5Q|||
|SSD|3840|E-Series|MZWLR3T8HCLS (PM1733a)|MPPA5B5Q|||
|SSD|3840|E-Series|MZWLJ3T8HBLS (PM1733) |EPK9FB5Q|||
|SSD|7680|HD-Series|SS200| X150|||
|SSD|7680|E-Series|MZWLR7T6HBLA (PM1733A)|MPPA5B5Q|||
|SSD|7860|E-Series|MZWLJ7T6HALA (PM1733a)|EPK9FB5Q|||
|SSD|15360|E-Series|MZWLJ15THALA (PM1733a)|EPK9FB5Q|||
|SSD|30720|E-Series|MZWLR30THBLA (PM1733a)|MPPA5B5Q|||

One thing to note is that they used SSDs from both the "original" Hitachi SSD line from HGST, and from the STEC line HGST bought.
There's also Mixed-Use and Read-Optimized models, and in general, a mixed-use STEC (SS200, SS300, SN200...) drive is
more like a read-optimized Hitachi drive as far as endurance is concerned.
In other words, the STEC SSDs are generally faster but not as durable.
Before that they also used some 2TB model, probably the Optimus/?!?!

(WD/HGST in a move of confidence later killed the HGST products and imho completely lost the race to Micron due to that choice. I read a manager had the task of "streamlining" their product portfolio. Likely that's what happened. )


#### HDD

|Type|Size|seen in|Model|Firmware|P/N|
|--|--|--|--|--|--|
|HDD|1000|| ST91000640SS||0004| 9RZ268-004 |
|HDD|1000||HUC721010ASS601|?|0B30781|
|HDD|1000||7.2K 64MB Cache 6Gb/s 2.5" SAS HDD|?|A680|0B30780|
|HDD|2000|SS2100|HU724020ALS640|A280|0B26887|
|HDD|2000||HU726020ALS6211|907|0F22958|
|HDD|2000|ESH-25-A1||||
|HDD|3000||HUS724030ALS641 | B280|0B26926 |
|HDD|4000||HUS726040ALS211|D05|0F22956|
|HDD|4000|| 7K6000|907|0f22962|
|HDD|14000||WUH721814AL5201|DN04||
|HDD|14000||WUH721414AL5201|DN08||
|HDD|18000||WUH721818AL5205|D680||
|HDD|20000||WUH722020BL5201|DN02||





## Trivia

### Interesting Order Numbers:

- 3T‐1DW‐NVME‐SSD Western Digital  3.84TB NVMe SSD in a 2.5" carrier 
- 3T‐3DW‐NVME‐SSD Western Digital  3.2TB NVMe SSD in a 2.5" carrier
- 4T‐1DW‐NVME‐SSD Western Digital  7.68TB NVMe SSD in a 2.5" carrier
- 4T‐3DW‐NVME‐SSD Western Digital  6.4TB NVMe SSD in a 2.5" carrier
- 1EX1135 Western Digital  AS P100 FRU Drive w/Carrier HDD 12TB SNGL SAS 4KN SE (HC520)

Note: They were very late / reluctant with adding support for large HDD.
It seems the small number of supported 14-20TB drives came with the 6xxx series.
Without testing there's no way if the "any IntelliFlash hybrid expansion can be attached to a T-Series" holds truth with regard to decent sized HDD.

### Things that might work

#### Drives
- Samsung PM1733 NVMe SSD

#### Expansions

- SanDisk / WD InfiniFlash Arrays (IF-100 (6g SAS), IF-150 (12g SAS). There's clear references to the IF-100 (as sandiskif100), not to the IF-150, but the IF-150 is the much more desirable model...
- SuperMicro JBOD enclosures without management
- SuperMicro JBOD enclosures with right management AND right Firmware
- SAS expansion cabling redundancy (DDN introduced that for the last series)

**InfiniFlash Array** used in combination with the HD series:  
This uses 8TB SAS flash modules in a JBOD fashion. It can hold ~60 of them, so this is the capacity monster among all options.
The flash modules themselves have some flash management controller on board and seem to be good endurance, but not high-performing.
So this JBOD is great for things like lower-latency large-size data tiers, but will need a faster layer for the metadata.

**4U 2.5" SAS Arrays** used with the HA series:  
those could hold 50-ish disks in 4U. you could get a large amount of 1TB (7.2k) SAS drives, plus a few SSDs as a cache/meta tier.
lternatively, they forewent the cache/meta tier and used 2TB SAS SSDs in the HA series before this.  
those were the 2TB SanDisk Optimus ECO 6G SAS drives



## Contributing

### How to query Disk info in running system and contribute

1. Look for `diskinfo` and `iostat -E` commands here.
2. Redact from your info: your device hostname (its in your prompt) and disk serial numbers, if any (They are normally not seen in this command output)
3. Make sure to identify both the model number and firmware revision

https://www.reddit.com/r/sysadmin/comments/dmfnaa/comment/j64n1xq/?utm_source=reddit&utm_medium=web2x&context=3

For NVMe drives, I know they are also managable by `nvmeadm` but I do not know more about this. Let's not try on a live system, ok?


### How to query Disk info in decommissioned system and contribute

1. Look for the part number `P/N`
2. Look for Model Number string (String starting with `HUS` followed by  alphanumberic string, normally ending in `1`)
3. Look for the Firmware version (4-digit alpanumeric)


### How to read HGST / WD part numbers

- H -> Hitachi
- U -> Ultrastar Line (Ex-IBM DDYS etc), this held true regarding the disk chassis etc for many years. For SSD, there's no as strict relationship with IBM, though IBM primarily used HGST drives for their pSeries and StorWize arrays etc whenever not using something home-grown
- S -> SAS device
- Numbers -> RPM, Series, Capacity, SAS Speed (726020 -  7200rpm, 6g sas, idk, 2.0TB; MR1650ASS201 - MLC or equiv? Mainstream?, Read Optimized, 12g sas, idk, 500GB). (MM is 'mainstream endurance' which in HGST terms was 10 DWD.
- A/B -> Revision, there will only be a second revision upon major issues. So if there IS a `B` revision, avoid the `A`.
- L -> IDK
- S -> IDK (SS could mean dualport?)
- 21 -> 2-digit number, trailing `1` means SED (encrypting) drive


### Code

Zebi - the OS was built on OpenSolaris; I'm only aware of one public patch set, but in general open source licensing (CDDL) should apply to the OS.

Zebi also had homegrown plugins for Sun Cluster to handle the pNFS failover, but those appear to be closed source (C binaries)
If you have other patches of the OS, or can give guidance which parts are truly OSS, that would help heaps.

If you have a savvy legal team, you should be able to obtain the sources to your OS. This is the classic scenario where a vendor becomes unavailable and OSS licences protect you, would allow you to maintain safe operations by fixing things yourself. I do not know if there's hope, but it goes without saying that being able to put development into the OS would open up a completely different set of options, and vastly extend the lifetime of one's investments.

### decommissioning

1. data erasure

If you need help wiping them, I can provide notes for that, or guide remotely.
it is easy enough, switching the SED key. to make it proper, collect the serial numbers before hand and mark them as you pull them out of the chassis.
This procedure might be part of the user manual or knowledge base, I didn't check yet.
Don't forget the SATA DOMs. They should support Sata secure erase, so if you don't know how to nuke solaris at run-time, you can remove the DOMs and delete them in some supermicro box.

2. hardware proliferation

If this helped you / you want to contribute more
I would gladly offer a retirement home for your array or parts like the NVDIMMs
I'm trying to build a second array for labbing out of spare parts.
Only thing I couldn't use is arrays that are of an older HW generation than mine (so anything with a X10DRS board / Xeon 26xx v3 or better works, the older ones I can't really do anything with)
