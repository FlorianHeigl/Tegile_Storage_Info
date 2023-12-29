


Design / Vorstellungen

Quelle: https://www.penguinpunk.net/blog/storage-field-day-6-day-1-tegile/ by Dan Frith

Hier zitiert mit Kommentaren:

## Data Reduction:

- In-line deduplication (single threaded, latency hit)
- block level dedupe across media (it will be restricted per pool)
- In-line compression (this works well enough, but also here there's no very lightweight + multithreaded algorithm, latency hit)
- block level compression - turn on/off at LUN / share level (works well enough)
- algorithms – LZ4, LZJB, GZIP

## Thin provisioning

- array-level thin, for LUNs and shares, supports VMware VAAI “STUN”, JIT storage provisioning

"Interestingly, Tegile chooses to compress then dedupe, which seems at odds with a few other offerings out there."
It worked well enough, tested with ISOs in different VMs and also with updates.
You have little image sprawl on tegile over update cycles. (besides from snashots)


## data protection perspective

- Instantaneous thin snapshots (true, and seemingly better performance than OpenZFS)
- point-in-time copies of data, space allocated only for changed blocks (that was nice back then compared to i.e. IBM Storwize)
- no reserve space for snapshots (i didn't feel like that was a benefit during migrations)
- unlimited number of snapshots (true, and seemingly better performance than OpenZFS)
- VM-consistent and application-consistent (imo daemon based)
- Instantaneous thin clones (yes, great)
- mountable copies (yes, great)
- R/W-able copies (yes, great)
- point-in-time copies (yes, very very great, the selector for the restores is also great)
- Detect and correct silent corruption (has to)
- checksums all data blocks (has to)
- data and checksum in separate locations (good!)
- match data/checksum for integrity
- corrupt / mismatched data fixed using blocks from mirrored copy (well not only mirrored I hope)


Data recovery perspective:


- Instantaneous stable Recovery (yes, mapping is very fast too, can be done in one workflow if needed)
- **No** support for chaging volume IDs/serial numbers in this (!Risk!)
- data-consistent VM snapshots (there's a specific daemon for that which is not well-documented and also not opensource, so security updates cannot be realized)
- hypervisor integrated (by default? imo no)
- MSFT VSS co-ordinated data-consistent snapshots (daemon)
- VM-consistent and application-consistent snapshots (daemon?)
- Intelligent data reconstruction no need to rebuild entire drive only portion of data rebuilt (that sounds like draid, uncertain)
- accelerated metadata accelerates rebuilds (this is less relevant in 2023 since ZFS got better at this in general)
- WAN-optimized replication (untested)
- snapshot-based site-to-site replication (untested)
- minimizes bandwidth usage, no need to replicate multiple updates to a block within the replication interval (normal)
- one to many / many to one replication (nice, and they kept improving on that)
- also added array-to-array migrations using this
- later added S3 backup destinations (not locked to specific providers!)
- later added NDMP support for backups (not tested, but great)


Snapshot time management (schedules etc) is absolutely great.
Restoration is great, also for use cases like clone-to-staging.
Management of snapshots as volumes is not good (you cannot rename and so you'll be running off _Snap_blah_clone1234 forever!)


### Storagereview article

https://www.storagereview.com/review/tegile-ha2300-hybrid-array-review

image


### Architecture Whitepaper

https://www.sanitysolutions.com/wp-content/uploads/2018/03/Technical-White-Paper-IntelliFlash-Architecture.pdf
