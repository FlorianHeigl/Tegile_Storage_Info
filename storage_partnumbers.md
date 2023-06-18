


### Collection of Disk Drives

Both SSD and HDD, Info mostly gathered from Ebay auction screenshots etc, some also from disks and spaces in running systems.

|Type|Size|seen in|Model|Firmware|P/N|
|--|--|--|--|--|--|
|SSD|250GB|ESH-25-A1||||
|SSD|400||SSD800MM||0B28588|
|SSD|250||HUSMR1625ASS201|B204||
|SSD|500||MUSMR1650ASS201|B300|0B32233|
|SSD|200||||0B28587|  
|SSD|200||HUSML4020ASS?00|A337|0B26577|
|SSD|960GB|T4700|SS200 SXHLLL|X130|0TS1397|
|SSD|1000GB|T4700|HUSMR1610ASS201|B300|0B32235|
|SSD|1920||HUSMR1619ASS235|D1C0|0B32297|
|SSD|1920|ESF-xx|HUSMR1619ASS231|B1C0||
|SSD|2000||Optimus ECO TXA2E2|?|SDLLGC6R-020T-5CA1|
|SSD|2TB + 3.84TB|N5100(*)|SN200|?||
|HDD|1000|| ST91000640SS||0004| 9RZ268-004 |
|HDD|1000||HUC721010ASS601|?|0B30781|
|HDD|1000||7.2K 64MB Cache 6Gb/s 2.5" SAS HDD|?|A680|0B30780|
|HDD|2000||HU724020ALS640|A280|0B26887|
|HDD|2000||HU726020ALS6211|907|0F22958|
|HDD|2000|ESH-25-A1||||
|HDD|3000||HUS724030ALS641 | B280|0B26926 |
|HDD|4000|| 7K6000|907|0f22962|




## Trivia

### Interesting Order Numbers:

- 3T‐1DW‐NVME‐SSD Western Digital  3.84TB NVMe SSD in a 2.5" carrier 
- 3T‐3DW‐NVME‐SSD Western Digital  3.2TB NVMe SSD in a 2.5" carrier
- 4T‐1DW‐NVME‐SSD Western Digital  7.68TB NVMe SSD in a 2.5" carrier
- 4T‐3DW‐NVME‐SSD Western Digital  6.4TB NVMe SSD in a 2.5" carrier
- 1EX1135 Western Digital  AS P100 FRU Drive w/Carrier HDD 12TB SNGL SAS 4KN SE (HC520)

Note: They were very late / reluctant with adding support for large HDD.
Without testing there's no way if the "any IntelliFlash can be attached to a T-Series" holds truth with regard to decent sized HDD

### Things that might work

#### Drives
- Samsung PM1733 NVMe SSD

#### Expansions

- InfiniFlash Arrays (IF-100, IF-150)
- SuperMicro JBOD enclosures without management
- SuperMicro JBOD enclosures with right management AND right Firmware
- SAS expansion cabling redundancy (DDN introduced that for the last series)


## Contributing

### How to query Disk info in running system and contribute

1. Look for `diskinfo` and `iostat -E` commands here.
2. Redact from your info: your device hostname (its in your prompt) and disk serial numbers, if any (They are normally not seen in this command output)
3. Make sure to identify both the model number and firmware revision

https://www.reddit.com/r/sysadmin/comments/dmfnaa/comment/j64n1xq/?utm_source=reddit&utm_medium=web2x&context=3

### How to query Disk info in decommissioned system and contribute

1. Look for the part number `P/N`
2. Look for Model Number string (String starting with `HUS` followed by  alphanumberic string, normally ending in `1`)
3. Look for the Firmware version (4-digit alpanumeric)


### How to read HGST / WD part numbers

- H -> Hitachi
- U -> Ultrastar Line (Ex-IBM DDYS etc), this held true regarding the disk chassis etc for many years. For SSD, there's no as strict relationship with IBM, though IBM afaik only used HGST drives for their pSeries and StorWize arrays etc whenever not using something home-grown
- S -> SAS device
- Numbers -> RPM, Series, Capacity, SAS Speed
- A/B -> Revision, there will only be a second revision upon major issues. So if there IS a `B` revision, avoid the `A`.
- L -> IDK
- S -> IDK
- 21 -> 2-digit number, trailing `1` means SED (encrypting) drive

