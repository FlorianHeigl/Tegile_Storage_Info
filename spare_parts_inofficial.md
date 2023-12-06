


## System

### Chassis / Nodes


#### T3200

Node: X9DBS-F  
Memory: 16GB 2Rx4 PC3L-12800R-11-13-E2, SKhynix HMT42GR7BFR4A-PB (96GB Total)

This model seems to not have an NVDIMM!

SATA DOM: Innodisk unknown model

#### T4700
Node: X10-DRS-2U
Power Supply:  PWS-1K23A-1R
PCIe: 3x half length/half height

The above PSU is a 1200W model, there's a 1400W version too that runs cheaper. Unknown if it's compatible.

SAS Controller:  AOM-S3008-L8SB

SATA DOM: Innodisk SATADOM-ML 3ME3 V2, 256GB DESML-B56D08-CAQC

#### T4100
X10-DRS-3U

PCIe: 2x half length/half height, 1x half length/full-height slot

### SAS JBOD (12g / 2.5")
927R-E2CJB
PSU for JBOD (PWS-1K23A-1R)


### NVDIMM

#### DIMM

A Smart Memory solutions module, supposedly in native, non-JEDEC mode.
Sizes: 8GB standard - this is: SuperMicro Smart 8GB 1Rx4 NN4-2400T-RZZZ-11

some newer systems have 16GB, which might be 2*8GB (interleaved, more bandwidth, costs one RAM slot) or 1x16GB.
The maximum module size in the series is 32GB.


As a rule of thumb, one could imagine that the NVDIMM size ought be sufficient to buffer enough data to sustain multiple cores doing compression/deduplication.


#### Battery

For other NVDIMM-N Modules you look for a so-called "PowerGEM". The ones I saw from Tegile use a Varta HVC 90F battery on an unknown module.

### KVM Cable

Supermicro CBL-0218L KVM


## Expansion Cards

These cards are often not the stock cards, but might be easier to obtain. Of course there's drawbacks and it could never be done with valid vendor support.
The last column indicates a successful load test.

Be very careful with X710/XL7xx/X722 Cards (Intel Quad 10g, Intel 40g), their firmware can be infested with over-the-top features for cloud providers.
You want stability, so look for things that come Oracle branded.


 ### 10g NICs

|Part|Descr|Core Hardware|Possible Replacement/OEM Part|Tested|
|----|-----|-----------|------|----|
|CARD-10G-E-2-BT-T4|Dual 10g RJ45|Intel X540-T2?|Silicom|Yes|
|CARD-10G-E-2-SFP+|Dual 10g SFP+|Intel X520|Silicom|Yes|
|CARD-10G-E-4-SFP+|Quad 10g SFP+|Intel x710 or Dual 82559|likely compatible Silicom PE310G4I71L|No|


 ### 40g NICs

|Part|Descr|Core Hardware|Possible Replacement/OEM Part|Tested|
|----|-----|-----------|------|----|
|CARD‐40G‐E‐2‐SFP+|Dual 40g QSFP|?|Silicom PE340G2QI71-QX4|No|

 ### 16G FC

|Part|Descr|Core Hardware|Possible Replacement|Tested|
|----|-----|-----------|------|-----|
|CARD-8G-F-2-T4|Dual 8g FC|?|?|No|
|CARD-16G-F-2-T4|Dual 16g FC|QLE8362|Oracle QLA8362|Yes|

 #### SAN HBA Advice

- SFP Type is very restricted, you want one with the `-QL` suffix
- You will not get a linkup with these HBAs in direct attached scenarios
- Mode settings via UEFI OPROM have no effect after the OS is up and initializes the NIC. The Solaris and QLA admin tools do not work with the adapter in target mode
- If you want to use FC, I think you DO NEED a switch, sorry. The cheapest I could get was a Cisco 16G switch, which was kinda hard to reset the password on, but otherwise works fine
- Upside: The SAN performance is great for a ZFS-based system
- Even with PCIe2 HBAs I was able to reach 2-3GB/s to a single host easily, with multiple it went up to somewhere under 5GB/s (fio randrw 256MB)
