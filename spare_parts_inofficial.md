


## System

### Chassis / Nodes

----

### SAS Based, No NVDIMM

#### HA2100, SS2100

CPU: 2x Xeon E5620
NIC: Intel X520-2
RAM: 8GB DDR3 1066 Hyundai (48GB per Node?)

?1x? E5620, ?12GB?, X89DTS-F, 2x 1200W PSU


#### ?
Tegile 16 BAY RACK W/ 

CPU XEON 5620 CPU 2.4 GHZ
RAM 48GB OF DDR3  (8GB Hynix PC3-10600R HMT31GR7BFR4C-H9)
Case CSE-836?
X8-DTH Board

#### T3100

16 BAY 
CPU 2xXEON INTEL CPU 2.4 GHZ
48GB

#### T3200

Node: X9DBS-F  
Memory: 96GB/Node 16GB 2Rx4 PC3L-12800R-11-13-E2, SKhynix HMT42GR7BFR4A-PB
Case: CSE-937  
CPU: 2x E5-2620 v2/Node



SATA DOM: Innodisk unknown model

#### T3800
X9DBS-F-2U
CPU: 2x E5-2450v2 2.5GHz/Node 
RAM: 96GB RAM / Node

SATA DOM: Innodisk unknown model (Power via Cable)



#### T4100
X10-DRS-3U
CPU: unknown, 6 core
RAM: 8x16GB / Node
PCIe: 2x half length/half height, 1x half length/full-height slot

----

### SAS Based, with NVDIMM


#### T4700
Node: X10-DRS-2U
Power Supply:  PWS-1K23A-1R
PCIe: 3x half length/half height

The above PSU is a 1200W model, there's a 1400W version too that runs cheaper. Unknown if it's compatible.

SAS Controller:  AOM-S3008-L8SB

SATA DOM: Innodisk SATADOM-ML 3ME3 V2, 256GB DESML-B56D08-CAQC

---

### NVMe based

#### N5100

CPU: Xeon Silver
RAM: 128GB DDR4

    This model seems to not have an NVDIMM!

---

### SAS JBOD 

can anyone fill in the list?

not all have had ipmi monitoring interfaces.

##### J1100 

12*3.5", 4x 6G SAS
3 x 200GB SSD & 9 x 2TB 7.2K
no ipmi

##### J2130

16*3.5"
4x 6G SAS
12x 3TB HGST HUS724030ALS640 HDD
4x 400GB HGST HUSMM8040ASS200 SSD
no ipmi

##### ESH-25-A1

16*3.5", 4x 12G SAS
Tegile Storage SAN 26TB Expansion Array 
13x 2TB SAS 3x 250GB SSD JBOD
no ipmi


#### JBOD 12g / 2.5" x24
927R-E2CJB
PSU for JBOD (PWS-1K23A-1R)

##### ESF-10

CSE-216
24x 2.5"
500GB SSD??
4x12G SAS
no ipmi

##### ESH-35 

16*3.5" 3TB
4x 12G SAS
no ipmi

##### ESH-65

4U, 72*2.5"
8 x 200GB SSD
64 x 1TB 7.2K 2.5"
4x12G SAS
no ipmi

##### ES-4000

TEGILE – ES4000, 4U, 72-bay Expansion Shelf – 72 x 1TB 7.2K 2.5”
4x6G SAS
no ipmi

##### ES-4100

Tegile ES4100 72*2.5"
64x 1TB Seagate ST91000640SS 2.5" SAS HDD
8x 200GB HGST HUSML4020ASS600 2.5" SSD

##### ES-4140
Tegile ES4140 72*2.5"
64 or 72 slots?
4x 6G SAS
64x 1TB Seagate ST91000640SS 2.5" SAS HDD
1x 400GB HGST HUSMM8040ASS200 2.5" SSD
no ipmi

#### JBOD 12g / 2.5" x64



##### other configurations that existed

1 - (24) 500GB
2 - (13) 2 TB, (3) SSD – 480 GB
3 - (6) 250 GB, (18) 1 TB
4 – (24) 500 GB



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
|CARD-10G-E-2-SFP+|Dual 10g SFP+|Intel X520|Silicom PE210G2SPI9-SR(*)|Yes|
|CARD-10G-E-4-SFP+|Quad 10g SFP+|Intel x710 or Dual 82559|likely compatible Silicom PE310G4I71L|No|

(*)Silicom PE210G2SPI9-SR was the 10g adapter used in T3200, it should match to this part no.


 ### 40g NICs

|Part|Descr|Core Hardware|Possible Replacement/OEM Part|Tested|
|----|-----|-----------|------|----|
|CARD‐40G‐E‐2‐SFP+|Dual 40g QSFP|?|Silicom PE340G2QI71-QX4|No|

 ### 16G FC

|Part|Descr|Core Hardware|Possible Replacement|Tested|
|----|-----|-----------|------|-----|
|CARD-8G-F-2-T4|Dual 8g FC|?|?|No|
|CARD-16G-F-2-T4|Dual 16g FC|QLE8362|Oracle QLA8362|Yes|

 ### SAN HBA Advice

- SFP Type is very restricted, you want one with the `-QL` suffix
- You will not get a linkup with these HBAs in direct attached scenarios
- Mode settings via UEFI OPROM have no effect after the OS is up and initializes the NIC. The Solaris and QLA admin tools do not work with the adapter in target mode
- If you want to use FC, I think you DO NEED a switch, sorry. The cheapest I could get was a Cisco 16G switch, which was kinda hard to reset the password on, but otherwise works fine
- Upside: The SAN performance is great for a ZFS-based system
- Even with PCIe2 HBAs I was able to reach 2-3GB/s to a single host easily, with multiple it went up to somewhere under 5GB/s (fio randrw 256MB)

### NVMe advice

The backplane of the T4700 has 4 dual-personality ports and the X10DRS-2U exposes PCI lanes for 4 NVMe Ports.
Nonetheless, it is NOT functional. This is confirmed by trying and by communication with SuperMicro.
If you wanted to introduce NVMe SSDs with the older models, you would need to find a (dual-ported) **external** solution.

### SAS Advice

The latest series (6xxx) have introduced a SAS loopback link. This removes one SPOF for storage access. It is unclear if this can also be used with the older models, it *should* be a purely software specific choice.

The type of cable is unknown, but generally it should just be a 12G SAS cable.
