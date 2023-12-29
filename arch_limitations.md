

## Known or suspected limitations

### Architektur generell

- Fake Active-Active
- Kein Boot-to-Ram
- unnoetig schlechte Performance wenn Volume parameter nicht genau passen, es gibt nicht so einen "alles wird zu 8K" Layer wie bei Pure
- Schlechte Skalierbarkeit (Diskshelves nachstecken, sonst nix)
- Fehlende NICs koennen den Cluster komplett disablen (keine Trennung zwischen "Control/Data", z.b. mittels 2 Instanzen)
- Keine Nutzung von Zones

### ZFS/Raid Handling

- Hot Spare per Pool hardwired, auch bei Raidz2
- Suboptimales vdev layout in vielen Configs (txg group implementierung evtl. anders als OpenZFS, aber es ist immer relevant)
- (wenn man die Source anschaut, sieht man, dass das Disk layout kein Faktor ist. Mit 4 Disks: `xxxx` mit 8 Disks: `xxxxxxxx`. Wozu das hardcoded ist, ist unklar
- Schafft selten full stripe writes, d.h. es kann sich selbst auf den Fuessen stehen
- Wenn man mit 2 Pools arbeitet, verliert man auch 2 Disks fuer Spares (keine global Spares)

### ZFS Code

- L2ARC RAM Usage Patches vermutlich nicht enthalten
- Dedup RAM Usage Patches vermutlich nicht enthalten
- Distributed Raid nicht portiert (d.h. schlechtere Raid6 Performance und ineffiziente Rebuilds)
- Metadata handling optimiert, aber was ist mit tiering?
- Weniger Compression algorithms als bei OpenZFS, und wird ohne HW offload gemacht. Heute muesste man das neu designen oder gar compression/dedup mit einer SmartNIC/DPU handlen, um mit der generellen HW Perf mitzuhalten

### Memory mirroring / Clustering

- nur 1 nvdimm je node <- WRONG
- vermutlich kein RDMA support / nutzung in nvdimm sync - es ging zwar ueber die PCIe Switches, aber mit viel OS hilfe.
- Keine Skalierbarkeit > 2 Nodes 
- Kein BIOS integrierter reinstall ala Tru64/VMS/Shared Root (das haette auch nur eine SD Karte sein koennen)
- Limitierung auf 2 Pools, vermutlich nur aufgrund der NVDIMM Partitionierung

### Hardware

- 8GB NVDIMM anstatt 16/32GB (sparmassnahme)
- SSD meistens MR (nur einige/besondere Modelle hatten MM SSDs)
- Das Chassis (Supermicro) ist vermutlich ohne Input von jemand mit Midrange oder Highend Storage rausgesucht wurden. Nur 1-2 externe SAS Ports pro node... Bottleneck usw.
- Grosse Performance Versprechen aber ausschliesslich langsamere read-optimized ssd verwendet - mit auswirkung auf die Latenz
- 1 statt 2 pcie switch/bridge zwischen nodes, keine redundanz an der stelle (SPOF, Probleme mit Lockups / Splitbrain sind wahrscheinlich)
- CPU Typ vermutlich nicht ideal fuer Low-Latency System (2680v3 vs. 2677v4 o.ae.). QPI Speed ist die gleiche, aber man sieht in DB Benchmarks unterschiede, zugunsten eben ca. 2677v4.

### NAS

#### SMB

- Usermapping nicht gut

#### NFS

- pNFS nicht, d.h. keine Distributed Read / Write (da nicht active/active?)

### SAN

- Initiator management / Cluster Gruppen etc. nur fuer SMB use cases geeignet
- Banalste Features wie `:` entfernen fehlen
