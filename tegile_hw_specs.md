Sources:
https://www.storagereview.com/news/tegile-launches-t4000-series-of-all-flash-hybrid-arrays
more... lots of googling and datasheets.


Key specifications:

 ### All-Flash Models: T4500 | T4600 | T4700 | T4800

Form Factor: 2U

CPU: 4 x E5-2640 v3 | 4 x E5-2680 v3 | 4 x E5-2680 v3 | 4 x E5-2680 v3

Controllers: Dual-Active Controller Architecture

Memory: 240GB | 464GB | 464GB | 464GB

 #### Storage

- Capacity: 6TB | 12TB | 24TB | 46TB
- Effective Capacity: 22 – 1093TB | 44 – 1116TB | 88 – 1160TB | 170 -1241TB

 #### Network Connectivity

- Lights-out Management Ports: 2 x 1Gbps KVM over IP
- Storage Connectivity: 16 & 8Gbps Fibre Channel, 10GE Copper/Fibre & 1 Gbps Ethernet


Power: 439W | 495W | 495W | 495W

Weight: 80 lbs

 ### Hybrid Models: T4100 | T4200 | T4530 | T4630 | T4730 | T4760 | T4860

Form Factor: 3U | 3U | 5U | 5U | 8U | 5U | 5U

CPU: 4 x E5-2620 v3 | 4 x E5-2640 v3 | 4 x E5-2640 v3 | 4 x E5-2680 v3 | 4 x E5-2680 v3 | 4 x E5-2680 v3 | 4 x E5-2680 v3

Controllers: Dual-Active Controller Architecture

Memory: 256GB | 464GB | 240GB | 464GB | 464GB | 464GB | 464GB

 #### Storage

- Flash Capacity: 1.5TB | 5.8TB | 7.5TB | 17.8TB | 35.6TB | 25.5TB | 51.8TB
- Disk Capacity:  26TB | 52TB | 26TB | 52TB | 104TB | 26TB | 52TB
- Effective Flash Capacity: N/A | N/A | 22-917TB | 44-939TB | 88-804TB | 88-983TB | 170-1065TB
- Effective Hybrid Capacity: 60-780TB | 120-840TB | 60-660TB | 120-720TB | 240-720TB | 60-660TB | 120-720TB


 #### Network Connectivity
- Lights-out Management Ports: 2 x 1Gbps KVM over IP
- Storage Connectivity: 16 & 8Gbps Fibre Channel, 10GE Copper/Fibre & 1 Gbps Ethernet


Power: 423W | 441W | 635W | 691W | 887W | 691W | 691W

Weight: 105lbs | 105lbs | 185lbs | 185lbs | 290lbs | 185lbs | 185lbs



### Example Layout for 3.5" System:

T4200: 13x4TB Disk, 3x 1.92TB SSD




## Virtualization:

Running virtualized is an unknown field, though I thnk there were some references to ESXi in the boot env?
 
QEMU should be able to emulate the WHOLE platform.  
There are documented emulators for *IPMI, UEFI* and *PCIe Switch*.
You would need to seed the correct information for them all.
There's probably NVDIMM-N emulation but the NVDIMM is an *optional* component.
You can launch Zebi on Hyper-V or Virtualbox (dont remember which) with some effort, but it won't complete boot.

Advice:
- Don't go down this road if you don't have a few weeks to investigate.
- The door to putting this under OpenQA control is clearly visible
- Don't go down that road if you don't have a few months to investigate.


### Virtual Load generators

There was a Hyper-V (`Tegile-IO-HyperV-1.3.zip`) and a VMware load (`Tegile-POC_2_1.ova`) generator.
It dates back to 2017, capabilities unknown.
(You get an impression how understaffed they must've kept their professional services considering they never managed to align those two names)

### Docs

#### umping and loading SMBIOS tables

https://patchwork.kernel.org/project/kvm/patch/1237835465.15558.4.camel@lappy/

#### IPMI-over-LAN for QEMU (option a)

- https://github.com/zexi/vbmc-qemu
- https://gist.github.com/williamcaban/aba796f856264799326d554ac11a4a66

#### IPMI Sim (option b)

here are some notes about really right eumulation[tm]  http://www.linux-kvm.org/images/7/76/03x08-Juniper-Corey\_Minyard-UsingIPMIinQEMU.ods.pdf

```
ipmi_sim

-device ipmi-bmc-sim,id=bmc0
-chardev socket,id=ipmichr0,host=localhost,port=9002,reconnect=10
-device ipmi-bmc-extern,chardev=ipmichr0,id=bmc0
```

source: https://github.com/cminyard/qemu

