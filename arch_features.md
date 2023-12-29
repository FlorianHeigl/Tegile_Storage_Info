


Design / Vorstellungen

Quelle: https://www.penguinpunk.net/blog/storage-field-day-6-day-1-tegile/

Hier zitiert mit Kommentaren:

Data Reduction is offered via:

In-line deduplication (single threaded, latency hit)
block level dedupe across media (it will be restricted per pool)
performance multiplier In-line compression (this works well enough, but also here there's no very lightweight + multithreaded algorithm, latency hit)
block level - turn on/off at LUN / share level (works well enough)
alogrithm – LZ4, LZJB, GZIP
Thin provisioning:
array-level thin, for LUNs and shares, supports VMware VAAI “STUN”, JIT storage provisioning

"Interestingly, Tegile chooses to compress then dedupe, which seems at odds with a few other offerings out there."
It worked well enough, tested with ISOs in different VMs and also with updates.
You have little image sprawl on tegile over update cycles. (besides from snashots)


From a data protection perspective, Tegile offers:

Instantaneous thin snapshots
point-in-time copies of data
space allocated only for changed blocks
no reserve space for snapshots
unlimited number of snapshots
VM-consistent and application-consistent
Instantaneous thin clones
mountable copies
R/W-able copies
point-in-time copies
Space allocated only for deltas
Detect and correct silent corruption
checksums all data blocks
data and checksum in separate locations
match data/checksum for integrity
corrupt / mismatched data fixed using blocks from mirrored copy


From a data recovery perspective, the Tegile solution offers:

Instantaneous stable Recovery
data-consistent VM snapshots (there's a specific daemon for that which is not well-documented and also not opensource, so security updates cannot be realized)
hypervisor integrated (by default? imo no)
MSFT VSS co-ordinated data-consistent snapshots (daemon)
VM-consistent and application-consistent snapshots

Intelligent data reconstruction no need to rebuild entire drive only portion of data rebuilt (that sounds like draid, uncertain)
accelerated metadata accelerates rebuilds (this is less relevant in 2023 since ZFS got better at this in general)
WAN-optimized replication (untested)
snapshot-based site-to-site replication (untested)
no need to replicate multiple updates to a block within the replication interval (normal)
minimizes bandwidth usage
one to many / many to one replication (nice, and they kept improving on that)


Snapshot time management (schedules etc) is absolutely great.
Restoration is great, also for use cases like clone-to-staging.
Management of snapshots as volumes is not good (you cannot rename and so you'll be running off _Snap_blah_clone1234 forever!)


### Storagereview article

https://www.storagereview.com/review/tegile-ha2300-hybrid-array-review

image


### Architecture Whitepaper

https://www.sanitysolutions.com/wp-content/uploads/2018/03/Technical-White-Paper-IntelliFlash-Architecture.pdf
